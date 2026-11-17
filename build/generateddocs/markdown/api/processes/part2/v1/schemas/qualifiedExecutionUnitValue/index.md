
# Qualified execution unit value (Schema)

`ogc.api.processes.part2.v1.schemas.qualifiedExecutionUnitValue` *v1.0.0*

Part 2 support schema for a qualified execution payload of any JSON type. This is not the Part 1 qualifiedInputValue contract.

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
allOf:
- $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/format/schema.yaml
- type: object
  required:
  - value
  properties:
    value: {}
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.qualifiedExecutionUnitValue
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: 1.0.0
  dateOfLastChange: '2026-11-09'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/qualifiedExecutionUnitValue/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/qualifiedExecutionUnitValue/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy (1.0 draft, OGC 20-044)](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/schemas/qualifiedExecutionUnitValue`

