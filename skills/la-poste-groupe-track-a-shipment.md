---
name: la-poste-track-a-shipment
description: >-
  Look up the delivery status and full routing history of a La Poste tracked mail
  item, Colissimo parcel or Chronopost express shipment, and read the answer
  correctly - including the partial-success case that HTTP status alone will not
  tell you about.
api: La Poste Suivi v2
base_url: https://api.laposte.fr/suivi/v2
spec: openapi/la-poste-groupe-suivi-openapi.json
operations:
  - "1.0"   # GET /idships/{idship}
  - "1.1"   # OPTIONS /idships/{idship}
generated: '2026-09-02'
method: generated
source: openapi/la-poste-groupe-suivi-openapi.json
---

# Track a La Poste shipment

Suivi v2 is the one La Poste API that answers across all three delivery networks -
tracked mail (*courrier suivi*), Colissimo parcels and Chronopost express - with a
harmonised status.

## Before you call

You need an `X-Okapi-Key`. Get one by subscribing an application to the Suivi plan
at <https://developer.laposte.fr/catalog-apis/suivi@2>. Note that the only Suivi
plan is marked **private**, so this is an access request La Poste approves, not a
self-serve signup. The plan allows **10 calls per second**; there is no runtime
rate-limit header, so pace from that number and not from the response.

## The call

`GET /idships/{idship}` (operationId `1.0`).

- `idship` is the tracking number. Pass **up to ten**, comma-separated, in the same
  path segment - that is how batching works here; there is no pagination.
- `lang` is a query parameter. Supported values are `fr_FR`, `en_GB`, `de_DE`,
  `it_IT`, `es_ES`, `nl_NL`.
- Send `Accept: application/json`. The spec states plainly that XML is deprecated.
- `X-Forwarded-For` is a documented header parameter; set it when you are proxying
  on behalf of an end user.

`OPTIONS /idships/{idship}` (operationId `1.1`) is the CORS preflight; it exists
because this API is designed to be called from a browser.

## Reading the answer - this is the part that goes wrong

The HTTP status is **not** the whole answer.

- **200** - one shipment resolved. The body is an array whose single member merges
  `baseResponse` with a `shipment` object.
- **207** - a multi-item call. The body is an array of per-shipment envelopes and
  **each one carries its own `returnCode`**. A 207 can mix successes and failures.
  If you branch only on the HTTP status you will treat a failed lookup as a hit.
- **400** - invalid input. `returnMessage` is a French sentence written to be shown
  to a customer, e.g. about the number of characters in the tracking number.
- **401** - the spec calls this "HMAC verification failed". Unauthenticated calls at
  the gateway return `{"code":"UNAUTHORIZED","message":"This action requires an
  authorization"}` before your request ever reaches Suivi.
- **404** - `returnCode` 104: unknown or not-yet-available. Read the published
  message carefully: it is a *not yet*, not a *never*. A freshly deposited item may
  simply not have entered the network. Retry later rather than reporting it as a bad
  number.

`returnCode` is declared as the enum `[101, 104, 105, 109, 200, 201, 208, 504]`, and
La Poste publishes a meaning for only three of those values. Treat any code you do
not recognise as indeterminate. Do not guess.

## What the shipment object gives you

- `shipmentPropPub` - `holder`, `product`, `isFinal`, `entryDate`, `estimDate` with
  `estimHourMin`/`estimHourMax`, `deliveryDate`, and a customer-facing `url`.
- `shipmentTrk.timeline[]` - the ordered routing history as `step` objects
  (`id`, `shortLabel`, `longLabel`, `status`, `type`, `date`, `country`).
- `shipmentTrk.event` - the latest movement (`date`, `label`, `code`).
- `contextData.partner` - which carrier leg handled it (`name`, `network`,
  `reference`), which is where Colissimo and Chronopost surface inside a unified
  answer.
- `contextData.removalPoint` - where it can be collected, if applicable.

Use `isFinal` to decide whether to stop polling. Do not infer finality from
`deliveryDate` alone.

## Cautions

- `removalPoint` here shares **no identifier** with Colissimo's `PointRetrait` or
  with the Open Data `pointscontact` dataset. Reconciling them means matching on
  address text.
- The gateway stamps `x-okapi-request-id` on every response. Log it; it is the
  reference to quote to support.
