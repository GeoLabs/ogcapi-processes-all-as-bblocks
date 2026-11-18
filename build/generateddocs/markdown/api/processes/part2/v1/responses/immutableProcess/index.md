
# Immutable Process Error Response (Response)

`ogc.api.processes.part2.v1.responses.immutableProcess` *v0.1*

Error response when attempting to replace or undeploy an immutable process

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
description: the process is not mutable
content:
  application/json:
    schema:
      $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v1/schemas/exception/schema.yaml
  text/html:
    schema:
      type: string
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.responses.immutableProcess
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '0.1'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/responses/immutableProcess/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/responses/immutableProcess/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy (Draft)](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part2/v1/responses/immutableProcess`

