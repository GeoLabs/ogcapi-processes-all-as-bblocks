
# Execution unit base schema (Schema)

`ogc.api.processes.part2.v1.schemas.executionUnitBase` *v1.1.0*

Base schema of a single execution unit (DRAFT): either a link to the execution unit, or an inline qualified value describing a container image, a CWL script, or another custom encoding.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

One execution unit: a link, or a qualified value holding a container image, a CWL document or a custom type.

The source is the schema fragment quoted in the OGC 20-044 draft, with its
references replaced by building block references. The descriptions of container,
CWL and custom script encodings retain the draft's intent.

## Local schema composition fixes (not amendments of the official draft)

- The draft refers to `../cwl/cwl.yaml`, which it does not include. This block uses the CWL v1.2 schema URL that the draft gives in a comment.
- The draft's third `anyOf` branch accepts any `type`, allowing invalid Docker
  values to bypass the container branch. Here an `if`/`then`/`else` discriminator
  gives `type: docker` or `type: oci` priority and validates `value` against
  `ogc.api.processes.part2.v1.schemas.executionUnitContainer`.
- Otherwise `mediaType: application/cwl` selects the raw remote CWL schema,
  including when `type` is absent. A custom type cannot bypass this check.
- The remaining custom branch requires a string `type` excluding `docker` and
  `oci`. Scripts such as `type: python` retain the qualified-value contract;
  an empty object is a valid custom payload.
- The Part 1 `qualifiedValue` `allOf` is retained; `value` is also explicitly
  required here. Link-only units exclude `value`, so a qualified value with an
  additional `href` cannot escape payload validation through the link branch.

These are local validation/composition fixes. They do not claim changes to the
official draft or runtime support for Docker/CWL deployment. Other draft
limitations, including the loose deployment enum, are documented on
`executionUnitContainer` rather than silently corrected.
## Examples

### Docker qualified value
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


### CWL link
#### json
```json
{
  "href": "https://example.com/ndvi.cwl",
  "type": "application/cwl"
}

```


### Custom qualified value
#### json
```json
{"type": "python", "value": {}}
```

## Schema

```yaml
oneOf:
- allOf:
  - $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v1/schemas/link/schema.yaml
  - not:
      required:
      - value
- allOf:
  - $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/qualifiedExecutionUnitValue/schema.yaml
  - type: object
    required:
    - value
    if:
      required:
      - type
      properties:
        type:
          enum:
          - docker
          - oci
    then:
      description: The execution unit is a container image.
      properties:
        value:
          $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitContainer/schema.yaml
    else:
      if:
        required:
        - mediaType
        properties:
          mediaType:
            const: application/cwl
      then:
        description: The execution unit is CWL script.
        properties:
          value:
            $ref: https://raw.githubusercontent.com/common-workflow-language/cwl-v1.2/main/json-schema/cwl.yaml
      else:
        description: 'The execution unit is not Docker/OCI or CWL and cannot be properly
          described via

          the "mediaType" property of a qualified value using an RFC 2046 media type
          (e.g.

          an "R" or "Python" script). In this case a community-defined or custom token
          may

          be used with the "type" property.'
        required:
        - type
        properties:
          type:
            type: string
            not:
              enum:
              - docker
              - oci
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.executionUnitBase
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: 1.1.0
  dateOfLastChange: '2026-11-17'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitBase/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/executionUnitBase/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part2/v1/schemas/executionUnitBase`

