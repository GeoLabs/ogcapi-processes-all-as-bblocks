
# schemaAndOccurrences (Schema)

`ogc.api.processes.part1.v2.schemas.processes-core.schemaAndOccurrences` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: object
required:
- schema
properties:
  schema:
    $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/schema/schema.yaml
  minOccurs:
    type: integer
    default: 1
  maxOccurs:
    oneOf:
    - type: integer
      default: 1
    - type: string
      enum:
      - unbounded
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.processes-core.schemaAndOccurrences
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/processes-core/schemaAndOccurrences/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/processes-core/schemaAndOccurrences/schema.yaml)

## Sources

* [OGC API - Processes pinned official Core component](https://raw.githubusercontent.com/opengeospatial/ogcapi-processes/0f9c3d88ccdb1802f6356fd39e7963df7b8dadae/openapi/schemas/processes-core/schemaAndOccurrences.yaml)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v2/schemas/processes-core/schemaAndOccurrences`

