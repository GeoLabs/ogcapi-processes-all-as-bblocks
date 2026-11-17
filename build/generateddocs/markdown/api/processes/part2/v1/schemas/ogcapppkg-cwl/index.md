
# CWL Encoding for Process Deployment (Schema)

`ogc.api.processes.part2.v1.schemas.ogcapppkg-cwl` *v0.1*

Common Workflow Language (CWL) document encoding for Deploy/Replace operations. The request body is a complete CWL document (Workflow, CommandLineTool, or ExpressionTool).

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# CWL Encoding for Process Deployment

This building block defines the **CWL encoding** for Deploy and Replace operations in OGC API - Processes - Part 2.

When using media types `application/cwl` or `application/cwl+yaml`, the **entire request body is a CWL document** - not an OGC Application Package wrapper.

## CWL Conformance Class

The CWL conformance class enables deploying processes using Common Workflow Language documents.

## Benefits

- **Native CWL** - Use CWL documents directly without wrapping
- **Tool Ecosystem** - Compatible with CWL tools and validators
- **Workflow Portability** - CWL is portable across platforms
- **Version Control** - CWL files can be versioned independently

## Real-World Example

The example for this building block uses a complete Earth Observation workflow from the Terradue hands-on tutorial:
[Water Bodies Detection Workflow](https://github.com/Terradue/ogc-eo-application-package-hands-on/releases/download/1.5.0/app-water-bodies-cloud-native.1.5.0.cwl) that is described [here](https://eoap.github.io/mastering-app-package/app/water-bodies-detection/).



## Examples

### CWL Workflow - Water Bodies Detection
#### yaml
```yaml
cwlVersion: v1.0
$namespaces:
  s: https://schema.org/
s:softwareVersion: 1.4.1
schemas:
  - http://schema.org/version/9.0/schemaorg-current-http.rdf
$graph:
  - class: Workflow
    id: water_bodies
    label: Water bodies detection based on NDWI and otsu threshold
    doc: Water bodies detection based on NDWI and otsu threshold
    requirements:
      - class: ScatterFeatureRequirement
      - class: SubworkflowFeatureRequirement
    inputs:
      aoi:
        label: area of interest
        doc: area of interest as a bounding box
        type: string
      epsg:
        label: EPSG code
        doc: EPSG code
        type: string
        default: "EPSG:4326"
      stac_items:
        label: Sentinel-2 STAC items
        doc: list of Sentinel-2 COG STAC items
        type: string[]
      bands:
        label: bands used for the NDWI
        doc: bands used for the NDWI
        type: string[]
        default: ["green", "nir"]
    outputs:
      - id: stac_catalog
        outputSource:
          - node_stac/stac_catalog
        type: Directory
    steps:
      node_water_bodies:
        run: "#detect_water_body"
        in:
          item: stac_items
          aoi: aoi
          epsg: epsg
          bands: bands
        out:
          - detected_water_body
        scatter: item
        scatterMethod: dotproduct
      node_stac:
        run: "#stac"
        in:
          item: stac_items
          rasters:
            source: node_water_bodies/detected_water_body
        out:
          - stac_catalog
  - class: Workflow
    id: detect_water_body
    label: Water body detection based on NDWI and otsu threshold
    doc: Water body detection based on NDWI and otsu threshold
    requirements:
      - class: ScatterFeatureRequirement
    inputs:
      aoi:
        doc: area of interest as a bounding box
        type: string
      epsg:
        doc: EPSG code
        type: string
        default: "EPSG:4326"
      bands:
        doc: bands used for the NDWI
        type: string[]
      item:
        doc: STAC item
        type: string
    outputs:
      - id: detected_water_body
        outputSource:
          - node_otsu/binary_mask_item
        type: File
    steps:
      node_crop:
        run: "#crop"
        in:
          item: item
          aoi: aoi
          epsg: epsg
          band: bands
        out:
          - cropped
        scatter: band
        scatterMethod: dotproduct
      node_normalized_difference:
        run: "#norm_diff"
        in:
          rasters:
            source: node_crop/cropped
        out:
          - ndwi
      node_otsu:
        run: "#otsu"
        in:
          raster:
            source: node_normalized_difference/ndwi
        out:
          - binary_mask_item
  - class: CommandLineTool
    id: crop
    requirements:
      InlineJavascriptRequirement: {}
      EnvVarRequirement:
        envDef:
          PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
          PYTHONPATH: /app
      ResourceRequirement:
        coresMax: 1
        ramMax: 512
    hints:
      DockerRequirement:
        dockerPull: ghcr.io/terradue/ogc-eo-application-package-hands-on/crop:1.5.0
    baseCommand: ["python", "-m", "app"]
    arguments: []
    inputs:
      item:
        type: string
        inputBinding:
          prefix: --input-item
      aoi:
        type: string
        inputBinding:
          prefix: --aoi
      epsg:
        type: string
        inputBinding:
          prefix: --epsg
      band:
        type: string
        inputBinding:
          prefix: --band
    outputs:
      cropped:
        outputBinding:
          glob: '*.tif'
        type: File
  - class: CommandLineTool
    id: norm_diff
    requirements:
      InlineJavascriptRequirement: {}
      EnvVarRequirement:
        envDef:
          PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
          PYTHONPATH: /app
      ResourceRequirement:
        coresMax: 1
        ramMax: 512
    hints:
      DockerRequirement:
        dockerPull: ghcr.io/terradue/ogc-eo-application-package-hands-on/norm_diff:1.5.0
    baseCommand: ["python", "-m", "app"]
    arguments: []
    inputs:
      rasters:
        type: File[]
        inputBinding:
          position: 1
    outputs:
      ndwi:
        outputBinding:
          glob: '*.tif'
        type: File
  - class: CommandLineTool
    id: otsu
    requirements:
      InlineJavascriptRequirement: {}
      EnvVarRequirement:
        envDef:
          PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
          PYTHONPATH: /app
      ResourceRequirement:
        coresMax: 1
        ramMax: 512
    hints:
      DockerRequirement:
        dockerPull: ghcr.io/terradue/ogc-eo-application-package-hands-on/otsu:1.5.0
    baseCommand: ["python", "-m", "app"]
    arguments: []
    inputs:
      raster:
        type: File
        inputBinding:
          position: 1
    outputs:
      binary_mask_item:
        outputBinding:
          glob: '*.tif'
        type: File
  - class: CommandLineTool
    id: stac
    requirements:
      InlineJavascriptRequirement: {}
      EnvVarRequirement:
        envDef:
          PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
          PYTHONPATH: /app
      ResourceRequirement:
        coresMax: 1
        ramMax: 512
    hints:
      DockerRequirement:
        dockerPull: ghcr.io/terradue/ogc-eo-application-package-hands-on/stac:1.5.0
    baseCommand: ["python", "-m", "app"]
    arguments: []
    inputs:
      item:
        type:
          type: array
          items: string
          inputBinding:
            prefix: --input-item
      rasters:
        type:
          type: array
          items: File
          inputBinding:
            prefix: --water-body
    outputs:
      stac_catalog:
        outputBinding:
          glob: .
        type: Directory

```

## Schema

```yaml
$ref: https://ogcincubator.github.io/bblocks-cwl/build/annotated/cwl/v1_2_1/CWL/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.processes.part2.v1.schemas.ogcapppkg-cwl
  register: https://jfarduino.github.io/ogcapi-processes-bblocks/build/register.json
  version: '0.1'
  dateOfLastChange: '2026-11-13'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg-cwl/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg-cwl/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "version": "cwl:SoftwarePackage/version",
    "doc": "http://www.w3.org/2000/01/rdf-schema#comment",
    "label": "http://www.w3.org/2000/01/rdf-schema#label",
    "arguments": {
      "@context": {
        "itemSeparator": "cwl:CommandLineBinding/itemSeparator",
        "position": "cwl:CommandLineBinding/position",
        "prefix": "cwl:CommandLineBinding/prefix",
        "shellQuote": "cwl:CommandLineBinding/shellQuote",
        "valueFrom": "cwl:valueFrom"
      },
      "@id": "cwl:arguments",
      "@container": "@list"
    },
    "baseCommand": {
      "@id": "cwl:baseCommand",
      "@container": "@list"
    },
    "hints": {
      "@context": {
        "DockerRequirement": "cwl:DockerRequirement",
        "EnvVarRequirement": "cwl:EnvVarRequirement",
        "InitialWorkDirRequirement": "cwl:InitialWorkDirRequirement",
        "InlineJavascriptRequirement": "cwl:InlineJavascriptRequirement",
        "InplaceUpdateRequirement": "cwl:InplaceUpdateRequirement",
        "LoadListingRequirement": "cwl:LoadListingRequirement",
        "MultipleInputFeatureRequirement": "cwl:MultipleInputFeatureRequirement",
        "NetworkAccess": "cwl:NetworkAccess",
        "ResourceRequirement": "cwl:ResourceRequirement",
        "ScatterFeatureRequirement": "cwl:ScatterFeatureRequirement",
        "SchemaDefRequirement": "cwl:SchemaDefRequirement",
        "ShellCommandRequirement": "cwl:ShellCommandRequirement",
        "SoftwareRequirement": "cwl:SoftwareRequirement",
        "StepInputExpressionRequirement": "cwl:StepInputExpressionRequirement",
        "SubworkflowFeatureRequirement": "cwl:SubworkflowFeatureRequirement",
        "ToolTimeLimit": "cwl:ToolTimeLimit",
        "WorkReuse": "cwl:WorkReuse",
        "dockerFile": "cwl:DockerRequirement/dockerFile",
        "dockerImageId": "cwl:DockerRequirement/dockerImageId",
        "dockerImport": "cwl:DockerRequirement/dockerImport",
        "dockerLoad": "cwl:DockerRequirement/dockerLoad",
        "dockerOutputDirectory": "cwl:DockerRequirement/dockerOutputDirectory",
        "dockerPull": "cwl:DockerRequirement/dockerPull",
        "packages": {
          "@context": {
            "package": "cwl:SoftwarePackage/package",
            "specs": {
              "@id": "cwl:SoftwarePackage/specs",
              "@type": "@id"
            }
          },
          "@id": "cwl:SoftwareRequirement/packages",
          "@container": "@id"
        },
        "envDef": {
          "@context": {
            "envName": "cwl:EnvironmentDef/envName",
            "envValue": "cwl:EnvironmentDef/envValue"
          },
          "@id": "cwl:EnvVarRequirement/envDef",
          "@container": "@id"
        },
        "types": {
          "@context": {
            "type": {
              "@id": "sld:type",
              "@type": "@vocab"
            },
            "fields": {
              "@context": {
                "format": {
                  "@id": "cwl:format",
                  "@type": "@id"
                },
                "loadContents": "cwl:loadContents",
                "secondaryFiles": "cwl:secondaryFiles",
                "streamable": "cwl:FieldBase/streamable"
              },
              "@id": "sld:fields",
              "@container": "@id"
            },
            "name": "@id",
            "items": {
              "@id": "sld:items",
              "@type": "@vocab"
            }
          },
          "@id": "cwl:SchemaDefRequirement/types"
        },
        "listing": "cwl:listing",
        "expressionLib": "cwl:InlineJavascriptRequirement/expressionLib",
        "inplaceUpdate": "cwl:InplaceUpdateRequirement/inplaceUpdate",
        "loadListing": "cwl:loadListing",
        "networkAccess": "cwl:NetworkAccess/networkAccess",
        "coresMin": "cwl:ResourceRequirement/coresMin",
        "coresMax": "cwl:ResourceRequirement/coresMax",
        "ramMin": "cwl:ResourceRequirement/ramMin",
        "ramMax": "cwl:ResourceRequirement/ramMax",
        "outdirMin": "cwl:ResourceRequirement/outdirMin",
        "outdirMax": "cwl:ResourceRequirement/outdirMax",
        "tmpdirMin": "cwl:ResourceRequirement/tmpdirMin",
        "tmpdirMax": "cwl:ResourceRequirement/tmpdirMax",
        "timelimit": "cwl:ToolTimeLimit/timelimit",
        "enableReuse": "cwl:WorkReuse/enableReuse"
      },
      "@id": "cwl:hints",
      "@container": "@type"
    },
    "id": "@id",
    "inputs": {
      "@context": {
        "default": {
          "@context": {
            "basename": "cwl:basename",
            "location": "@id",
            "nameroot": "cwl:File/nameroot",
            "path": {
              "@id": "cwl:path",
              "@type": "@id"
            }
          },
          "@id": "sld:default"
        },
        "type": {
          "@id": "sld:type",
          "@type": "@vocab"
        },
        "inputBinding": {
          "@context": {
            "itemSeparator": "cwl:CommandLineBinding/itemSeparator",
            "position": "cwl:CommandLineBinding/position",
            "prefix": "cwl:CommandLineBinding/prefix",
            "shellQuote": "cwl:CommandLineBinding/shellQuote",
            "valueFrom": "cwl:valueFrom"
          },
          "@id": "cwl:inputBinding"
        }
      },
      "@id": "cwl:inputs",
      "@container": "@id"
    },
    "intent": {
      "@id": "cwl:Process/intent",
      "@type": "@id"
    },
    "outputs": {
      "@context": {
        "outputBinding": {
          "@context": {
            "glob": "cwl:CommandOutputBinding/glob"
          },
          "@id": "cwl:outputBinding"
        },
        "type": {
          "@id": "sld:type",
          "@type": "@vocab"
        }
      },
      "@id": "cwl:outputs",
      "@container": "@id"
    },
    "requirements": {
      "@context": {
        "DockerRequirement": "cwl:DockerRequirement",
        "EnvVarRequirement": "cwl:EnvVarRequirement",
        "InitialWorkDirRequirement": "cwl:InitialWorkDirRequirement",
        "InlineJavascriptRequirement": "cwl:InlineJavascriptRequirement",
        "InplaceUpdateRequirement": "cwl:InplaceUpdateRequirement",
        "LoadListingRequirement": "cwl:LoadListingRequirement",
        "MultipleInputFeatureRequirement": "cwl:MultipleInputFeatureRequirement",
        "NetworkAccess": "cwl:NetworkAccess",
        "ResourceRequirement": "cwl:ResourceRequirement",
        "ScatterFeatureRequirement": "cwl:ScatterFeatureRequirement",
        "SchemaDefRequirement": "cwl:SchemaDefRequirement",
        "ShellCommandRequirement": "cwl:ShellCommandRequirement",
        "SoftwareRequirement": "cwl:SoftwareRequirement",
        "StepInputExpressionRequirement": "cwl:StepInputExpressionRequirement",
        "SubworkflowFeatureRequirement": "cwl:SubworkflowFeatureRequirement",
        "ToolTimeLimit": "cwl:ToolTimeLimit",
        "WorkReuse": "cwl:WorkReuse",
        "dockerFile": "cwl:DockerRequirement/dockerFile",
        "dockerImageId": "cwl:DockerRequirement/dockerImageId",
        "dockerImport": "cwl:DockerRequirement/dockerImport",
        "dockerLoad": "cwl:DockerRequirement/dockerLoad",
        "dockerOutputDirectory": "cwl:DockerRequirement/dockerOutputDirectory",
        "dockerPull": "cwl:DockerRequirement/dockerPull",
        "packages": {
          "@context": {
            "package": "cwl:SoftwarePackage/package",
            "specs": {
              "@id": "cwl:SoftwarePackage/specs",
              "@type": "@id"
            }
          },
          "@id": "cwl:SoftwareRequirement/packages",
          "@container": "@id"
        },
        "envDef": {
          "@context": {
            "envName": "cwl:EnvironmentDef/envName",
            "envValue": "cwl:EnvironmentDef/envValue"
          },
          "@id": "cwl:EnvVarRequirement/envDef",
          "@container": "@id"
        },
        "types": {
          "@context": {
            "type": {
              "@id": "sld:type",
              "@type": "@vocab"
            },
            "fields": {
              "@context": {
                "format": {
                  "@id": "cwl:format",
                  "@type": "@id"
                },
                "loadContents": "cwl:loadContents",
                "secondaryFiles": "cwl:secondaryFiles",
                "streamable": "cwl:FieldBase/streamable"
              },
              "@id": "sld:fields",
              "@container": "@id"
            },
            "name": "@id",
            "items": {
              "@id": "sld:items",
              "@type": "@vocab"
            }
          },
          "@id": "cwl:SchemaDefRequirement/types"
        },
        "listing": "cwl:listing",
        "expressionLib": "cwl:InlineJavascriptRequirement/expressionLib",
        "inplaceUpdate": "cwl:InplaceUpdateRequirement/inplaceUpdate",
        "loadListing": "cwl:loadListing",
        "networkAccess": "cwl:NetworkAccess/networkAccess",
        "coresMin": "cwl:ResourceRequirement/coresMin",
        "coresMax": "cwl:ResourceRequirement/coresMax",
        "ramMin": "cwl:ResourceRequirement/ramMin",
        "ramMax": "cwl:ResourceRequirement/ramMax",
        "outdirMin": "cwl:ResourceRequirement/outdirMin",
        "outdirMax": "cwl:ResourceRequirement/outdirMax",
        "tmpdirMin": "cwl:ResourceRequirement/tmpdirMin",
        "tmpdirMax": "cwl:ResourceRequirement/tmpdirMax",
        "timelimit": "cwl:ToolTimeLimit/timelimit",
        "enableReuse": "cwl:WorkReuse/enableReuse"
      },
      "@id": "cwl:requirements",
      "@container": "@type"
    },
    "scatter": {
      "@id": "cwl:scatter",
      "@type": "@id",
      "@container": "@list"
    },
    "scatterMethod": {
      "@id": "cwl:scatterMethod",
      "@type": "@vocab"
    },
    "stderr": "cwl:stderr",
    "stdin": "cwl:stdin",
    "stdout": "cwl:stdout",
    "class": "@type",
    "CommandLineTool": "cwl:CommandLineTool",
    "ExpressionTool": "cwl:ExpressionTool",
    "Workflow": "cwl:Workflow",
    "$graph": "@graph",
    "steps": {
      "@context": {
        "in": {
          "@context": {
            "linkMerge": "cwl:linkMerge",
            "source": {
              "@id": "cwl:source",
              "@type": "@id"
            },
            "valueFrom": "cwl:valueFrom",
            "default": {
              "@context": {
                "basename": "cwl:basename",
                "location": "@id",
                "nameroot": "cwl:File/nameroot",
                "path": {
                  "@id": "cwl:path",
                  "@type": "@id"
                }
              },
              "@id": "sld:default",
              "@container": "@list"
            }
          },
          "@id": "cwl:in",
          "@container": "@id"
        },
        "out": {
          "@id": "cwl:out",
          "@type": "@id"
        },
        "run": {
          "@id": "cwl:run",
          "@type": "@id"
        },
        "when": "cwl:when"
      },
      "@id": "cwl:Workflow/steps",
      "@container": "@id"
    },
    "writable": "cwl:Dirent/writable",
    "checksum": "cwl:File/checksum",
    "size": "cwl:File/size",
    "null": "sld:null",
    "boolean": "xsd:boolean",
    "int": "xsd:int",
    "integer": "xsd:int",
    "long": "xsd:long",
    "float": "xsd:float",
    "double": "xsd:double",
    "string": "xsd:string",
    "File": "cwl:File",
    "Directory": "cwl:Directory",
    "BuiltinRequirement": "ogccwl:BuiltinRequirement",
    "OGCAPIRequirement": "ogccwl:OGCAPIRequirement",
    "WPS1Requirement": "ogccwl:WPS1Requirement",
    "s": "https://schema.org/",
    "cwl": "https://w3id.org/cwl/cwl#",
    "cwltool": "http://commonwl.org/cwltool#",
    "sld": "https://w3id.org/cwl/salad#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "ogccwl": "https://w3id.org/ogc/cwl/",
    "dct": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://jfarduino.github.io/ogcapi-processes-bblocks/build/annotated/api/processes/part2/v1/schemas/ogcapppkg-cwl/context.jsonld)

## Sources

* [OGC API - Processes - Part 2: Deploy, Replace, Undeploy - CWL Encoding](https://docs.ogc.org/DRAFTS/20-044.html#_2016252b-e710-0f32-a102-1c4635e52f7c)
* [Common Workflow Language Specification](https://www.commonwl.org/v1.0/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-processes-bblocks](https://github.com/JFarduino/ogcapi-processes-bblocks)
* Path: `_sources/part2/v1/schemas/ogcapppkg-cwl`

