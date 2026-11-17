
# qualifiedValue (Schema)

`ogc.api.processes.part1.v2.schemas.qualifiedValue` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
allOf:
- $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/format/schema.yaml
- $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/processes-core/dataClasses/schema.yaml
- type: object
  required:
  - value
  properties:
    value:
      $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/value/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.qualifiedValue
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/qualifiedValue/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/qualifiedValue/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core](https://docs.ogc.org/is/18-062r2/18-062r2.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v2/schemas/qualifiedValue`

