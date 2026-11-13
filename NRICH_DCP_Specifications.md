# N-RICH Digitisation Capabilities - Specifications

## Introduction

These standards and guidelines are the outcome of the N-RICH Digitisation
Capabilities Pilot and target cultural heritage digitisation resulting in 2D
image artefacts and the associated metadata. Taking inspiration from the IMPULSE
Consortium’s  [Deliverable D3.4: Guidelines on simplification of metadata based
on open standards](https://zenodo.org/records/18301994), the objective is to
establish a “minimum viable set” of standards and guidelines which should allow
the construction of a federated research infrastructure.

### Audience
This document is intended primarily for those implementing N-RICH compatible infrastructure and tools.

### Terminology

The key words *MUST*, *MUST NOT*, *REQUIRED*, *SHOULD*, *SHOULD NOT*,
*RECOMMENDED*, and *OPTIONAL* in this document are to be interpreted as
described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

For a more discursive expression of the standards, please see the [Explanatory Notes](NRICH_DCP_SpecEx.md)

### Overview

These recommendations will follow the conceptual workflow used
in the Review of Standards and Guidelines.  This is deliberately not an
expansive specification and the expectation is that this will extend over time
as skills and technology evolve.

- **Selection** is concerned with identifying objects as in-scope (i.e. cultural
heritage), then making a series of evaluation and selection decisions: to
determine whether they are accessioned into a physical collection, and
subsequently, to determine priority for downstream actions such as conservation
or digitisation. 
- **Metadata** focuses on metadata creation to go alongside the digitised artefact.
This includes descriptive information about the underlying physical artefect and
technical information but, also links to related objects and rights related
information.
- **Imaging** is largely a technical activity and thus amenable to setting and
measuring quality standards.
- **Preservation** concerns the long-term availability of the digitised object
(to avoid having to re-digitise). Often file formats suitable for preservation
are not optimal for use by the public or researchers.
- **Access** needs to consider both human and machine consumption which requires both
presentation systems and APIs. However, discovery and reliable referencing is
also requirements.

## Levels of Compliance

The specification identifies 3 levels of compliance which map to RFC 2119 terminology as detailed below.

| Level | Requirements |
| ----- | ----- |
| Baseline | The "minumum viable set". Elements identified by key words *MUST, MUST NOT* and *REQUIRED.* |
| Extended  | Baseline elements plus those identified by the key words *SHOULD*, *SHOULD NOT* and *RECOMMENDED.* |
| Aspirational | Extended elements plus those identified by the key word *OPTIONAL.* |

## Selection

### Standard

Transparency around how and why selections decisions have been made is essential
so that the researchers and the public can understand gap between what is
available and what exists (or exist*ed*). This information is made available in
the documents outlined in the table below. 
- When a document exists, it MUST be made available online.
- When collection or item level documentation exists, it MUST be linked in the *provenance* metadata for the objects to which they apply.
- When CARE (see below) considerations apply, they MUST be covered in an appropriate item or collection level appraisal document.

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

The [CARE Principles](https://www.gida-global.org/careprinciples) outline specific considerations for the treatment of indigenous (and other culturally sensitive) materials.

## Metadata

This section focuses on object metadata that is made available to researchers
and the public through the N-RICH shared infrastructure. Metadata is structured
rather than documentary information, and is thus more amenable to computation
and automation. Cultural heritage materials are enormously diverse so the common attributes
that can be used to construct generic interfaces for services such as discovery
are somewhat limited. This specification is based on [Dublin
Core](https://www.dublincore.org/specifications/) Elements with some additions
from the more specific DC Terms.

Note that some fields specifically refer to attributes of the physical object being digitised which are inherited by the digital object, while others are unique to the digital object. This distinction does not apply to born-digital materials, of course. This specification avoids making a distinction between the physical object and more abstract bibliographic entities such as [Works and Manifestations](https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frbr/frbr.pdf) which apply to specific types of material. Since the specification provides for linking to native metadata, this information can still be exposed and explored if required.

### Standard

- Organisations will usually keep metadata or documentation in native formats depending on their internal systems or needs. If these records are available online they MUST be linked in the metadata using *related* or *source*
- Standardised formats, controlled vocabularies or authoritative references SHOULD be used in preference to plaintext where this is indicated in parentheses.
- If a [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) entry exists for a person, organisation or place it SHOULD be used in preference to other authoritative sources. While Wikidata is not the authoritative source for information on these entities itself, it links to multiple such sources and can be a valuable disambiguation tool.
- It can be useful to see how metadata (catalogues) have changed when they are updated. Keeping historical metadata records and making them available online is OPTIONAL. 

**Metadata about the Physical Object**
| **DC**  | **Notes** | 
| :--- | :--- |
| dc:title<br>dc:description<br>dc:type ([DCMI Type Vocabulary](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-7))<br>dc:related (URL)<br>dc:creator<br>dc:contributor<br>dcterms:created ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF)<br>dcterms:provenance (URL) | These MUST always be present<br><br>*related* links to originators native metadata record(s) for physical object<br><br>*created* is the creation date of the physical object<br><br>*provenance* links to accession policy and/or accession details |
| dc:subject ([LCSH](https://www.loc.gov/aba/publications/FreeLCSH/freelcsh.html))<br>dcterms:spatial ([ISO 6709](https://en.wikipedia.org/wiki/ISO_6709), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html))<br>dcterms:temporal ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF)<br>dc:language* ([RFC3066](http://www.ietf.org/rfc/rfc3066.txt)/[ISO 639](http://www.oasis-open.org/cover/iso639a.html)) | *subject* is OPTIONAL<br><br>**Maps MUST specify *spatial* coverage<br><br>Text bearing materials MUST specify *language* |

**Metadata about Digital Object**
| **DC**  | **Notes** |
| :--- | :--- |
| dc:source (URL)<br>dcterms:references (IIIF URL)<br>dcterms:license<br>dcterms:rightsHolder (OrgID or ISNI)<br>dc:format ([MIME Type](http://www.iana.org/assignments/media-types/))<br>dc:identifier (PID, local identifiers)<br>dc:publisher ([ROR](https://ror.org/))<br>dcterms:issued ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF) | These MUST always be present<br><br>*source* links to originators native metadata record(s) for digital object<br><br>*references* links to IIIF manifest of digital object<br><br>*issued* is the publication date of the digital resource |

### Mappings 
**This section is work-in-progress**

The Dublin Core fields can be mapped to equivalent fields in other interoperability standards. This specification allows for the use of the Europeana Data Model and LinkedArt as alternative publishing formats. These are more expressive models which can permit a more nuanced expression of object metadata (see OPTIONAL Event Metadata below). Whichever standards is chosen, they MUST be serialised as [RDF/XML](https://www.w3.org/TR/rdf-syntax-grammar/) or JSON-LD for harvesting.

| **Dublin Core** | **Europeana** **Data Model** **(edm:WebResource)** | **LinkedArt** **(abbreviated)** | 
| --- | --- | --- | 
| dc:title | dc:title | identified_by:<br>  type: "Name" |
| dc:description | dc:description |referred_to_by:<br>  type: "LinguisticObject",<br>  classified_as:<br>    type: "Type",<br>    _label: "Description", |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

Other useful mappings have already been published elsewhere, although they are much more detailed than required by this specification. 
- Europeana have published a [Mapping from MARC to EDM](https://pro.europeana.eu/files/Europeana_Professional/EuropeanaTech/EuropeanaTech_taskforces/Mapping_Refinement_Extension/Case_studies/Polymath/Mapping%20EDM%20explanations.doc).
- Archives Portal Europe have published a [Mapping from ISAD(G) to EDM](https://www.archivesportaleurope.net/uploads/files/2023_ISAD(G)2EDM.pdf).

### OPTIONAL Event Metadata

- EDM and LinkedArt both support an event based approach to metadata (LinkedArt uses the term "Activity"). Collection holders publishing metadata using these formats can include arbitrary additional event-based metadata. This mechanism allows the expression of complex narratives around digital objects covering history, provenance and cultural impact.   
- Events/activities MUST conform to the same requirements as other metadata:
  - Times/Dates MUST use [ISO8601](https://www.iso.org/standard/70908.html) with EDTF
  - Locations MUST use one of [ISO 6709](https://en.wikipedia.org/wiki/ISO_6709) (geospatial coordinates), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) (country codes), a [GeoNames](https://www.geonames.org/) URL or a Wikidata URL referencing for a geopolitical entity.
  - Agents MUST reference a recognised identity resource such as a Wikidata URL (as mentioned above) or an [ISNI](https://isni.org/) reference URL.  

### Guidelines

- Some objects might only be described at an aggregate level (e.g. boxes of material). This can be readily accommodated since a record can link to multiple digitised objects (*references*).
- Some objects, may not be able to be made available online for GDPR, CARE sensitivity or other cultural or legal reasons. It is still possible to publish a useful metadata record that records the existence of the object and document how it can be accessed. In this case there may be no *references* in the metadata record. This can also apply to undigitised items.
  - Resources such [Early Modern Letters Online](https://emlo.bodleian.ox.ac.uk/) demonstrate the significant research value of a suitably structured metadata catalogue even in the absence of digitised surrogates.
- Converting from plaintext metadata in the *baseline* to the controlled vocabularies and authorities required by *extended* compliance is a non-trivial task. While improving metadata *at source* is an aspirational goal, there is a need for retrospective conversion. Reconciliation and some AI tools can be used to partially automate such as transition.

## Imaging

This section focuses on minimum quality guidelines for 2D imaging materials. While it is possible to go into considerable detail on quality standards, many organisations will lack the technical capacity to conform to, or
verify compliance, with such standards, rendering them moot.

### Standard

**Colour**
- Full colour materials MUST be captured in 24-bit colour (8-bit per colour, 16 Million colours), and SHOULD use the [Enumerated sRGB](https://webstore.iec.ch/en/publication/6169) colourspace profile.
- Microfilm and other monochrome materials may OPTIONALLY be captured in 8-bit grayscale using the Enumerated greyscale colourspace profile.
- Images SHOULD aim for daylight white balance (5000-6000K colour temperature)

**Resolution**
- Images MUST be a minimum of 4.5 migapixels. There is no maximum although very large images may be composed of smaller images tiled/stitched together/ 
- Material between A5 and A3 in size MUST be captured at a minimum of 300 DPI, giving images between 4.5 and 17.5 megapixels. 
- Smaller objects MUST be imaged at an appropriately higher resolution to give a similar final image size, e.g.:
  - 6x4 inch photographs at a minimum of 600 DPI
  - 35mm transparencies at a minimum 4000 DPI
- For documents imaged on film, images SHOULD correspond to resolution equivalent to at least 300 DPI for the original document
- For larger objects, correspondingly, lower resolution imaging is permissible.
- Objects with levels of detail SHOULD be imaged at a higher resolution sufficient to capture the detail.

**Composition**
- All images MUST have a sufficient clear border/margin to demonstrate to users that the entire item has been captured.
- The item MUST occupy at least 90% of the image in at least one direction. This allows for long-thin objects
- Images MUST be captured against a neutral background that makes this easily discernable.

**Tiling**
- If a single image cannot capture an object in its entirety, there MUST be sufficient overlap between adjacent images (>10%) to allow images to be stitched together programatically.

### Guidelines

These specifications are based on the National Archives’ “[Guidance on techniques for digitising documents and other materials](https://cdn.nationalarchives.gov.uk/documents/information-management/digitisation-at-the-national-archives.pdf)” which provide a good balance of detail vs practicality. The  Guidance document not only defines quality standards but provides useful guidance for a complete digitisation workflow, including handling guidance, metadata, and code recipes to create conformant [JPEG 2000](https://www.iso.org/standard/87632.html) files and validate them.

## Preservation

The specification leverages existing digital preservation practice and certification rather than creating additional requirements.

### Standard

- Materials SHOULD be archived in a [CoreTrustSeal](https://www.coretrustseal.org/) certified repository or service.
- Digitised material SHOULD be archived in a format that is suitable for long-term preservation. For 2D imaged materials, [TIFF](https://www.iso.org/standard/34342.html) or uncompressed JPEG2000 are acceptable formats.
- Metadata SHOULD be stored alongside image data in the native format used by the originating organisation.
- Archiving an additional version of the metadata formatted for compliance with N-RICH is OPTIONAL.

### Guidelines

The [Digital Preservation Handbook](https://www.dpconline.org/handbook) is a good introduction to digital preservation theory and practice. 

## Access

### Standard

**Documentaion**
- N-RICH compliant documentation such as selection policies MUST use one of the following file formats:
  - PDF/A: Specifically, PDF/A-1 ([ISO 19005-1](https://www.iso.org/standard/38920.html)) or PDF/A-2 ([ISO 19005-2](https://www.iso.org/standard/50655.html))
  - [UTF-8 plaintext](https://www.w3schools.com/charsets/ref_html_utf8.asp)
  - [Markdown](https://www.markdownguide.org/)
  - [TeX](https://en.wikipedia.org/wiki/TeX)
 
**Metadata**
- Metadata (whether Dublin Core, EDM or LinkedArt) MUST be published using one of the following Linked-Data file formats:
  - [RDF-XML](https://www.w3.org/TR/rdf12-xml/)
  - [JSON-LD](https://json-ld.org/)
- Metadata SHOULD be available for harvest via [OAI-PMH](https://www.openarchives.org/pmh/)
- Collection holders can OPTIONALLY harvest metadata back from the N-RICH Infrastructure via OAI-PMH to take advantage of enrichments made by researchers and other third parties, incorporating the additional information into their collection management or cataloguing systems.

**Images**
- Objects (both physical and digital) and their metadata MUST be referenceable and accessible via persistent identifiers.    - [ARK](https://arks.org/) or [DataCite DOI](https://datacite.org/) SHOULD be used since they have provision for resolver services that can handle movement of objects between providers.
- Digitised images MUST be made available via an [International Image Interoperability Framework](https://iiif.io) V2.1+ image service at compliance level 1 or greater. IIIF services can operate over both JPEG2000 and TIFF images, so are compatible with preservation recommendations.
- Digitised objects MUST be described online by a IIIF V2.1+ presentation API manifest.
- When the URL to the IIIF manifest is invoked, it MUST return the manifest loaded into a IIIF viewer.
- The URL to the IIIF manifest MUST be linked in the *references* element of the object metadata 


    


