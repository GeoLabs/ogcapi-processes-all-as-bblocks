
# Deploy Success Response (Response)

`ogc.api.processes.part2.v1.responses.deploySuccess` *v0.1*

Response schema for successful process deployment operations

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: object
description: Successful process deployment response
properties:
  status:
    type: string
    enum:
    - success
  message:
    type: string
    description: Success message
  processId:
    type: string
    description: ID of the deployed process
  processSummary:
    $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/staticIndicator/schema.yaml
  links:
    type: array
    items:
      $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/link/schema.yaml
required:
- status
- processId
- processSummary
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.responses.deploySuccess
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '0.1'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/responses/deploySuccess/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/responses/deploySuccess/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](http://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/responses/deploySuccess`

