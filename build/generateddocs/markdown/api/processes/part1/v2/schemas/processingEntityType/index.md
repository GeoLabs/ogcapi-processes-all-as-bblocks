
# processingEntityType (Schema)

`ogc.api.processes.part1.v2.schemas.processingEntityType` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
anyOf:
- $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/apis/schema.yaml
- type: string
  enum:
  - ogc-api-processes
  - openeo
  default: ogc-api-processes
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.processingEntityType
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/processingEntityType/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/processingEntityType/schema.yaml)

## Sources

* [OGC API - Processes pinned official Core component](https://raw.githubusercontent.com/opengeospatial/ogcapi-processes/0f9c3d88ccdb1802f6356fd39e7963df7b8dadae/openapi/schemas/processes-core/processingEntityType.yaml)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part1/v2/schemas/processingEntityType`

