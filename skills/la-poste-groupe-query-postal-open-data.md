---
name: la-poste-query-postal-open-data
description: >-
  Query La Poste's open datasets - postal codes, contact points, opening hours,
  services, accessibility, self-service machines, street letterboxes and new
  communes - either directly on data.laposte.fr with no key, or through the Okapi
  gateway with one.
api: La Poste Open Data v1
base_url: https://data.laposte.fr/data-fair/api/v1
spec: openapi/la-poste-groupe-open-data-openapi.json
operations:
  - listDatasets      # GET /datasets
  - readDescription   # GET /datasets/{id}
  - readSchema        # GET /datasets/{id}/schema
  - readLines         # GET /datasets/{id}/lines
  - getValuesAgg      # GET /datasets/{id}/values_agg
  - getVocabulary     # GET /vocabulary
  - readApiDoc        # GET /datasets/{id}/api-docs.json
  - ping              # GET /ping
generated: '2026-09-02'
method: generated
source: openapi/la-poste-groupe-open-data-openapi.json
---

# Query La Poste postal open data

This is the most agent-friendly surface La Poste operates, and the least advertised.

## Two front doors

1. **Direct** - `https://data.laposte.fr/data-fair/api/v1`. This is the Data Fair
   instance La Poste self-hosts. It serves its own OpenAPI 3.1 at
   `/data-fair/api/v1/api-docs.json` and answers read queries without a key.
2. **Gateway** - `https://api.laposte.fr/opendata/v1`, which requires an
   `X-Okapi-Key` and exposes named aliases: `/codespostaux`, `/pointscontact`,
   `/horairesbureaux`, `/servicesbureaux`, `/accessibilitebureaux`,
   `/automatesbureaux`, `/boitesrue`, `/communesnouvelles`.

Prefer the direct surface for exploration; it is where the machine-readable
description lives.

## Discovery

Start at `https://data.laposte.fr/.well-known/api-catalog`. It is a real **RFC 9727**
linkset with 21 anchors, and every anchor carries a `service-desc` link to a
per-dataset OpenAPI (`application/vnd.oai.openapi+json;version=3.0`), a `service-doc`
HTML link and a `status` link. Nothing on developer.laposte.fr points at it.

Then:

- `listDatasets` - `GET /datasets` to enumerate.
- `readDescription` - `GET /datasets/{id}` for metadata.
- `readSchema` - `GET /datasets/{id}/schema` for the field list.
- `readApiDoc` - `GET /datasets/{id}/api-docs.json` for a dataset-specific OpenAPI.
- `getVocabulary` - `GET /vocabulary` maps this instance's concepts to
  **schema.org** and **RDF Schema** identifiers. If you already speak schema.org you
  can bind these fields with no bespoke mapping.

## Reading rows

`readLines` - `GET /datasets/{id}/lines`:

- `q` - full-text query
- `select` - sparse fieldset (comma-separated field names)
- `sort` - ordering
- `page` + `size` - page-number paging
- `after` - cursor for deep paging; use this rather than a large `page`
- `format` - alternative output encodings

`getValuesAgg` - `GET /datasets/{id}/values_agg` aggregates without pulling rows.
Use it for counts and facets instead of paging the whole dataset.

## Errors and limits

- 404, 409, 413 and 500 come back as **`text/plain`**, not JSON. Do not assume a
  parseable body on failure.
- **413 appears on twelve operations** - the instance enforces a payload/result size
  ceiling. If you hit it, narrow with `select`, reduce `size`, or aggregate.
- Through the gateway, the plan carries no quota limiter; direct access is
  unmetered but unguaranteed.
- `ping` - `GET /ping` is a health check.

## Everything here is read-only for you

The Data Fair OpenAPI documents `postDataset`, `writeData`, `createLine`,
`deleteAllLines` and `delete` because the software supports them. Those are
administrative operations for the instance owner and they are not yours. Restrict
yourself to the read operations listed in this skill's frontmatter.
