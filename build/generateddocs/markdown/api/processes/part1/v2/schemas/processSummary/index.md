
# processSummary (Schema)

`ogc.api.processes.part1.v2.schemas.processSummary` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
allOf:
- $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/descriptionType/schema.yaml
- type: object
  required:
  - id
  - version
  properties:
    id:
      type: string
    version:
      type: string
    jobControlOptions:
      type: array
      items:
        $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/jobControlOptions/schema.yaml
    links:
      type: array
      items:
        $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/link/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.processSummary
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/processSummary/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/processSummary/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (2.0 draft, OGC 18-062r3)](https://docs.ogc.org/DRAFTS/18-062r3.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part1/v2/schemas/processSummary`

