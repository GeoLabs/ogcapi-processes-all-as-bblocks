
# inputDescription (Schema)

`ogc.api.processes.part1.v1.schemas.swagger.inputDescription` *v1.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
allOf:
- $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/descriptionType/schema.yaml
- type: object
  required:
  - schema
  properties:
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
    schema:
      $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/swagger/schema/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v1.schemas.swagger.inputDescription
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '1.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/swagger/inputDescription/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/swagger/inputDescription/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (version 1.0, OGC 18-062r2)](https://docs.ogc.org/is/18-062r2/18-062r2.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v1/schemas/swagger/inputDescription`

