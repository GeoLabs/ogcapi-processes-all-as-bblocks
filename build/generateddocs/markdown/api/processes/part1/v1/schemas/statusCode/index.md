
# statusCode (Schema)

`ogc.api.processes.part1.v1.schemas.statusCode` *v1.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
type: string
nullable: false
enum:
- accepted
- running
- successful
- failed
- dismissed
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v1.schemas.statusCode
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '1.0'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v1/schemas/statusCode/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v1/schemas/statusCode/schema.yaml)

## Sources

* [OGC API - Processes - Part 1: Core (version 1.0, OGC 18-062r2)](https://docs.ogc.org/is/18-062r2/18-062r2.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part1/v1/schemas/statusCode`

