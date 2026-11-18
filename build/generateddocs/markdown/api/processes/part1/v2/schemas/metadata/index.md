
# metadata (Schema)

`ogc.api.processes.part1.v2.schemas.metadata` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
oneOf:
- allOf:
  - $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/link/schema.yaml
  - type: object
    properties:
      role:
        type: string
- type: object
  properties:
    role:
      type: string
    title:
      type: string
    lang:
      type: string
    value:
      oneOf:
      - type: string
      - type: object
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.metadata
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/metadata/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/metadata/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (2.0 draft, OGC 18-062r3)](https://docs.ogc.org/DRAFTS/18-062r3.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part1/v2/schemas/metadata`

