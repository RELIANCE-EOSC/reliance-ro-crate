## RELIANCE RO-crate profile

<!---You can use the [editor on GitHub](https://github.com/RELIANCE-EOSC/reliance-ro-crate/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.-->

* Authors:
  - Oscar Corcho <https://orcid.org/0000-0002-9260-0753>
  - Esteban Gonzalez
  - Daniel Garijo <https://orcid.org/0000-0003-0454-7145>
  - Raul Palma <https://orcid.org/0000-0003-4289-4922>
* Title: RELIANCE RO-Crate profile
* Publisher: [RELIANCE project](https://reliance-project.eu/)
* Version: [1.0]


<!---
  Permalink: <https://w3id.org/workflowhub/workflow-ro-crate/1.0> (this version)  
  <https://w3id.org/workflowhub/workflow-ro-crate/> (latest version)

  [Profile Crate `ro-crate-metadata.json`](ro-crate-metadata.json)
    [Profile Crate preview](ro-crate-preview.html)
  [Example RO-Crate `ro-crate-metadata.json`](example/ro-crate-metadata.json)
    [Example RO-Crate profile preview](example/ro-crate-preview.html)
-->

Please leave any suggestions and comments here: <https://github.com/RELIANCE-EOSC/reliance-ro-crate/issues>

_RELIANCE RO-Crates_ are a specialization of [_RO-Crate_](https://researchobject.github.io/ro-crate/) for packaging data cubes enabling access earth observation data, along with all the necessary and other related artifacts like documentation, images, related infrastructures, etc.  

RELIANCE project uses _RELIANCE RO-Crates_ as an exchange format to package data cubes in Earth Science.


## Concepts

This section uses terminology from the [RO-Crate 1.1 specification](https://w3id.org/ro/crate/1.1).

### Context

The _Crate_ JSON-LD MUST be valid according to [RO-Crate 1.1](https://w3id.org/ro/crate/1.1) and SHOULD use the RO-Crate 1.1 `@context` <https://w3id.org/ro/crate/1.1/context>

### Metadata File Descriptor

The [Metadata File Descriptor](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html#ro-crate-metadata-file-descriptor) `conformsTo` SHOULD be an array that contains at least <https://w3id.org/ro/crate/1.1>.

## RELIANCE RO-Crate Description

A RELIANCE RO-Crate MAY  include at least one Data Cube Data Entity, which MUST have the following properties:

- @type: MUST be ***DataCubeCollection*** or ***DataCubeProduct***.
- @id: MUST be either a URI Path relative to the RO Crate root, or an absolute URI, which can point to a file with the data cube or to a Web service call that allows generating the data cube on demand.

### DataCube Data Description

A DataCube Data Entity MAY include the following properties:

- @contentLocation: MUST be the id of a Contextual Entity of type Place.
- @temporalCoverage: MUST be a temporal range specified as a period (e.g., 2011/2013).

A DataCube Data Entity MUST include the following properties:

- @reliance:spatialCoverage: MUST be the id of a Contextual Entity that identifies the spatial coverage in detail, including rel:extent (expressed as a WKT text), rel:spatial-step-resolution and rel:coordinate-reference-system.
- @reliance:temporalCoverage: MUST be the id of a Contextual Entity that identifies the temporal coverage in detail, including rel:beginningTime (expressed as ISO8601), rel:endTime (expressed as ISO8601), rel:temporal-step-resolution and rel:temporal-reference-system-unit.  

A DataCube Entity MAY include the following property:

- @verticalCoverage: MUST be the id of a Contextual Entity that identifies the vertical coverage in detail, including rel:highestValue, rel:lowestValue, rel:vertical-step-resolution and rel:vertical-reference-system-unit.

A DataCube Data Entity SHOULD include the properties:

- sch:name
- sch:description
- sch:keywords (already discussed in the general layer for RO-Crate)
- sch:contentSize  
- sch:encodingFormat
- sch:contactPoint

A DataCube Data Entity MAY include the properties:

- reliance:product-type
- reliance:product-version
- reliance:data-type
- reliance:data-type-unit
- reliance:processing-level
- reliance:processor
- reliance:instrument
- reliance:platform
- reliance:other-data-acquisition-system
- reliance:dataquality
- reliance:maxValue
- reliance:minValue
- reliance:maxDate
- reliance:minDate
- reliance:noDataValue
- reliance:links-to-resources

### Software Description

In what relates to the software description, the following will be included as a Data Entity. A RELIANCE RO-Crate MAY include one or more Software Data Entities, which MUST have the following properties:

- @type: MUST be Software.
- @id: MUST be either a URI Path relative to the RO Crate root, or an absolute URI, which can point to a file with the software, to a DOI with the software or to a Web address of the repository of the software.

A Software Data Entity SHOULD include the following properties (besides the Data Cube Entity properties):

- sch:name
- sch:description
- sch:license
- sch:softwareVersion
- sch:author
- sch:codeRepository
- cm:referencePublication

A Software Data Entity MAY include the following properties:

- cm:buildInstructions
- sch:programmingLanguage
- sch:runtimePlatform
- sch:downloadURL
- sch:operatingSystem
- sch:memoryRequirements
- sch:preocessorRequirements
- sch:publisher
- cm:readme

### Versioning Research Objects Description

A RELIANCE RO-Crate MAY include the following properties (from the RO-Evo ontology):

- roevo:archivedAtTime, which represents the release date of the Research Object.
- roevo:snapshotedAtTime, which represents the snapshot date of the Research Object.
- eop:status, which MUST have any of the following values: liveRO, forkedRO, snapshotRO or archivedRO.
- roevo:wasArchivedBy, which MUST point to a Contextual Entity of type Person.
- roevo:wasSnapshotedBy, which MUST point to a Contextual Entity of type Person.

Other properties from the RO-Evo ontology MAY be also included, following that ontology.


### ro-crate-metadata.json Example

This is a minimal example of  a _Reliance DataCube RO-Crate_.

```json
{
  "@context": "https://w3id.org/ro/crate/1.1/context",
  "@graph": [
    {
      "@id": "ro-crate-metadata.json",
      "@type": "CreativeWork",
      "about": {
        "@id": "./"
      },
      "conformsTo": [
        { "@id": "https://w3id.org/ro/crate/1.1"},
        { "@id": "https://w3id.org/workflowhub/workflow-ro-crate/1.0"}
      ]
    },
    {
      "@id": "ro-crate-preview.html",
      "@type": "CreativeWork",
      "about": {
        "@id": "./"
      }
    },
    {
      "@id": "./",
      "@type": "Dataset",
      "name": "Example Workflow",
      "description": "An example workflow RO-Crate",
      "license": "Apache-2.0",
      "mainEntity": {
        "@id": "example_workflow.cwl"
      },
      "hasPart": [
        {
          "@id": "example_workflow.cwl"
        },
        {
          "@id": "diagram.svg"
        },
        {
          "@id": "README.md"
        }
      ]
    },
    {
      "@id": "example_workflow.cwl",
      "@type": [
        "File",
        "SoftwareSourceCode",
        "HowTo"
      ],
      "programmingLanguage": {
        "@id": "https://w3id.org/workflowhub/workflow-ro-crate#cwl"
      },
      "name": "Example Workflow",
      "image": {
        "@id": "diagram.svg"
      }
    },
    {
      "@id": "diagram.svg",
      "name": "Example Workflow Diagram",
      "@type": [
        "File",
        "ImageObject"
      ]
    },
    {
      "@id": "README.md",
      "@type": "File",
      "about": "./",
      "encodingFormat": "text/markdown"
    },
    {
      "@id": "https://w3id.org/workflowhub/workflow-ro-crate#cwl",
      "@type": "ComputerLanguage",
      "name": "Common Workflow Language",
      "alternateName": "CWL",
      "identifier": "https://w3id.org/cwl/v1.2/",
      "url": "https://www.commonwl.org/"
    }
  ]
}
```
<!---
```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/RELIANCE-EOSC/reliance-ro-crate/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.-->
