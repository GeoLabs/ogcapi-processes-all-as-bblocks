
# bbox-def-crs (Schema)

`ogc.api.processes.part1.v2.schemas.bbox-def-crs` *v2.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
anyOf:
- type: string
  format: uri
  enum:
  - http://www.opengis.net/def/crs/OGC/1.3/CRS84
  - http://www.opengis.net/def/crs/OGC/0/CRS84h
  default: http://www.opengis.net/def/crs/OGC/1.3/CRS84
- type: string
  format: uri
  default: http://www.opengis.net/def/crs/OGC/1.3/CRS84
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v2.schemas.bbox-def-crs
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '2.0'
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/bbox-def-crs/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v2/schemas/bbox-def-crs/schema.yaml)

## Sources

* [OGC API - Processes pinned official Core component](https://raw.githubusercontent.com/opengeospatial/ogcapi-processes/0f9c3d88ccdb1802f6356fd39e7963df7b8dadae/openapi/schemas/processes-core/bbox-def-crs.yaml)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part1/v2/schemas/bbox-def-crs`

