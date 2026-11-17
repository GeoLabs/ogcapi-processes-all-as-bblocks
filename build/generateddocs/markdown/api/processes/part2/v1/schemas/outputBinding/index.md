
# Docker output binding (Schema)

`ogc.api.processes.part2.v1.schemas.outputBinding` *v1.0.0*

How a process output is retrieved from a Docker execution unit (Requirement /req/docker/output-binding).

[*Status*](http://www.opengis.net/def/status): Under development

## Description

How a process output is retrieved from a Docker execution unit (Requirement /req/docker/output-binding).

The schema is the fragment quoted in the OGC 20-044 draft, with its references replaced by building block references.

Glob values may be strings or arrays of strings. Validation does not evaluate
glob patterns or the expressions described by the draft.
## Examples

### Output glob string
#### json
```json
{
  "glob": "/outputs/*.tif"
}

```


### Output glob array
#### json
```json
{
  "glob": [
    "/outputs/*.tif",
    "/outputs/*.json"
  ]
}

```

## Schema

```yaml
type: object
description: Defines how to retrieve the output result from the command.
properties:
  glob:
    description: ". Wildcard pattern to find the output on disk or mounted volume.\n.
      Uses UNIX \"glob\" wildcard patterns (see: \"man 7 glob\").\n. See inputBinding.yaml
      for referencing input values in an output\n  binding \"glob\" expression."
    oneOf:
    - type: string
    - type: array
      items:
        type: string
additionalProperties: true
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.outputBinding
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: 1.0.0
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/outputBinding/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/outputBinding/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/schemas/outputBinding`

