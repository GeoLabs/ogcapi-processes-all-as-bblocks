
# inputDescription (Schema)

`ogc.api.processes.part1.v2.schemas.swagger.inputDescription` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
allOf:
- $ref: https://schemas.opengis.net/ogcapi/processes/part1/1.0/openapi/schemas/descriptionType.yaml
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
      $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/swagger/schema/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.swagger.inputDescription
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/swagger/inputDescription/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/swagger/inputDescription/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (2.0 draft, OGC 18-062r3)](https://docs.ogc.org/DRAFTS/18-062r3.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part1/v2/schemas/swagger/inputDescription`

