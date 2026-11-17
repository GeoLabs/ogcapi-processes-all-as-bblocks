
# schema (Schema)

`ogc.api.processes.part1.v1.schemas.schema` *v1.0*

None

[*Status*](http://www.opengis.net/def/status): Under development

## Schema

```yaml
$schema: http://json-schema.org/draft-04/schema#
oneOf:
- $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
- type: object
  properties:
    title:
      type: string
    multipleOf:
      type: number
      minimum: 0
      exclusiveMinimum: true
    maximum:
      type: number
    exclusiveMaximum:
      type: boolean
      default: false
    minimum:
      type: number
    exclusiveMinimum:
      type: boolean
      default: false
    maxLength:
      type: integer
      minimum: 0
    minLength:
      type: integer
      minimum: 0
      default: 0
    pattern:
      type: string
      format: regex
    maxItems:
      type: integer
      minimum: 0
    minItems:
      type: integer
      minimum: 0
      default: 0
    uniqueItems:
      type: boolean
      default: false
    maxProperties:
      type: integer
      minimum: 0
    minProperties:
      type: integer
      minimum: 0
      default: 0
    required:
      type: array
      items:
        type: string
      minItems: 1
      uniqueItems: true
    enum:
      type: array
      items: {}
      minItems: 1
      uniqueItems: false
    type:
      type: string
      enum:
      - array
      - boolean
      - integer
      - number
      - object
      - string
    not:
      oneOf:
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
    allOf:
      type: array
      items:
        oneOf:
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
    oneOf:
      type: array
      items:
        oneOf:
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
    anyOf:
      type: array
      items:
        oneOf:
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
    items:
      oneOf:
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
    properties:
      type: object
      additionalProperties:
        oneOf:
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
        - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
    additionalProperties:
      oneOf:
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml
      - $ref: https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/reference/schema.yaml
      - type: boolean
      default: true
    description:
      type: string
    format:
      type: string
    default: {}
    nullable:
      type: boolean
      default: false
    readOnly:
      type: boolean
      default: false
    writeOnly:
      type: boolean
      default: false
    example: {}
    deprecated:
      type: boolean
      default: false
    contentMediaType:
      type: string
    contentEncoding:
      type: string
    contentSchema:
      type: string
  additionalProperties: false
x-jsonld-vocab: https://w3id.org/ogc/api/schema/
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part1.v1.schemas.schema
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '1.0'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "https://w3id.org/ogc/api/schema/",
    "not": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "allOf": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "oneOf": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "anyOf": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "items": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "properties": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "additionalProperties": {
      "@context": {
        "@vocab": "https://w3id.org/ogc/api/schema/"
      }
    },
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part1/v1/schemas/schema/context.jsonld)

## Sources

* [OGC API - Processes - Part 1: Core (version 1.0, OGC 18-062r2)](https://docs.ogc.org/is/18-062r2/18-062r2.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part1/v1/schemas/schema`

