
# descriptionType (Schema)

`ogc.api.processes.part1.v2.schemas.descriptionType` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: object
properties:
  title:
    type: string
  description:
    type: string
  keywords:
    type: array
    items:
      type: string
  metadata:
    type: array
    items:
      $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/metadata/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.descriptionType
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/descriptionType/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/descriptionType/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (2.0 draft, OGC 18-062r3)](https://docs.ogc.org/DRAFTS/18-062r3.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v2/schemas/descriptionType`

