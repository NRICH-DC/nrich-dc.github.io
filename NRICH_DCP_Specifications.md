# N-RICH Digitisation Capabilities Prototype - Specifications

## Introduction

These standards and guidelines are the outcome of the N-RICH Digitisation
Capabilities Pilot and target cultural heritage digitisation resulting in 2D
image artefacts and the associated metadata. Taking inspiration from the IMPULSE
Consortium’s  [Deliverable D3.4: Guidelines on simplification of metadata based
on open standards](https://zenodo.org/records/18301994) the objective is to
stablish a “minimum viable set” of standards and guidelines which should allow
the construction of a federated research infrastructure.

This recommendation attempts to define a “minimum viable set” of standards and
guidelines that balances useful interoperability, practical implementability
for a wide range of organisation and extensibility to cover expansions in scope.
To avoid reinventing the wheel, existing widely used approaches are chosen
where possible. Many standards overlap, and where a choice has been made, it
favours simplicity and flexibility for the pragmatic reason that such standards
are easier to validate and map to other approaches.

### Audience
This document is intended primarily for collection holders digitising material
for inclusion in N-RICH. However, it is also of informative for those
implementing N-RICH infrastructure and tools.

### Terminology

The key words *MUST*, *MUST NOT*, *REQUIRED*, *SHOULD*, *SHOULD NOT*,
*RECOMMENDED*, and *OPTIONAL* in this document are to be interpreted as
described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

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

### Levels of Compliance

The specification identifies 3 levels of compliance:

| Level | Requirements |
| ----- | ----- |
| Level 0 | Elements identified by key words *MUST, MUST NOT* and *REQUIRED.* |
| Level 1 | Level 0 elements plus those identified by the key words *SHOULD*, *SHOULD NOT* and *RECOMMENDED.* |
| Level 2 | Level 1 elements plus those identified by the key word *OPTIONAL.* |

## Selection Documentation

Transparency around how and why selections decisions have been made is essential
so that the researchers and the public can understand gap between what is
available and what exists (or exist*ed*). This information is made available in
the documents outlined in the table below. When a document exists, it MUST be
made available online, and, for collection or item level documentation, MUST be
linked in the metadata for the objects to which they apply.

| Document  | Requirements |
| ----- | ----- |
| Collection/Accession Policy – why and how collections and/or items are acquired | MUST be published at organisation level<br>SHOULD be published at a collection level<br>OPTIONAL at item level (for special acquisitions) |
| Digitisation Policy – why and how material is selected for digitisation | SHOULD be published at organisation level
SHOULD be published at a collection/project level
OPTIONAL at item level (for special acquisitions) |
| Appraisal/Evaluation Document - why is an item/collection considered culturally significant, at risk and/or unique | OPTIONAL at a collection level
OPTIONAL at item level (for special acquisitions) |

### Recommended Reading
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
Manifestations](https://www.ifla.org/wp-content/uploads/2019/05/assets/
cataloguing/frbr/frbr.pdf) which apply to specific types of material. If
required, the ability to link to more detailed metadata allows these types of
relationships to be exposed.

#### Metadata about the Physical Object

| **DC**  | **Notes** | | :--- | :--- | | dc:titledc:descriptiondc:type ([DCMI
Type
Vocabulary](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/
#section-7))dc:related (URL)dc:creatordc:contributordcterms:created
([ISO8601](https://www.iso.org/standard/70908.html) including
EDTF)dcterms:provenance (URL) | These MUST always be present*related* links to
originators native metadata record(s) for physical object *created* is the
creation date of the physical object*provenance* links to accession policy
and/or accession details  | | dc:subject
([LCSH](https://www.loc.gov/aba/publications/FreeLCSH/freelcsh.html))dcterms:
spatial ([ISO 6709](https://en.wikipedia.org/wiki/ISO_6709), [ISO
3166](https://www.iso.org/iso-3166-country-codes.html))dcterms:temporal
([ISO8601](https://www.iso.org/standard/70908.html) including EDTF)dc:language*
([RFC3066](http://www.ietf.org/rfc/rfc3066.txt)/[ISO
639](http://www.oasis-open.org/cover/iso639a.html)) | *subject* is OPTIONAL
**Maps MUST specify *spatial* coverageText bearing materials MUST specify
*language* |

#### Metadata about Digital Object

| **DC**  | **Notes** | | :--- | :--- | | dc:source (URL)dcterms:references
(IIIF URL)dcterms:licensedcterms:rightsHolder (OrgID or ISNI)dc:format ([MIME
Type](http://www.iana.org/assignments/media-types/))dc:identifier (PID, local
identifiers)dc:publisher ([ROR](https://ror.org/))dcterms:issued
([ISO8601](https://www.iso.org/standard/70908.html) including EDTF) | These MUST
always be present*source* links to originators native metadata record(s) for
digital object *references* links to IIIF manifest of digital object*issued* is
the publication date of the digital resource |

### Mappings

The Dublin Core fields can be mapped to equivalent fields in other
interoperability standards, such as the Europeana Data Model and LinkedArt.
These are more expressive models which may permit a more nuanced expression of
object metadata. Whichever standards is chosen, they MUST be serialised as
[RDF/XML](https://www.w3.org/TR/rdf-syntax-grammar/) or JSON-LD for harvesting.

| **Dublin Core** | **Europeana** **Data Model** **(edm:WebResource)** |
**LinkedArt** **(abbreviated)** | | --- | --- | --- | | dc:title | dc:title |
identified_by:      type: "Name" | | dc:description | dc:description |
referred_to_by:       type: "LinguisticObject",      classified_as:
type: "Type",          _label: "Description", | |  |  |  | |  |  |  | |  |  |  |
|  |  |  | |  |  |  |

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

These are based on the National Archives’ “[Guidance on techniques for
digitising documents and other
materials](https://cdn.nationalarchives.gov.uk/documents/information-management/
digitisation-at-the-national-archives.pdf)” which provide a good balance of
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

    


