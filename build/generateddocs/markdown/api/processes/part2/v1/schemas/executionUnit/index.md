
# Execution Unit schema (Schema)

`ogc.api.processes.part2.v1.schemas.executionUnit` *v0.1*

Schema for execution units (Docker, OCI containers) for process deployment

[*Status*](http://www.opengis.net/def/status): Under development

## Examples

### Legacy flat container execution unit
#### json
```json
{
  "type": "docker",
  "image": "geolabs/geospatial-processor:2.1.0",
  "deployment": "local",
  "config": {
    "cpuMin": 2,
    "cpuMax": 8,
    "memoryMin": 4,
    "memoryMax": 16,
    "storageTempMin": 10,
    "storageOutputsMin": 20,
    "jobTimeout": 7200
  }
}
```

## Schema

```yaml
description: Resource containing an executable or runtime information for executing
  the process.
type: object
required:
- type
- image
properties:
  type:
    description: Type of execution unit.
    type: string
    enum:
    - docker
    - oci
  image:
    description: Container image reference for the execution unit.
    type: string
  deployment:
    description: Deployment information for the execution unit.
    type: string
    enum:
    - local
    - remote
    - hpc
    - cloud
  config:
    type: object
    description: Hardware requirements and configuration properties for executing
      the process.
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
additionalProperties: true
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.executionUnit
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '0.1'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnit/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnit/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](http://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/schemas/executionUnit`

