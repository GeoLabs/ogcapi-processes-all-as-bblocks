
# landingPage (Schema)

`ogc.api.processes.part1.v2.schemas.common-core.landingPage` *v2.0*

This building block corresponds to the schema for an OGC API Features landingPage

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: object
required:
- links
properties:
  title:
    type: string
    example: Example processing server
  description:
    type: string
    example: Example server implementing the OGC API - Processes 1.0 Standard
  attribution:
    type: string
    title: attribution for the Processes API
    description: The `attribution` should be short and intended for presentation to
      a user, for example, in a corner of a map. Parts of the text can be links to
      other resources if additional information is needed. The string can include
      HTML markup.
  links:
    type: array
    items:
      $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/common-core/link/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.common-core.landingPage
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/common-core/landingPage/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v2/schemas/common-core/landingPage/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (2.0 draft, OGC 18-062r3)](https://docs.ogc.org/DRAFTS/18-062r3.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v2/schemas/common-core/landingPage`

