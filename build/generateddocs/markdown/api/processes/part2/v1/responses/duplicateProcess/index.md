
# Duplicate Process Error Response (Response)

`ogc.api.processes.part2.v1.responses.duplicateProcess` *v0.1*

Error response when attempting to deploy a process that already exists

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
description: the process being added is already deployed (i.e. duplicate)
content:
  application/json:
    schema:
      $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/exception/schema.yaml
  text/html:
    schema:
      type: string
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.responses.duplicateProcess
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '0.1'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/responses/duplicateProcess/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/responses/duplicateProcess/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy (Draft)](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/responses/duplicateProcess`

