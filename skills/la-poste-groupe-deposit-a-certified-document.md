---
name: la-poste-deposit-a-certified-document
description: >-
  Enrol a user into a Digiposte+ certified digital safe and file a document into it
  as an issuing partner - and understand which of those steps you can take back and
  which you cannot.
api: Digiposte v3
base_url: https://api.laposte.fr/digiposte/v3
spec: openapi/la-poste-groupe-digiposte-openapi.json
operations:
  - "Obtenir un token « client_credentials »"    # POST /digiposte/v3/oauth/token
  - "Créer une adhésion"                          # POST /digiposte/v3/membership
  - "Récupérer la liste des adhésions existantes" # GET  /digiposte/v3/memberships
  - "Déposer un document certifié"                # POST /digiposte/v3/document/certified
  - "Résilier une adhésion"                       # DELETE /digiposte/v3/membership/{id}
  - "Créer un nouveau compte partiel"             # POST /user/partial
  - "Créer ou renouveler l'url de personnalisation d'un compte partiel" # POST /user/customizationurl
generated: '2026-09-02'
method: generated
source: >-
  openapi/la-poste-groupe-digiposte-openapi.json and the public resource catalogue
  at https://developer.laposte.fr/catalog-apis/digiposte@3
---

# Deposit a certified document into a Digiposte+ vault

Digiposte+ is La Poste's *coffre-fort numérique à valeur probante* - a probative-value
digital safe. As an issuing partner you deposit documents that carry a "certifié La
Poste" seal attesting issuer identity and non-alteration.

**Read the reversibility section before you write anything.**

## 1. Get a token

`POST /digiposte/v3/oauth/token` (operationId `Obtenir un token
« client_credentials »`) using HTTP **Basic** auth with your client credentials.
Every other operation then takes the resulting OAuth 2.0 bearer token.

The published security scheme declares `authorizationUrl` and `tokenUrl` as the
literal placeholder `/`. That is a defect in the spec, not a missing endpoint - the
token path above is the real one, and it is discoverable only from the path list.

## 2. Enrol the user

Enrolment is consent-first. The user is redirected into a Digiposte consent journey
from your site, creates or signs into an account, and comes back.

- `POST /user/partial` (`Créer un nouveau compte partiel`) creates a shell account.
- `POST /user/customizationurl` (`Créer ou renouveler l'url de personnalisation
  d'un compte partiel`) mints the personalisation URL (PURL) the user follows.
- `POST /api/v4/resend-purl` re-sends that link if the user loses it.
- `POST /digiposte/v3/membership` (`Créer une adhésion`) creates the membership -
  the consented link between you and the user's vault.
- `GET /digiposte/v3/memberships` (`Récupérer la liste des adhésions existantes`)
  lists what you already hold.

## 3. Deposit

`POST /digiposte/v3/document/certified` (`Déposer un document certifié`) files the
document against a membership. A folder named for your service is created in the
user's vault automatically and the user is notified by email and mobile.

## Reversibility - the part that matters

| Action | Reversal | Window |
|---|---|---|
| Create a membership | `DELETE /digiposte/v3/membership/{id}` (`Résilier une adhésion`) | **Not stated** |
| Deposit a certified document | **None published** | n/a |
| Create an organisation-safe document | `DELETE /partner/safes/{id}/documents/{document_id}` | Not stated - and the delete is itself permanent |
| Share documents with an organisation | `DELETE /partner/shares/{partner_user_id}/documents/{document_id}` | Not stated |

The certified deposit is the highest-consequence write in La Poste's whole public
estate and the published contract exposes **no way to undo it**. Confirm with a
human before calling it on data you are not certain about.

## No idempotency

There is no `Idempotency-Key` header and no client-supplied request identifier
anywhere in this contract - the string "idempoten" does not occur in it. If a
deposit or a membership creation times out, you **cannot** safely retry: you have no
way to distinguish a lost response from a lost request. Reconcile with
`GET /digiposte/v3/memberships` before re-issuing anything.

## Version drift

Six v3 operations are labelled `OBSOLETE` or `PROCHAINEMENT DECOMISSIONNE` in their
French titles in La Poste's own resource catalogue, while carrying **no**
`deprecated: true` flag in the OpenAPI. The catalogue points integrators at `v4`
equivalents on `api.digiposte.fr` (`/api/v4/memberships`,
`/api/v4/partner/{partner_id}/memberships`,
`/api/v4/memberships/{route_code}/documents/certified`). See
`overlays/la-poste-groupe-digiposte-overlay.yaml`, which makes those deprecations
machine-readable. Prefer the v4 paths for new work.

## Errors

400, 403, 404, 409 and 412 each have a named response schema
(`BadRequest_PostUserCustomizationUrl_Conflict`, `BadRequest_GetPartnerProcedures`,
and so on). The schema **name** carries the semantics; there is no separate error
registry. Nothing here is RFC 9457.
