
# OGC Application Package schema (Schema)

`ogc.api.processes.part2.v1.schemas.ogcapppkg` *v0.2*

OGC Application Package with canonical single-or-array executionUnitValue or a backwards-compatible legacy flat executionUnit

[*Status*](http://www.opengis.net/def/status): Under development

## Description

Schema of an OGC Application Package document (Requirement /req/ogcapppkg/schema).

The source is the fragment quoted in the OGC 20-044 draft, with its references
replaced by building block references.

The `docker-example` test is the example from the draft with a top-level `title` added.
The local JSON-LD context preserves `executionUnit` and `processDescription` as
opaque JSON literals, including links, arrays and custom executable documents.
Their contents are validated by JSON Schema, not interpreted as RDF classes.

## Local compatibility and composition

The draft `executionUnit` reference maps to
`ogc.api.processes.part2.v1.schemas.executionUnitValue`, the canonical single-or-array
property-value contract. An `anyOf` additionally accepts the existing public
`ogc.api.processes.part2.v1.schemas.executionUnit` legacy flat container contract.
Only this package's legacy branch excludes `value`; the global legacy schema
is unchanged. Thus an invalid qualified Docker payload cannot escape validation
by also carrying a top-level `image`.

The former direct Part 1 `link` and `qualifiedValue` alternatives are removed:
links and custom qualified values remain supported through `executionUnitBase`,
with Docker/CWL payload validation enforced there. An untyped qualified value
is not an execution unit.

When present, `processDescription.process` composes Part 1 `process` with
`staticIndicator` to retain the full process structure and validate the optional
DRU `mutable` flag. These compatibility/composition rules are local fixes, not
an amendment of the official draft. Draft limitations in the container and
binding schemas remain documented on those blocks.
## Examples

### OGC Application Package with CWL reference
#### json
```json
{
  "executionUnit": {
    "href": "https://github.com/Terradue/ogc-eo-application-package-hands-on/releases/download/1.5.0/app-water-bodies-cloud-native.1.5.0.cwl",
    "type": "application/cwl"
  }
}
```

#### jsonld
```jsonld
{
  "@context": "https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/context.jsonld",
  "executionUnit": {
    "href": "https://github.com/Terradue/ogc-eo-application-package-hands-on/releases/download/1.5.0/app-water-bodies-cloud-native.1.5.0.cwl",
    "type": "application/cwl"
  }
}
```

#### ttl
```ttl
@prefix proc: <https://w3id.org/ogc/api/processes/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

[] proc:executionUnit "{\"href\":\"https://github.com/Terradue/ogc-eo-application-package-hands-on/releases/download/1.5.0/app-water-bodies-cloud-native.1.5.0.cwl\",\"type\":\"application/cwl\"}"^^rdf:JSON .


```


### Canonical Docker application package
#### json
```json
{
  "title": "NDVI application package",
  "executionUnit": {
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
}

```

#### jsonld
```jsonld
{
  "@context": "https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/context.jsonld",
  "title": "NDVI application package",
  "executionUnit": {
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
}
```

#### ttl
```ttl
@prefix dct: <http://purl.org/dc/terms/> .
@prefix proc: <https://w3id.org/ogc/api/processes/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

[] dct:title "NDVI application package" ;
    proc:executionUnit "{\"type\":\"docker\",\"value\":{\"bindings\":{\"inputBindings\":{\"inputImage\":{\"inputSeparator\":\",\",\"prefix\":\"inputsImages=\"}},\"outputBindings\":{\"outputImage\":{\"glob\":\"$(\\\"/outputs/ndvi_\\\" + inputs.inputImage.basename)\"}}},\"config\":{\"cpuMax\":5,\"cpuMin\":2,\"memoryMax\":3,\"memoryMin\":1},\"deployment\":\"local\",\"image\":\"mydocker/ndvi:latest\"}}"^^rdf:JSON .


```


### Canonical execution unit array
#### json
```json
{
  "executionUnit": [
    {"type": "docker", "value": {"image": "example/echo:1"}},
    {"href": "https://example.com/echo.cwl", "type": "application/cwl"}
  ]
}
```

#### jsonld
```jsonld
{
  "@context": "https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/context.jsonld",
  "executionUnit": [
    {
      "type": "docker",
      "value": {
        "image": "example/echo:1"
      }
    },
    {
      "href": "https://example.com/echo.cwl",
      "type": "application/cwl"
    }
  ]
}
```

#### ttl
```ttl
@prefix proc: <https://w3id.org/ogc/api/processes/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

[] proc:executionUnit "[{\"type\":\"docker\",\"value\":{\"image\":\"example/echo:1\"}},{\"href\":\"https://example.com/echo.cwl\",\"type\":\"application/cwl\"}]"^^rdf:JSON .


```


### Legacy flat container application package
#### json
```json
{"executionUnit": {"type": "docker", "image": "example/echo:1"}}
```

#### jsonld
```jsonld
{
  "@context": "https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/context.jsonld",
  "executionUnit": {
    "type": "docker",
    "image": "example/echo:1"
  }
}
```

#### ttl
```ttl
@prefix proc: <https://w3id.org/ogc/api/processes/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .

[] proc:executionUnit "{\"image\":\"example/echo:1\",\"type\":\"docker\"}"^^rdf:JSON .


```

## Schema

```yaml
type: object
required:
- executionUnit
properties:
  processDescription:
    type: object
    required:
    - process
    properties:
      process:
        allOf:
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/process/schema.yaml
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/staticIndicator/schema.yaml
    x-jsonld-id: https://w3id.org/ogc/api/processes/processDescription
    x-jsonld-type: '@json'
  executionUnit:
    anyOf:
    - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitValue/schema.yaml
    - allOf:
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnit/schema.yaml
      - not:
          required:
          - value
    x-jsonld-id: https://w3id.org/ogc/api/processes/executionUnit
    x-jsonld-type: '@json'
x-jsonld-prefixes:
  proc: https://w3id.org/ogc/api/processes/
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.ogcapppkg
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '0.2'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "processDescription": {
      "@id": "proc:processDescription",
      "@type": "@json"
    },
    "executionUnit": {
      "@id": "proc:executionUnit",
      "@type": "@json"
    },
    "title": "dct:title",
    "description": "dct:description",
    "keywords": "proc:keywords",
    "nullable": "proc:nullable",
    "type": "proc:type",
    "$ref": {
      "@id": "proc:ref",
      "@type": "@id"
    },
    "default": {
      "@id": "proc:default",
      "@type": "@json"
    },
    "enum": {
      "@id": "proc:enum",
      "@container": "@set"
    },
    "minOccurs": "proc:minOccurs",
    "maxOccurs": "proc:maxOccurs",
    "dct": "http://purl.org/dc/terms/",
    "proc": "https://w3id.org/ogc/api/processes/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg/context.jsonld)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/schemas/ogcapppkg`

