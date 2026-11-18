
# Process summary with mutability indicator (Schema)

`ogc.api.processes.part2.v1.schemas.staticIndicator` *v0.2*

Extension of Process Summary with mutability indicator for Deploy, Replace, Undeploy operations

[*Status*](http://www.opengis.net/def/status): Under development

## Description

Summary description of a deployed process, returned in the body of a Deploy response (Requirement /req/deploy-replace-undeploy/deploy-response-body).

The migrated draft `processSummary` maps to the existing public
`ogc.api.processes.part2.v1.schemas.staticIndicator`; no duplicate summary schema is
introduced. Unlike the stripped local draft fragment, this block retains its
`allOf` reference to the full Part 1 `processSummary`, including validation of
`outputTransmission`, and the optional boolean `mutable` with `default: true`.

The schema itself is unchanged by consolidation. Tests and metadata are updated.
A JSON Schema default is an annotation, not an instruction to insert a missing
property. The added mutability contract is local DRU composition, not a claim
that the quoted draft summary fragment itself declares `mutable`.
## Examples

### Process summary with explicit mutability
#### json
```json
{
  "id": "custom-classifier",
  "title": "Custom Land Cover Classifier", 
  "description": "User-deployed classification algorithm",
  "version": "2.0.0",
  "jobControlOptions": ["async-execute"],
  "outputTransmission": ["reference"],
  "keywords": ["classification", "machine-learning"],
  "links": [
    {
      "href": "https://api.example.org/processes/custom-classifier",
      "rel": "self",
      "type": "application/json"
    }
  ],
  "mutable": true
}
```


### Deploy response summary
#### json
```json
{
  "id": "EchoProcess",
  "title": "EchoProcess",
  "version": "1.0.0",
  "jobControlOptions": [
    "sync-execute",
    "async-execute"
  ],
  "links": [
    {
      "href": "https://processing.example.org/processes/EchoProcess",
      "rel": "self",
      "type": "application/json",
      "title": "Process description"
    }
  ]
}

```

## Schema

```yaml
allOf:
- $ref: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part1/v1/schemas/processSummary/schema.yaml
- type: object
  properties:
    mutable:
      type: boolean
      default: true
      description: Indicates whether the process can be modified via Deploy, Replace,
        Undeploy operations
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.staticIndicator
  register: https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/register.json
  version: '0.2'
  dateOfLastChange: '2026-11-17'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/staticIndicator/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/ogcapi-processes-all-as-bblocks/build/annotated/api/processes/part2/v1/schemas/staticIndicator/schema.yaml)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy](https://docs.ogc.org/DRAFTS/20-044.html)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks](https://github.com/GeoLabs/ogcapi-processes-all-as-bblocks)
* Path: `_sources/part2/v1/schemas/staticIndicator`

