# N-RICH Digitisation Capabilities - Explanatory Notes

## Introduction

This document provides a discursive overview of the specifications. It includes 
more explanatory details than the formal specification, providing the reasoning 
behind decisions made in drafting the specifications.   

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

This is deliberately not an expansive specification and the expectation is that 
this will extend over time as skills and technology evolve.

### Audience

This document is intended primarily for collection holders digitising material
for inclusion in N-RICH. However, it is also of informative for those
implementing N-RICH infrastructure and tools.

### Overview

These recommendations will follow the conceptual digitisation workflow below. 

- **Selection** is concerned with identifying objects as in-scope (i.e. cultural heritage), then making a series of evaluation and selection decisions: to determine whether they are accessioned into a physical collection, and subsequently, to determine priority for downstream actions such as conservation or digitisation. 
- **Metadata** focuses on metadata creation to go alongside the digitised artefact. This includes descriptive information about the underlying physical artefect and technical information but, also links to related objects and rights related information.
- **Imaging** is largely a technical activity and thus amenable to setting and measuring quality standards.
- **Preservation** concerns the long-term availability of the digitised object (to avoid having to re-digitise). Often file formats suitable for preservation are not optimal for use by the public or researchers.
- **Access** needs to consider both human and machine consumption which requires both presentation systems and APIs. However, discovery and reliable referencing is also requirements.

## Levels of Compliance

The specification identifies 3 levels of compliance:

| Level | Description |
| ----- | ----- |
| Baseline | Describes to "minimum viable set". These requirements must be met in order for collections to be included in N-RICH Infrastructure. This is expected to be within reach for all collections although correct data formatting and machine accessibility may require the use of external services. |
| Extended | These requirements will improve the utility of collections included in N-RICH but many collections may require further work to achieve the required metadata detail. |
| Aspirational | These requirements encompass information that is not habitually recorded in the sector, but may be generated as an outcome of research activities or specific projects. Ingesting this additional information into catalogues and collection management systems would make it available **at source**. This would greatly enhance the basic discoverability and comprehensibility of cultural heritage materials, as well as increasing opportunities for advanced machine analytics. |

Conceptually, in terms of knowledge content, much of the meaning of an artefact is derived from information that is not intrinsic to the object itself. Its cultural significance instead comes largely from its original context, provenance, and interactions with people and culture over time. Correspondingly, a digital surrogate or born-digital object should be considered as a composite entity composed of multiple files that can be labelled as data, metadata, documentation or paradata but all of which contribute to overall meaning and understanding. 

The *aspirational* level recognises this, along with the fact the such information is not commonly generated as part of conventional collection management practice but rather from research or specific projects. Such information can be included in N-RICH by leveraging the event-based metadata capabilities of the Europeana Data Model or LinkArt standards. However, it would also be desirable for collection holders to be able to capture information from other sources (such as research conducted using N-RICH) to include in their metadata. The *aspirational* level thus also describes collections harvesting metadata back from N-RICH or other sources, recognising that this would require a significant changes in both institutional practice and catalogue/collection management systems.              

## FAIR Principles

The [FAIR principles](https://www.go-fair.org/) encapsulate researchers’ broad requirements with respect to data and has been adopted by UKRI. The specification makes the following provisions to meet these requirements:

**Findable** – Metadata specifications will:
- Allow the construction of a discovery service what will allow a researcher to find the object that they require
- Provide enough detail about the identity of the object to enable a researcher its authenticity and suitability for their needs
- Be sufficiently generic to apply across the wide variety cultural heritage objects, so that no specific materials are privileged in terms of discovery  

**Accessible** – The mechanisms for accessing both data (images) and metadata will:
- Be suitable for both human and machine consumption without undue technical or policy barriers
- Be compliant with [UKRI Policy on Research Data](https://www.ukri.org/publications/uk-research-and-innovation-research-data-policy/ukri-research-data-policy/#section-responsibly-managing-and-sharing-data): "As open as possible, and as closed as necessary"
  - Most importantly, metadata should be available under a license that is compliant with the policy   
- Provide a human- and machine-actionable mechanism to access more detailed information (e.g. collection specific metadata, source records etc.).

**Interoperable** – This specification identifies the following standards for interoperability between collections:
- [International Image Interoperability Framework (IIIF)](https://iiif.io) Version 2.1+, level 1+ for machine access to 2D images
  - IIIF is widely supported by both commercial and open-source image delivery platforms
  - IIIF supports a wide variety of image viewers that support advanced features such as zoom, pan and annotation overlays
  - IIIF supports complex objects such as books and newspapers, large objects displayed using tiled images such as maps and scrolls and alternate views to support features such as foldouts and two-page spreads
  - IIIF integrates with a wide variety of research tools such as Optical Character Recognition (OCR), Handwritten Text Recognition (HTR), crowdsourcing platforms such as Zooniverse, Web Annotation (by humans and machines) and image analytics (AI or otherwise)
- [OAI-PMH](https://www.openarchives.org/pmh/) is a simple mechanism for publishing metadata for harvesting by other services (e.g. N-RICH infrastructure)
- Metadata requirements can be met using several formats
  - [Dublin Core](https://www.dublincore.org/specifications/) is the simplest and most common metadata format but has limited expressiveness for information beyond the *baseline* requirements
  - The [Europeana Data Model](https://pro.europeana.eu/index.php/page/edm-documentation) is already used by a number of collections and systems to feed metadata into Europeana. It has a stronger cultural heritage focus and therefore can accommodate *extended* or *aspirational* metadata.
  - [LinkedART](https://linked.art/) is a subset of the [CIDOC-CRM](https://cidoc-crm.org/) developed by the [International Council of Museums](https://icom.museum/en/). While the CRM is very expansive and can be daunting to implementers, LinkedArt is rather simpler and aligns with the N-RICH infrastructure prototype requirements. It can also accommodate *extended* or *aspirational* metadata.
  - A mapping is also provided for [SPECTRUM](https://collectionstrust.org.uk/spectrum/) since it used within many museum collection management systems, although not as a metadata format *per se*. 
- [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) references are recommended for key entities such as people, groups, organisations, places and events. While Wikidata is not a canonical source for such entities, it links to many other resources and thus acts as a resolver for related entries these sources.     

**Reusable** – Data and metadata should available for researchers in the longer term for both new research and reproducibility purposes. The specification makes the following provisions: 
- To ensure that references and citations to research data continue to work, Persistent Identifiers (PIDs) must be used for each item. The specification recommends using [ARK](https://arks.org/) or [DataCite DOI](https://datacite.org/).
- Digital materials (both data and metadata) should be archived using a service that is [CoreTrustSeal](https://www.coretrustseal.org/) certified to ensure continued availability.   
- As metadata can be updated over time, previous versions should also be archived supported to ensure referential integrity over the longer term. The OAI-PMH protocol allows for the publication of updates to previously harvested records.

## CARE Principles

The [CARE Principles](https://www.gida-global.org/careprinciples) outline specific considerations for the treatment of indigenous (and other culturally sensitive) materials. This may affect how both digital and physical materials are handled and made available and thus must be accounted for.

**Collective Benefit** 
- Data ecosystems shall be designed and function in ways that enable Indigenous Peoples to derive benefit from the data.
- 
**Authority to Control**
- Indigenous Peoples’ rights and interests in Indigenous data must be recognised and their authority to control such data be empowered. Indigenous data governance enables Indigenous Peoples and governing bodies to determine how Indigenous Peoples, as well as Indigenous lands, territories, resources, knowledges and geographical indicators, are represented and identified within data.

**Responsibility**
- Those working with Indigenous data have a responsibility to share how those data are used to support Indigenous Peoples’ self-determination and collective benefit. Accountability requires meaningful and openly available evidence of these efforts and the benefits accruing to Indigenous Peoples

**Ethics**
- Indigenous Peoples’ rights and wellbeing should be the primary concern at all stages of the data life cycle and across the data ecosystem.

The CARE Principles come to the fore when making selection decisions and through the crafting of metadata that reflects indigenous concerns. When CARE considerations are a factor, these must be addressed in an object or collection level appraisal of the item and released as part of the object metadata. The use of Wikidata to map between indigenous and conventional representations of place, events and peoples can also be useful in this context.   

## Selection

### Standard

Transparency around how and why selection decisions have been made is essential so that the researchers and the public can understand gap between what is available digitally, and what actually exists (or exist*ed*). The specification identifies key three selection events about which documentary information can be required. These may be high level policies or, for specific projects or cases, more descriptive documents. Accession polices are relatively common in the museum and archival communities since they are required for various certification processes. They are less ubiquitous in libraries. Each may be published at an organisational, collection or item level. Item level documentation is typically only required for special one-off acquisitions or similar special cases. 

- **Accession** Document why and how collections and/or items are acquired
- **Digitisation** Document why and how material is selected for digitisation
- **Appraisal** Document why an item/collection is considered culturally significant, at risk and/or unique. This may include CARE considerations if applicable.  

**Baseline**
- Organisational accession documentation (almost always a policy) must be published
- If collection or item level documents exist
  - They must be published
  - They must be referenced in the metadata of the objects to which they apply    

**Extended**
- Baseline requirements plus...
- Accession documentation must be published for all collections
- Digitisation documentation must be published at either an organisational or collection/project level  

**Aspirational**
- Extended requirements plus...
- Appraisal documentation must be available at collection or item level

### Guidelines

The [UNESCO Recommendation Concerning the Preservation of, and Access to,
Documentary Heritage Incl. Digital Form
(2015)](https://unesdoc.unesco.org/ark:/48223/pf0000244675.page=5) goes into
considerable detail on good practice for selection processes and the
accompanying documentation.

The [CARE Principles](https://www.gida-global.org/careprinciples) outline specific considerations for the treatment of indigenous (and other culturally sensitive) materials.

## Metadata

This section focuses on object metadata that is made available to researchers and the public through the N-RICH shared infrastructure. Metadata is structured rather than documentary information, and is thus more amenable to computation and automation.

Organisations are likely to keep additional metadata or documentation information depending on curatorial capabilities or their internal process needs. This specification avoids making a distinction between the physical object and more abstract bibliographic entities such as [Works and Manifestations](https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frbr/frbr.pdf) which apply to specific types of material. If required, the ability to link to more detailed metadata allows these types of relationships to be exposed.

Cultural heritage materials are enormously diverse so the common attributes that can be used to construct generic interfaces for services such as discovery is somewhat limited. The baseline specification is based on [Dublin Core](https://www.dublincore.org/specifications/) Elements with some additions from the more specific DC Terms.  Note that some fields specifically refer to attributes of the physical object being digitised which are inherited by the digital object, while others are unique to the digital object.

### Standard

Items marked with an asterisk may occur more than once in a metadata record. The specification allows metadata to be expressed in one of three formats: Dublin Core, Europeana Data Model (EDM) and LinkedArt to give collection holders flexibility when publishing their data. Each of the three formats are expressible as [Linked-Data](https://www.w3.org/DesignIssues/LinkedData) which allows data from multiple sources to be integrated into complex "knowledge graphs" that open the way to a variety of discovery, navigation and analytical approaches. *Baseline* and *extended* requirements can be accommodated within all three formats but *aspirational* requirements make use of advanced event-based features that only EDM and LinkedArt support. Since the specification addresses digitised materials, there is a distinction between metadata relating to the physical objects and its digital surrogate, which would obviously not apply to a born-digital object.    

**Baseline**
- Required metadata about the Physical Object
  - *title*: Short text identifying the object as uniquely as possible 
  - *description*: Longer more descriptive text
  - *type*: an indication of the type of physical object being described (e.g. statue)
  - *related\**: URL link(s) to the native metadata record(s) for the physical object, if they exist, May also link to appraisal documentation if it exists. 
  - *creator\**: name of person, group or organisation who created the object ("anonymous" or "unknown" are acceptable values)
  - *contributor\**: name of person, group or organisation who contributed indirectly to the creation of the object. May be omitted if not relevant. 
  - *created*: the date that the object was created, expressing any uncertainty 
  - *provenance*: URL link to accession documentation
  - *spatial coverage*: geographical area to which the object refers (only required for maps or similar objects) 
  - *language\**: languages and/or scripts used (only required for text-bearing objects) 
- Required metadata about the Digital Object
  - *source\**: URL links to native metadata record(s) for digital object, if they exist. May also link to digitisation documentation if it exists.
  - *references\**: URL link(s) to digitised object(s) if available
  - *license\**: license for the digitised object and its associated metadata record, which must be compliant with UKRI research data policy as described above
  - *rights holder*: name of the owner of the rights to the digitised object
  - *format*: description of file format of the digitised object
  - *identifer\*: one or more persistent identifiers for the object, and any local identifiers  
  - *publisher*: name of the organisation originally publishing the metadata record and digitised object
  - *issued*: date that the metadata record and digtised object were published

**Extended**
- Baseline requirements plus the following qualifications...
- Required metadata about the Physical Object
  - *creator\**: must reference a recognised identity resource such as a Wikidata URL (as mentioned above) or an [ISNI](https://isni.org/) reference URL  
  - *contributor\**: as with *creator*
  - *created*: must use [ISO8601](https://www.iso.org/standard/70908.html) standard date format but can use Extended Date-Time Format (EDTF) to express uncertainty
  - *spatial coverage*: must use one of [ISO 6709](https://en.wikipedia.org/wiki/ISO_6709) (geospatial coordinates), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) (country codes), a [GeoNames](https://www.geonames.org/) URL or a Wikidata URL referencing for a geopolitical entity.
  - *language\**: must use one of [RFC3066](http://www.ietf.org/rfc/rfc3066.txt)/[ISO 639](http://www.oasis-open.org/cover/iso639a.html) language identifers
  - *subject\**: one or more keywords that help describe the object
- Required metadata about the Digital Object
  -  *rights holder*: as with *creator*
  -  *format*: must use [MIME Type](http://www.iana.org/assignments/media-types/)
  -  *publisher*: must use [Research ORganisation](https://ror.org/) identifier 
  -  *issued*: as with *created*

**Aspirational**
- Extended requirements plus...
- Previous version of metadata records should continue to be made available (although not necessarily in N-RICH), so researchers can understand how descriptions have changed over time
- Rich contextual and provenance metadata. Both EDM and LinkedArt support an event based approach to metadata (LinkedArt uses the term "Activity"). An event is typically located at a particular time and place, involves one or more agents (the people, places, organisations involved in the event) and results in a change to the object involved. The change may be terms of meaning, understanding or cultural relevance as much as anything physical. This mechanism allows the capture of complex narratives around digital objects.
- Events/activities must conform to the same requirements as other metadata:
  - Times/Dates should use [ISO8601](https://www.iso.org/standard/70908.html) with EDTF
  - Locations should use one of [ISO 6709](https://en.wikipedia.org/wiki/ISO_6709) (geospatial coordinates), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) (country codes), a [GeoNames](https://www.geonames.org/) URL or a Wikidata URL referencing for a geopolitical entity.
  - Agents should use must reference a recognised identity resource such as a Wikidata URL (as mentioned above) or an [ISNI](https://isni.org/) reference URL       

### Guidelines

- Some objects might only be described at an aggregate level (e.g. boxes of material). This can be readily accommodated since a record can link to multiple digitised objects (*references*).
- Some objects, may not be able to be made available online for GDPR, CARE sensitivity or other cultural or legal reasons. It is still possible to publish a useful metadata record that records the existence of the object and document how it can be accessed. In this case there may be no *references* in the metadata record. This can also apply to undigitised items.
  - Resources such [Early Modern Letters Online](https://emlo.bodleian.ox.ac.uk/) demonstrate the significant research value of a suitably structured metadata catalogue even in the absence of digitised surrogates.
- Converting from plaintext metadata in the *baseline* to the controlled vocabularies and authorities required by *extended* compliance is a non-trivial task. While improving metadata *at source* is an aspirational goal, there is a need for retrospective conversion. Reconciliation and some AI tools can be used to partially automate such as transition.

## Imaging

This section focuses on minimum quality guidelines for 2D imaging materials. While it is possible to go into considerable detail on quality standards, many organisations will lack the technical capacity to conform to, or verify compliance, with such standards, rendering them moot.

### Standard

**Baseline**
- The specification aims for a complete image of an object to be a minimum of 4.5 megapixels in resolution. This is within the reach of almost all digital and phone cameras currently available. A typical image is more likely to be 10-18 meagpixels. For comparison, a typical monitor is around 2-4 megapixels so it allows a modest amount of zooming in for more detail.
- For objects with high levels of detail, it makes sense to capture more detailed images, perhaps using image stitching software or in-camera panorama features to combine multiple images. IIIF viewers provide the ability to zoom and pan across larger images automatically.
- Colour objects should be captured using 24-bit colour (8-bits per colour channel) which is standard for most cameras.
- Monochrome sources such as microfilm may be captured using 8-bit greyscale.
- Objects must span at least 90% of the final image in one direction (to allow for long, thin objects) but they should not extend right to the edge of the image so viewers can be sure that no part of the object is cut off.
- Objects should be photographed against a uniform, neutral background that contrasts with the object so that its edges can be clearly identified.

**Extended**
- Baseline requirements plus...
- Objects can, of course, be imaged at higher resolutions than baseline requirements if resources permit. They are, however, made available online in the same way as lower resolution images.

**Aspirational**
- Extended requirements plus...
- More advanced techniques such as hyperspectral imaging are very specific to particular projects and must be published as separate digital objects alongside conventional imaging. 
- Such objects should be accompanied by digitisation selection documentation detailing why the techniques in question were chosen.      

### Guidelines

These specifications are based on the National Archives’ “[Guidance on techniques for digitising documents and other materials](https://cdn.nationalarchives.gov.uk/documents/information-management/digitisation-at-the-national-archives.pdf)” which provide a good balance of detail vs practicality. The  Guidance document not only defines quality standards but provides useful guidance for a complete digitisation workflow, including handling guidance, metadata, and code recipes to create conformant [JPEG 2000](https://www.iso.org/standard/87632.html) files and validate them.

## Preservation

The specification leverages existing digital preservation practice and certification rather than creating additional requirements. 

### Standard

**Baseline**
- Preservation is not a *baseline* requirement

**Extended**
- Materials must be archived in a [CoreTrustSeal](https://www.coretrustseal.org/) certified repository or service.
- Digitised material must be archived in a format that is suitable for long-term preservation. For 2D imaged materials, [TIFF](https://www.iso.org/standard/34342.html) or uncompressed JPEG2000 are acceptable formats.
- Metadata must be stored alongside image data in the native format used by the originating organisation.

**Aspirational**
- Extended requirements plus...
- Archiving an additional version of the metadata formatted for compliance with N-RICH.

### Guidelines

The [Digital Preservation Handbook](https://www.dpconline.org/handbook) is a good introduction to digital preservation theory and practice. 

## Access

### Standard

**Baseline**
- N-RICH compliant documentation such as selection policies MUST use one of the following file formats:
  - PDF/A: Specifically, PDF/A-1 ([ISO 19005-1](https://www.iso.org/standard/38920.html)) or PDF/A-2 ([ISO 19005-2](https://www.iso.org/standard/50655.html))
  - [UTF-8 plaintext](https://www.w3schools.com/charsets/ref_html_utf8.asp)
  - [Markdown](https://www.markdownguide.org/)
  - [TeX](https://en.wikipedia.org/wiki/TeX)
- Metadata (whether Dubline Core, EDM or LinkedArt) should be published using one of the following Linked-Data file formats:
  - [RDF-XML](https://www.w3.org/TR/rdf12-xml/)
  - [JSON-LD](https://json-ld.org/)
- Objects (both physical and digital) and their metadata MUST be referenceable and accessible via persistent identifiers. 
- Digitised images must be made available via an [International Image Interoperability Framework](https://iiif.io) V2.1+ image service at compliance level 1 or greater. IIIF provides access to a rich set of presentation tools for public and scholarly access. IIIF services can operate over both JPEG2000 and TIFF images, so are compatible with preservation recommendations.
- Digitised objects should be described online by a IIIF V2.1+ presentation API manifest. When the URL to a digital object is invoked, it should return the manifest loaded into a IIIF viewer, although the choice of viewer is up to the collection holder. The manifest describes how to display and navigate between the multiple images that may comprise a complex object such as a book. The   

**Extended**
- Baseline requirements plus...
- [ARK](https://arks.org/) or [DataCite DOI](https://datacite.org/) persistent identifers must be used since they have provision for resolver services that can handle movement of objects between providers, enabling persistent references in the longer term.
- Metadata must be available for harvest via [OAI-PMH](https://www.openarchives.org/pmh/) which provides a mechanism for picking up just updated records, and collection-based filtering. 

**Aspirational**
- Extended requirements plus...
- Collection holders should harvest metadata back from the N-RICH Infrastructure via OAI-PMH to take advantage of enrichments made by researchers and other third parties, incorporating the additional information into their collection management or cataloguing systems.
