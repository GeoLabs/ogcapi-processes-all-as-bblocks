
# additionalParameter (Schema)

`ogc.api.processes.part1.v1.schemas.additionalParameter` *v1.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: object
required:
- name
- value
properties:
  name:
    type: string
  value:
    type: array
    items:
      oneOf:
      - type: string
      - type: number
      - type: integer
      - type: array
        items: {}
      - type: object
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v1.schemas.additionalParameter
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '1.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/additionalParameter/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/additionalParameter/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (version 1.0, OGC 18-062r2)](https://docs.ogc.org/is/18-062r2/18-062r2.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v1/schemas/additionalParameter`

