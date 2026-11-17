
# bbox (Schema)

`ogc.api.processes.part1.v2.schemas.bbox` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: object
required:
- bbox
properties:
  bbox:
    type: array
    oneOf:
    - minItems: 4
      maxItems: 4
    - minItems: 6
      maxItems: 6
    items:
      type: number
  crs:
    $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/processes-core/bbox-def-crs/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.bbox
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/bbox/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/bbox/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (2.0 draft, OGC 18-062r3)](https://docs.ogc.org/DRAFTS/18-062r3.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v2/schemas/bbox`

