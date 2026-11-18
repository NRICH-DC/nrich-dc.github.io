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
determine whether they are accessioned into a collection, and
subsequently, to determine priority for downstream actions such as conservation
or digitisation. 
- **Metadata** focuses on metadata creation to go alongside the digitised artefact.
This includes descriptive information about the underlying artefect and
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

Note that some fields specifically refer to attributes of the artefacts being digitised which are inherited by the digital assets, while others are unique to the digital assets. This distinction does not apply to born-digital materials, of course. This specification avoids making a distinction between the actual artefacts and more abstract bibliographic entities such as [Works and Manifestations](https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frbr/frbr.pdf) which apply to specific types of material. Since the specification provides for linking to native metadata, this information can still be exposed and explored if required.

### Standard

- Organisations will usually keep metadata or documentation in native formats depending on their internal systems or needs. If these records are available online they MUST be linked in the metadata using *related* or *source*
- Standardised formats, controlled vocabularies or authoritative references SHOULD be used in preference to plaintext where this is indicated in parentheses.
- If a [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) entry exists for a person, organisation or place it SHOULD be used in preference to other authoritative sources. While Wikidata is not the authoritative source for information on these entities itself, it links to multiple such sources and can be a valuable disambiguation tool.
- It can be useful to see how metadata (catalogues) have changed when they are updated. Keeping historical metadata records and making them available online is OPTIONAL. 

**Metadata about the artefact**

| **DC**  | **Notes** | 
| :--- | :--- |
| dc:title<br>dc:description<br>dc:type ([DCMI Type Vocabulary](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-7))<br>dc:identifier<br>dc:creator<br>dc:contributor<br>dcterms:created ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF) | These MUST always be present<br><br>*related* links to originators native metadata record(s) for artefact<br><br>*created* is the creation date of the artefact |
| dc:subject ([LCSH](https://www.loc.gov/aba/publications/FreeLCSH/freelcsh.html))<br>dcterms:spatial ([ISO 6709](https://en.wikipedia.org/wiki/ISO_6709), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html))<br>dcterms:temporal ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF)<br>dc:language* ([RFC3066](http://www.ietf.org/rfc/rfc3066.txt)/[ISO 639](http://www.oasis-open.org/cover/iso639a.html))<br>dc:medium<br>dcterms:provenance (URL) | *subject* is OPTIONAL<br><br>**Maps MUST specify *spatial* coverage<br><br>Text bearing materials MUST specify *language*<br><br>*provenance* links to selection documentation where it exists at an organisational or item level: accession details or appraisal |

**Metadata about digital asset**

| **DC**  | **Notes** |
| :--- | :--- |
| dc:source (URL)<br>dcterms:references (IIIF URL)<br>dcterms:license<br>dcterms:rightsHolder (OrgID or ISNI)<br>dc:format ([MIME Type](http://www.iana.org/assignments/media-types/))<br>dc:identifier (PID, local identifiers)<br>dc:publisher ([ROR](https://ror.org/))<br>dcterms:issued ([ISO8601](https://www.iso.org/standard/70908.html) including EDTF) | These MUST always be present<br><br>*source* links to originators native metadata record(s) for digital object<br><br>*references* links to IIIF manifest of digital object<br><br>*issued* is the publication date of the digital resource |

### Mappings 
The Dublin Core fields can be mapped to equivalent fields in other interoperability standards. This specification allows for the use of the Europeana Data Model and LinkedArt as alternative publishing formats. These are more expressive models which can permit a more nuanced expression of object metadata (see OPTIONAL Event Metadata below). Whichever standards is chosen, they MUST be serialised as [RDF/XML](https://www.w3.org/TR/rdf-syntax-grammar/) or JSON-LD for harvesting.


**Spectrum mapping**

| **Standard level** | **Metadata type** | **Dublin Core** | **Spectrum mapping** | **Notes** |
| --- | --- | --- | --- | --- |
| Baseline | Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | [Title](https://collectionstrust.org.uk/resource/title/)<br> If no formal title, then:<br>[Object name](https://collectionstrust.org.uk/resource/object-name/)<br> - [Object name type](https://collectionstrust.org.uk/resource/object-name-type/)  | In Spectrum, Object name has a sub field of Object name type which should be used to denote if it is a simple name, specific or taxonomic name. |
| Baseline | Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | [Object number](https://collectionstrust.org.uk/resource/object-number/) |  |
| Baseline | Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | [Brief description](https://collectionstrust.org.uk/resource/brief-description/) |  |
| Baseline | Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | [Object name](https://collectionstrust.org.uk/resource/object-name/)<br> - [Object name type](https://collectionstrust.org.uk/resource/object-name-type/) = object type | In Spectrum, Object name has a sub field of Object name type which should be used to denote if it is a simple name, specific or taxonomic name. For type, it should say ‘object type’. |
| Baseline | Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | [Object production person](https://collectionstrust.org.uk/resource/object-production-person/)<br>[Object production organisation](https://collectionstrust.org.uk/resource/object-production-organisation/)<br>[Object production people](https://collectionstrust.org.uk/resource/object-production-people/) | Spectrum breaks this down into people, organisation and person. There isn’t a generic creator. |
| Baseline | Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | [Associated person](https://collectionstrust.org.uk/resource/associated-person/)<br>[Associated organisation](https://collectionstrust.org.uk/resource/associated-organisation/)<br>[Associated people](https://collectionstrust.org.uk/resource/associated-people/)<br> - [Association type](https://collectionstrust.org.uk/resource/association-type/) | Spectrum breaks this down into people, organisation and person. There isn’t a generic creator.<br><br>Association type is used to define the type of association / contribution. |
| Baseline | Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | [Object production date](https://collectionstrust.org.uk/resource/object-production-date/) |  |
| Baseline | Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | [Object history note](https://collectionstrust.org.uk/resource/object-history-note/) |  |
| Baseline | Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | [Reproduction number](https://collectionstrust.org.uk/resource/reproduction-number/) | This doesn’t really exist in Spectrum. The closest would be Reproduction number, which would be a unique ID linked to the digital asset. However, that relates more directly to identifier below. So perhaps this is a gap? |
| Baseline | Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | [Current reproduction location](https://collectionstrust.org.uk/resource/current-reproduction-location/) | Based on this being identified as the property that the IIIF manifest would be shared under. |
| Baseline | Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | [Rights out type](https://collectionstrust.org.uk/resource/rights-out-type/) |  |
| Baseline | Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | [Right holder – Person](https://collectionstrust.org.uk/resource/right-holder/)<br>[Right holder – Organisation](https://collectionstrust.org.uk/resource/right-holder/)<br>[Right holder - People](https://collectionstrust.org.uk/resource/right-holder/) |  |
| Baseline | Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | [Reproduction format](https://collectionstrust.org.uk/resource/reproduction-format/) |  |
| Baseline | Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | [Reproduction number](https://collectionstrust.org.uk/resource/reproduction-number/) |  |
| Baseline | Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | [Reproduction creator](https://collectionstrust.org.uk/resource/reproduction-creator/) |  |
| Baseline | Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | [Reproduction date](https://collectionstrust.org.uk/resource/reproduction-date/) |  |
| Extended | Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | [Associated concept](https://collectionstrust.org.uk/resource/associated-concept/) | Spectrum does not have a generic subject or keyword. Associated concept is what Museum Data Service has used to record subjects and keywords in museum metadata. |
| Extended | Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | [Associated place](https://collectionstrust.org.uk/resource/associated-place/)<br> - [Association type](https://collectionstrust.org.uk/resource/association-type/) | Association type would be used to define the type of relationship to place. |
| Extended | Artefact | [temporal](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/temporal/) | [Associated date](https://collectionstrust.org.uk/resource/associated-date/)<br> - [Association type](https://collectionstrust.org.uk/resource/association-type/) | Association type would be used to define the type of relationship to the date / period. |
| Extended | Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | [Content - language](https://collectionstrust.org.uk/resource/content-language/) | This is quite specific for printed material, so doesn’t sit very clearly within Spectrum but it can be done via content-language. |
| Extended | Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | [Material](https://collectionstrust.org.uk/resource/material/) |  |

**LinkedArt Mapping**

| **Standard level** | **Metadata type** | **Dublin Core** | **Linked Art** **mapping** | **Notes** |
| --- | --- | --- | --- | --- |
| Baseline | Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | Identified_by<br> - Type: “Name”<br> - Label: | The name or title of the artefact should be recorded under the label property |
| Baseline | Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | Identified_by<br> - Type: “Identifier”<br> - Label: | The identifier is specified in the label property |
| Baseline | Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | Referred_to_by<br> - Type: “LinguisticObject”<br>  - Classified_as<br>    - Type: "Description"<br> - Content:  | The description is recorded under the content property. |
| Baseline | Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | Classified_as<br> - Type<br>  -Type_of_work |  |
| Baseline | Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | Produced_by<br>- Type: “Production”<br>- Carried_out_by |  |
| Baseline | Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | Produced_by<br>- Type:<br>   - Carried_out_by | The type specifies the contribution |
| Baseline | Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | Produced_by<br> - Timespan |  |
| Baseline | Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | Type: “Activity”<br>- Type: “Provenance Activity” | LinkedArt has quite a structured approach to provenance, so under the activity type, defined as provenance activity, there are a range of other properties relating to timespan, acquisition, transfer of title, payment etc. |
| Baseline | Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | Type: “DigitalObject”<br>  - Access_point<br>    - ID<br>    - Type: “Digital object” | ID would be where a URL would be added |
| Baseline | Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | Subject_of<br> - Type: “LinguisticObject”<br> - Digitally_carried_by<br>  - Type: “DigitalObject”<br>  - Access_point<br>    - ID<br>    - Type: “Digital Object” | The ID is where the IIIF manifest would be added |
| Baseline | Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | Type: “VisualItem”<br> - Referred_to_by<br>  - Type: “LinguisticObject”<br>  - Classified_as<br>    - Label: Copyright/License Statement<br>  - Content: | Content would be used to specify the actual licence. |
| Baseline | Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | Type: “VisualItem”<br>- Subject_to<br>  - Type: “Right”<br>  - Classified_as<br>    - Label: [insert type of right]<br>  - Possessed_by<br>    - Label: [insert name of rights holder] | By using type of visual item, we are referring to a right of the visual, rather than the actual object.<br><br>The label of classified by specifies the type or right and the possessed by property allows you to give the name of the rights holder. |
| Baseline | Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | Type: “DigitalObject”<br>- format |  |
| Baseline | Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | Type: “DigitalObject”<br>- Identified_by<br>  - Type: “Identifier”<br>  - Content | The identifier will be recorded under content |
| Baseline | Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | Type: “DigitalObject”<br>- Created_by<br>- Type:<br> - Carried_out_by | Type could be ‘Creation’ or ‘Published’ with the person or organisation under ‘carried out by’. |
| Baseline | Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | Type: “DigitalObject”<br>- Created_by<br>- Type: “Creation”<br>- Timespan |  |
| Extended | Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | Type: “VisualItem”<br>- About |  |
| Extended | Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | Produced_by<br>- Type:<br> - Took_place_at | Type can be used to define to relationship to the spatial |
| Extended | Artefact | [temporal](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/temporal/) | Produced_by<br>- Type:<br> - timespan | Type can be used to define to relationship to the temporal |
| Extended | Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | Type: “LinguisticObject”<br>- Classified_as<br>  - Language |  |
| Extended | Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | Made_of<br>- Type: “Material”<br>- Label: | The actual material is recorded in label |

**Europeana Data Model Mapping**

| **Standard level** | **Metadata type** | **Dublin Core** | **European** **Data** **Model** **mapping** | **Notes** |
| --- | --- | --- | --- | --- |
| Baseline | Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | edm:ProvidedCHO<br>- dc:title |  |
| Baseline | Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | edm:ProvidedCHO<br>- dc:identifier |  |
| Baseline | Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | edm:ProvidedCHO<br>- dc:description |  |
| Baseline | Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | edm:ProvidedCHO<br>- dc:type |  |
| Baseline | Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | edm:ProvidedCHO<br>- dc:creator |  |
| Baseline | Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | edm:ProvidedCHO<br>- dc:contributor |  |
| Baseline | Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | edm:ProvidedCHO<br>- dc:created |  |
| Baseline | Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | edm:ProvidedCHO<br>- dc:provenance |  |
| Baseline | Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | edm:WebResource<br>- dc:source | A URL |
| Baseline | Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | edm:WebResource<br>- dcterms:isReferencedBy | Where a IIIF manifest would sit |
| Baseline | Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | edm:WebResource<br>- edm:rights | The EDM Rights  property is different to the dc:rights property below. The edm:rights property requires specific licences to be identified per digital asset / representation. |
| Baseline | Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | edm:WebResource<br>- dc:rights | The dc:rights property can be used for more generic rights statements or to identify rights holders. |
| Baseline | Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | edm:WebResource<br>- dc:format |  |
| Baseline | Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | edm:WebResource<br>- dc:identifer |  |
| Baseline | Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | edm:WebResource<br>- dc:publisher |  |
| Baseline | Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | edm:WebResource<br>- dcterms:issued |  |
| Extended | Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | edm:ProvidedCHO<br>- dc:subject |  |
| Extended | Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | edm:ProvidedCHO<br>- dcterms:spatial |  |
| Extended | Artefact | [temporal](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/temporal/) | edm:ProvidedCHO<br>- dcterms:temporal |  |
| Extended | Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | edm:ProvidedCHO<br>- dc:language |  |
| Extended | Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | edm:ProvidedCHO<br>- dc:format |  |

Note: for the EDM to connect the artefact and digital asset metadata, an aggregation class is needed with the following set of propertie

| **Metadata type** | **Dublin Core** | **EDM** | **Notes** |
| --- | --- | --- | --- |
| Extended | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | ore:aggregatedCHO | This is the identifier of the artefact |
| Extended | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | edm:isShownBy | This would be the same URL or IIIF manifest represented in either edm:WebResource, dc:source (URL) or edm:WebResource, dcterms:isReferencedBy (specifically for IIIF).  |
| Extended | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | edm:hasView | IF there is more than one digital asset, this is used to represent secondary views. |
| Extended | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | edm:dataProvider | The name of the data provider for the artefact. This doesn’t directly relate to the N-RICH data standard, but would be relevant if using the EDM as there would need to be an organisation ID on Europeana for any organisation using EDM. |
| Extended | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | edm:provider | If there is a third party, ie the Museum Data Service, then their Europeana organisation ID is noted here. |
| Extended | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | edm:rights |  |

**Other Mappings**

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


    


