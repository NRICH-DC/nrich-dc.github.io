# N-RICH Digitisation Capabilities Prototype - Explanatory Notes

## Introduction

This document provides a verbal overview of the specifications. It includes 
more explanatory details than the formal specification, providing the reasoning 
behind decisions made in drafting the specifications, identifying where 
feedback from the community has been incorporated.   

These standards and guidelines are the outcome of the N-RICH Digitisation
Capabilities Pilot and target cultural heritage digitisation resulting in 2D
image artefacts and the associated metadata. Taking inspiration from the IMPULSE
Consortium’s  [Deliverable D3.4: Guidelines on simplification of metadata based
on open standards](https://zenodo.org/records/18301994), the objective is to
establish a “minimum viable set” of standards and guidelines which should allow
the construction of a federated research infrastructure.

This “minimum viable set” tries to balance useful interoperability and practical
implementability for a wide range of organisation, and include extensibility 
to cover expansions in scope. To avoid reinventing the wheel, existing widely 
used approaches are chosen where possible. Many standards overlap, and where a
choice has been made, it favours simplicity and flexibility for the pragmatic 
reason that such standards are easier to validate and map to other approaches.

### Audience
This document is intended primarily for collection holders digitising material
for inclusion in N-RICH. However, it is also of informative for those
implementing N-RICH infrastructure and tools.

### Overview

These recommendations will follow the conceptual workflow used
in the [Review of Standards and Guidelines](link required).  This is deliberately not an
expansive specification and the expectation is that this will extend over time
as skills and technology evolve.

- **Selection** is concerned with identifying objects as in-scope (i.e. cultural heritage), then making a series of evaluation and selection decisions: to determine whether they are accessioned into a physical collection, and subsequently, to determine priority for downstream actions such as conservation or digitisation. 
- **Metadata** focuses on metadata creation to go alongside the digitised artefact. This includes descriptive information about the underlying physical artefect and technical information but, also links to related objects and rights related information.
- **Imaging** is largely a technical activity and thus amenable to setting and measuring quality standards.
- **Preservation** concerns the long-term availability of the digitised object (to avoid having to re-digitise). Often file formats suitable for preservation are not optimal for use by the public or researchers.
- **Access** needs to consider both human and machine consumption which requires both presentation systems and APIs. However, discovery and reliable referencing is also requirements.

## FAIR Principles

The [FAIR principles](https://www.go-fair.org/) encapsulate researchers’ broad requirements with respect to data and has been adopted by UKRI. The specification makes the following provisions to meet these requirements:

- **Findable** – Metadata specifications will:
  - Allow the construction of a discovery service what will allow a researcher to find the object that they require
  - Provide enough detail about the identity of the object to enable a researcher its authenticity and suitability for their needs
  - Be sufficiently generic to apply across the wide variety cultural heritage objects, so that no specific materials are privileged in terms of discovery  

- **Accessible** – The mechanisms for accessing both data (images) and metadata will:
  - Be suitable for both human and machine consumption without undue technical or policy barriers
  - Be compliant with [UKRI Policy on Research Data](https://www.ukri.org/publications/uk-research-and-innovation-research-data-policy/ukri-research-data-policy/#section-responsibly-managing-and-sharing-data): "As open as possible, and as closed as necessary"
    - Most importantly, metadata should be available under a license that is compliant with the policy   
  - Provide a human- and machine-actionable mechanism to access more detailed information (e.g. collection specific metadata, source records etc.).

- **Interoperable** – This specification identifies the following standards for interoperability between collections:
  - [International Image Interoperability Framework (IIIF)](https://iiif.io) Version 2.1+, level 1+ for machine access to 2D images
    - IIIF is widely supported by both commercial and open-source image delivery platforms
    - IIIF supports a wide variety of image viewers that support advanced features such as zoom, pan and annotation overlays
    - IIIF supports complex objects such as books and newspapers, large objects displayed using tiled images such as maps and scrolls and alternate views to support features such as foldouts and two-page spreads
    - IIIF integrates with a wide variety of research tools such as Optical Character Recognition (OCR), Handwritten Text Recognition (HTR), crowdsourcing platforms such as Zooniverse, Web Annotation (by humans and machines) and image analytics (AI or otherwise)
  - OAI-PMH for harvesting of metadata
  - Metadata requirements can be met using several formats
    - Dublin CORE is the simplest and most common metadata format but has limited expressiveness for information beyond the *baseline* requirements
    - Europeana Data Model already used by a number of collections and systems to feed metadata into Europeana. It has a stronger cultural heritage focus and therefore can accommodate *extended* or *aspirational* metadata.
    - LinkedART is a subset of the CIDOC-CRM (developed by the International Council of Museums). While the CRM is very expansive and can be daunting to implementers, LinkedARt is rather simpler and aligns with the N-RICH infrastructure prototype requirements. It can also accommodate *extended* or *aspirational* metadata.
    - A mapping is also provided for SPECTRUM since it used within many museum collection management systems, although not as a metadata transfer format. 
  - Wikidata references are recommended for key entities such as peoples, organisations, places and events since Wikidata acts as a resolver for related entries in many other sources     

- **Reusable** – Data and metadata should available for researchers in the longer term for both new research and reproducibility purposes. The specification 
  - To ensure that references and citations to research data continue to work, Persistent Identifiers (PIDs) should be used for each item. Data DOIs and ARKs
  - Digital materials (both data and metadata) should be archived in a certified archiving service. The specification recommends  
  - As metadata can be updated over time, versioning should also be supported to ensure referential integrity over the longer term.

## CARE Principles

The [CARE Principles](https://www.gida-global.org/careprinciples) outlines specific considerations for the treatment of indigenous (and other culturally sensitive) materials. This may affect how both digital and physical materials are handled and made available and thus must be accounted for may be a consideration outline consideration of **Collective Benefit, Authority to Control, Responsibility** and **Ethics**

## Levels of Compliance

The specification identifies 3 levels of compliance:

| Level | Description |
| ----- | ----- |
| Baseline | These requirements must be met in order for collections to be included in N-RICH Infrastructure. This is expected to be within reach for all collections although correct data formatting and machine accessibility may require the use of external services. |
| Extended | These requirements will improve the utility of collections included in N-RICH but many collections may require further work to achieve the required metadata detail. |
| Aspirational | These requirements encompass information that is not habitually recorded in the sector, but may be generated as an outcome of research activities or specific projects. Ingesting this additional information into catalogues and collection management systems would make it available **at source**. This would greatly enhance the basic discoverability and comprehensibility of cultural heritage materials, as well as increasing opportunities for advanced machine analytics. |

## Selection

### Standard

Transparency around how and why selection decisions have been made is essential
so that the researchers and the public can understand gap between what is
available digitally, and what actually exists (or exist*ed*). This information 
is made available in the documents outlined in the table below. When a document 
exists, it MUST be made available online, and, for collection or item level 
documentation, MUST be linked in the metadata for the objects to which they apply.

| Document  | Requirements |
| ----- | ----- |
| Collection/Accession Policy<br> – why and how collections and/or items are acquired | MUST be published at organisation level<br>SHOULD be published at a collection level<br>OPTIONAL at item level (for special acquisitions) |
| Digitisation Policy<br> – why and how material is selected for digitisation | SHOULD be published at organisation level<br>SHOULD be published at a collection/project level<br>OPTIONAL at item level (for special acquisitions) |
| Appraisal/Evaluation Document<br> - why is an item/collection considered culturally significant, at risk and/or unique | OPTIONAL at a collection level<br>OPTIONAL at item level (for special acquisitions) |

### Guidelines

The [UNESCO Recommendation Concerning the Preservation of, and Access to,
Documentary Heritage Incl. Digital Form
(2015)](https://unesdoc.unesco.org/ark:/48223/pf0000244675.page=5) goes into
considerable detail on good practice for selection processes and the
accompanying documentation.

## Metadata

This section focuses on object metadata that is made available to researchers
and the public through the N-RICH shared infrastructure. Metadata is structured
rather than documentary information, and is thus more amenable to computation
and automation. Conceptually, in terms of information content, a digital object
should be considered as a composite entity composed of multiple data streams
that can be labelled as data, metadata, documentation or paradata but all of
which contribute to overall meaning and understanding.

Organisations are likely to keep additional metadata or documentation
information depending on curatorial capabilities or their internal process
needs. Where such additional information exists online, it SHOULD be linked in
the metadata for the objects to which it applies.

### Core Metadata

Cultural heritage materials are enormously diverse so the common attributes
that can be used to construct generic interfaces for services such as discovery
is somewhat limited. This specification is based on [Dublin
Core](https://www.dublincore.org/specifications/) Elements with some additions
from the more specific DC Terms. Standardised formats or controlled vocabularies
SHOULD be used in preference to plaintext where this is indicated in
parentheses. Note that some fields specifically refer to attributes of the
physical object being digitised which are inherited by the digital object, while
others are unique to the digital object.

This specification avoids making a distinction between the physical object and
more abstract bibliographic entities such as [Works and
Manifestations](https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frbr/frbr.pdf) which apply to specific types of material. If
required, the ability to link to more detailed metadata allows these types of
relationships to be exposed.

#### Metadata about the Physical Object

| **DC**  | **Notes** | 
| :--- | :--- |
| dc:title<br>dc:description<br>dc:type ([DCMI Type Vocabulary](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-7))<br>dc:related (URL)<br>dc:creator<br>dc:contributor<br>dcterms:created ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF)<br>dcterms:provenance (URL) | These MUST always be present<br><br>*related* links to originators native metadata record(s) for physical object<br><br>*created* is the creation date of the physical object<br><br>*provenance* links to accession policy and/or accession details |
| dc:subject ([LCSH](https://www.loc.gov/aba/publications/FreeLCSH/freelcsh.html))<br>dcterms:spatial ([ISO 6709](https://en.wikipedia.org/wiki/ISO_6709), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html))<br>dcterms:temporal ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF)<br>dc:language* ([RFC3066](http://www.ietf.org/rfc/rfc3066.txt)/[ISO 639](http://www.oasis-open.org/cover/iso639a.html)) | *subject* is OPTIONAL<br><br>**Maps MUST specify *spatial* coverage<br><br>Text bearing materials MUST specify *language* |

#### Metadata about Digital Object

| **DC**  | **Notes** |
| :--- | :--- |
| dc:source (URL)<br>dcterms:references (IIIF URL)<br>dcterms:license<br>dcterms:rightsHolder (OrgID or ISNI)<br>dc:format ([MIME Type](http://www.iana.org/assignments/media-types/))<br>dc:identifier (PID, local identifiers)<br>dc:publisher ([ROR](https://ror.org/))<br>dcterms:issued ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF) | These MUST always be present<br><br>*source* links to originators native metadata record(s) for digital object<br><br>*references* links to IIIF manifest of digital object<br><br>*issued* is the publication date of the digital resource |

### Mappings 
**This section is work-in-progress**

The Dublin Core fields can be mapped to equivalent fields in other
interoperability standards, such as the Europeana Data Model and LinkedArt.
These are more expressive models which may permit a more nuanced expression of
object metadata. Whichever standards is chosen, they MUST be serialised as
[RDF/XML](https://www.w3.org/TR/rdf-syntax-grammar/) or JSON-LD for harvesting.

| **Dublin Core** | **Europeana** **Data Model** **(edm:WebResource)** | **LinkedArt** **(abbreviated)** | 
| --- | --- | --- | 
| dc:title | dc:title | identified_by:<br>  type: "Name" |
| dc:description | dc:description |referred_to_by:<br>  type: "LinguisticObject",<br>  classified_as:<br>    type: "Type",<br>    _label: "Description", |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

### WikiData

Amongst other functions,
[Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) provides useful
resource for the identification and disambiguation of people and places. While
it is not the authoritative source for information on these entities, it links
to multiple sources which are. Therefore, for person and named place references,
metadata SHOULD use links to WikiData references rather than specific sources,
where they exist.

### Multiple objects

Some objects might only be described
at an aggregate level (e.g. boxes of material). This can be accommodated since
there is not requirement that a record must link to a single IIIF object. There
can be multiple *dc:references* links in a record.

### Metadata-only objects

Some objects, for various reasons, may not be available online, but can still
publish a useful metadata record that records the existence of the object and
mechanisms for access. This can apply to both undigitised items and items that
cannot be made available for legal or other reasons. Resources such [Early
Modern Letters Online](https://emlo.bodleian.ox.ac.uk/) demonstrate the
significant research value of a suitably structured catalogue even in the
absence of digitised surrogates.

### Notes

It is expected that organisations will be able to accommodate the required
metadata within the systems and schemas that they already use. Formats are
discussed for informational purposes but the emphasis is on ensuring the
relevant data exists – mapping can be used to convert to suitable consumption
forms when the need arises. However, the use of authorities and reference
ontologies at source *is* strongly encouraged - these are discussed in more
detail in the Access section.

## Imaging

This section focuses on minimum quality guidelines for 2D imaging
materials. While it is possible to go into considerable detail on quality
standards, many organisations will lack the technical capacity to conform to, or
verify compliance, with such standards, rendering them moot.

### Minimum Imaging Quality Standards

These are based on the National Archives’ “[Guidance on techniques for digitising documents and other materials](https://cdn.nationalarchives.gov.uk/documents/information-management/digitisation-at-the-national-archives.pdf)” which provide a good balance of
detail vs practicality.

- Full colour materials MUST be captured in 24-bit colour, and SHOULD use the
[Enumerated sRGB](https://webstore.iec.ch/en/publication/6169) colourspace
profile

- Microfilm and other monochrome material may OPTIONALLY be captured in  8-bit
grayscale using the Enumerated greyscale colourspace profile

- Material between A5 and A3 in size MUST be captured at a minimum of 300 DPI,
giving images between 4.5 and 17.5 megapixels

- Smaller objects MUST be imaged at an appropriately higher resolution to give a
similar final image size, e.g.:

  - 6x4 inch photographs at a minimum of 600 DPI

  - 35mm transparencies at a minimum 4000 DPI

- For documents imaged on film, images SHOULD correspond to resolution
equivalent to at least 300 DPI for the original document

- For larger objects, correspondingly, lower resolution imaging is permissible
although high levels of detail in a large object may warrant higher resolution
imaging.

- All images MUST have a sufficient clear border/margin to demonstrate to users
that the entire item has been captured. Images MUST be captured against a
neutral background that makes this easily discernable.

- If a single image cannot capture an object in its entirety, there MUST be
sufficient overlap between adjacent images (>10%) to allow images to be stitched
together programatically.

### Recommended Reading
The National Archives’ Guidance document not only defines quality standards but
provides useful guidance for a complete digitisation workflow, including
handling guidance, metadata, and code recipes to create conformant [JPEG
2000](https://www.iso.org/standard/87632.html) files and validate them.

## Preservation
The specification leverages existing digital preservation practice
and certification rather than creating additional requirements.

- Materials SHOULD be archived in a
[CoreTrustSeal](https://www.coretrustseal.org/) certified repository or service.

- Digitised material SHOULD be archived in a format that is suitable for
long-term preservation. For 2D imaged materials,
[TIFF](https://www.iso.org/standard/34342.html) or uncompressed JPEG2000 are
acceptable formats.

- Metadata SHOULD be stored alongside image data in the native format used by
the originating organisation. Archiving an additional version of the metadata
formatted for compliance with N-RICH is OPTIONAL.

## Access

### Document Formats

N-RICH compliant documentation such as selection policies MUST use one of the
following file formats:

- PDF/A: Specifically, PDF/A-1 ([ISO
19005-1](https://www.iso.org/standard/38920.html)) or PDF/A-2 ([ISO
19005-2](https://www.iso.org/standard/50655.html))

- [UTF-8 plaintext](https://www.w3schools.com/charsets/ref_html_utf8.asp)

- [Markdown](https://www.markdownguide.org/)

- [TeX](https://en.wikipedia.org/wiki/TeX)

### Persistent Identifiers

Objects (both physical and digital) and their metadata MUST be referenceable and
accessible via persistent identifiers. [ARK](https://arks.org/) or [DataCite
DOI](https://datacite.org/) SHOULD be used since they have provision for
resolver services that can handle movement of objects between providers,
enabling persistent references in the longer term.

### Image Access

Digitised images MUST be made available via an [International Image
Interoperability Framework](https://iiif.io) service. IIIF also provides access
to a rich set of presentation tools for pubic and scholarly access. IIIF
services can operate over both JPEG2000 and TIFF images, so are compatible with
preservation recommendations.

### Metadata Access API

Metadata SHOULD be available for harvest via
[OAI-PMH](https://www.openarchives.org/pmh/) which provides a mechanism for
picking up just updated records, and collection-based filtering. Any additional
metadata SHOULD also be made available in its native form via the same
mechanism, signposted via *dc:*s*ource* or *dc:related* **links in the
metadata.

    


