
# Docker execution unit value (Schema)

`ogc.api.processes.part2.v1.schemas.executionUnitContainer` *v1.0.0*

Value of the value field of a Docker execution unit (Requirement /req/docker/schema).

[*Status*](http://www.opengis.net/def/status): Under development

## Description

Value of the value field of a Docker execution unit (Requirement /req/docker/schema).

The schema is the fragment quoted in the OGC 20-044 draft, with its references replaced by building block references.

Differences from the draft:

- `required` is a list here. The draft writes `required: image`, which is not a valid schema.

## Draft limitations retained

The draft's `deployment` combines an unrestricted string branch with an enum,
so strings outside `local`, `remote`, `hpc`, and `cloud` remain valid. This is
not silently tightened here. Likewise, the binding maps retain the draft's
`additionalProperties` formulation without adding a missing `type: object`.
Binding objects are checked against the canonical `inputBinding` and
`outputBinding` schemas. The draft example's `inputSeparator` is preserved as an
extension; the declared input binding property is `itemSeparator`.

The local discriminator fix belongs to `executionUnitBase`, not to an amendment
of this draft fragment or a claim that the Docker conformance class is implemented.
## Examples

### Container payload from the draft
#### json
```json
{
  "image": "mydocker/ndvi:latest",
  "bindings": {
    "inputBindings": {
      "inputImage": {
        "prefix": "inputsImages=",
        "inputSeparator": ","
      }
    },
    "outputBindings": {
      "outputImage": {
        "glob": "$(\"/outputs/ndvi_\" + inputs.inputImage.basename)"
      }
    }
  },
  "deployment": "local",
  "config": {
    "cpuMin": 2,
    "cpuMax": 5,
    "memoryMin": 1,
    "memoryMax": 3
  }
}

```

## Schema

```yaml
type: object
required:
- image
properties:
  image:
    description: Container image reference for the execution unit.
    type: string
  deployment:
    description: Deployment information for the execution unit.
    type: string
    anyOf:
    - type: string
    - enum:
      - local
      - remote
      - hpc
      - cloud
  config:
    type: object
    description: 'Hardware requirements and configuration properties for executing
      the

      process.'
    properties:
      cpuMin:
        description: Minimum number of CPUs required to run the process (unit is CPU
          core).
        type: number
        minimum: 1
      cpuMax:
        description: Maximum number of CPU dedicated to the process (unit is CPU core)
        type: number
      memoryMin:
        description: Minimum RAM memory required to run the application (unit is GB)
        type: number
      memoryMax:
        description: Maximum RAM memory dedicated to the application (unit is GB)
        type: number
      storageTempMin:
        description: Minimum required temporary storage size (unit is GB)
        type: number
      storageOutputsMin:
        description: Minimum required output storage size (unit is GB)
        type: number
      jobTimeout:
        description: Timeout delay for a job execution (in seconds)
        type: number
    additionalProperties: true
  bindings:
    type: object
    properties:
      inputBindings:
        additionalProperties:
          $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/inputBinding/schema.yaml
      outputBindings:
        additionalProperties:
          $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/outputBinding/schema.yaml
additionalProperties: true
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.executionUnitContainer
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: 1.0.0
  dateOfLastChange: '2026-11-18'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitContainer/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitContainer/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part2/v1/schemas/executionUnitContainer`

