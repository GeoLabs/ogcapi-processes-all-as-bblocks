
# Execution unit property value (single or array) (Schema)

`ogc.api.processes.part2.v1.schemas.executionUnitValue` *v1.0.0*

Canonical value of an OGC Application Package executionUnit property: one executionUnitBase or an array. Distinct from the legacy flat executionUnit container schema.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

Value of the executionUnit property of an OGC Application Package: one execution unit, or an array of them.

The schema is the fragment quoted in the OGC 20-044 draft, with its references replaced by building block references.

Differences from the draft:

- `items` is a single schema here, not the one-element array written in the draft: the array form is not a valid schema in OpenAPI 3.0 or JSON Schema 2020-12.

## Canonical versus legacy contract

The draft's `executionUnit` schema is published here as
`ogc.api.processes.part2.v1.schemas.executionUnitValue`: this is the **property value**,
not the container payload itself. Each element uses `executionUnitBase`, including
the local composition fixes documented there.

The legacy flat contract, now `ogc.api.processes.part2.v1.schemas.executionUnit`, is deliberately
unchanged: it remains the legacy flat `{ "type": "docker", "image": "..." }`
contract. It must not be used as the canonical single-or-array schema.
## Examples

### Single container execution unit
#### json
```json
{
  "type": "docker",
  "value": {
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
}

```


### Execution unit array
#### json
```json
[
  {
    "type": "docker",
    "value": {
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
  },
  {
    "href": "https://example.com/ndvi.cwl",
    "type": "application/cwl"
  }
]

```

## Schema

```yaml
oneOf:
- $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitBase/schema.yaml
- type: array
  items:
    $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitBase/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.executionUnitValue
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: 1.0.0
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitValue/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitValue/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/schemas/executionUnitValue`

