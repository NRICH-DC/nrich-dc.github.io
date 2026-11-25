# N-RICH Digitisation Capabilities - Specifications
## Introduction
This specification in relation to standards and guidelines are the outcome of the N-RICH Digitisation Capabilities Pilot and target cultural heritage digitisation resulting in 2D image artefacts and the associated metadata. Taking inspiration from the IMPULSE Consortium’s  [Deliverable D3.4: Guidelines on simplification of metadata based on open standards]([https://zenodo.org/records/18301994)](https://zenodo.org/records/18301994)), the objective is to establish a “minimum viable set” of requirements that cohere existing standards and guidelines which should allow the construction of a federated research infrastructure.
### Audience
This document is intended primarily for those implementing N-RICH compatible infrastructure and tools.
### Overview
These recommendations will follow the conceptual workflow used in the Review of Standards and Guidelines.  This is deliberately not an expansive specification and the expectation is that this will extend over time as skills and technology evolve.

- **Selection** is concerned with identifying objects as in-scope (i.e. cultural heritage), then making a series of evaluation and selection decisions: to determine whether they are accessioned into a collection, and subsequently, to determine priority for downstream actions such as conservation or digitisation. 

- **Metadata** focuses on metadata creation to go alongside the digitised artefact. This includes descriptive information about the underlying artefect and technical information but, also links to related objects and rights related information.

- **Imaging** is largely a technical activity and thus amenable to setting and measuring quality standards.

- **Preservation** concerns the long-term availability of the digitised object (to avoid having to re-digitise). Often file formats suitable for preservation are not optimal for use by the public or researchers.

- **Access** needs to consider both human and machine consumption which requires both presentation systems and APIs. However, discovery and reliable referencing is also requirements.
## Levels of Compliance
The specification identifies 3 levels of compliance detailed below.

| Level | Requirements |
| --- | --- |
| Baseline | The "minumum viable set". This level of compliance is designed to support basic discovery. |
| Extended | Baseline elements with tighter data quality controls and additional contextual data. The level of compliance is designed to support interoperability. |
| Aspirational | Extended elements with the inclusion of more structured event-based data. This level of compliance is designed to produce contextually-rich collection as data. |
## Selection
### Specification
Organisational level documentation around selection should be considered as part of the contextual information and a form of paradata around a collection dataset that will help researchers better understand the data they are working with. 

Transparency around how and why selections decisions have been made is essential so that the researchers and the public can understand gap between what is available and what exists (or exist*ed*). This information is made available in the documents outlined in the table below. 

- When a document exists, it must be made available online.

- When collection or item level documentation exists, it should be linked in the *provenance* metadata for the objects to which they apply.

- When CARE (see below) considerations apply, they must be covered in an appropriate item or collection level appraisal document.

| **Compliance level** | **Metadata type** | **Property** | **Notes** |
| --- | --- | --- | --- |
| Baseline | Organisational | Collection Policy | As a baseline, this should be made available with collection level descriptions, and, where possible notes on the history of the collection. |
| Extended | Organisational | Digitisation Policy | As part of the extended standard, policies and decision-making processes around digitisation priorities should be made available. |
| Aspirational | Organisational | Significance documentation | Where possible, as part of the aspirational standard, reports and documentation on the significance of collections and their appraisals should be made available. This could include collections review documentation at a collection and/or individual artefact level. |
### Guidelines
The [UNESCO Recommendation Concerning the Preservation of, and Access to, Documentary Heritage Incl. Digital Form (2015)]([https://unesdoc.unesco.org/ark:/48223/pf0000244675.page=5)](https://unesdoc.unesco.org/ark:/48223/pf0000244675.page=5)) goes into considerable detail on good practice for selection processes and the accompanying documentation.

The [CARE Principles](https://www.gida-global.org/careprinciples) outline specific considerations for the treatment of indigenous (and other culturally sensitive) materials.
## Metadata
This section focuses on object metadata that is made available to researchers and the public through the N-RICH shared infrastructure. Metadata is structured rather than documentary information, and is thus more amenable to computation and automation. Cultural heritage materials are enormously diverse so the common attributes that can be used to construct generic interfaces for services such as discovery are somewhat limited. This specification is based on [Dublin Core]([https://www.dublincore.org/specifications/)](https://www.dublincore.org/specifications/)) Elements with some additions from the more specific DC Terms.

Note that some fields specifically refer to attributes of the artefacts being digitised which are inherited by the digital assets, while others are unique to the digital assets. This distinction does not apply to born-digital materials, of course. This specification avoids making a distinction between the artefacts and more abstract bibliographic entities such as [Works and Manifestations](https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frbr/frbr.pdf) which apply to specific types of material. Since the specification provides for linking to native metadata, this information can still be exposed and explored if required.
### Specification
- Organisations will usually keep metadata or documentation in native formats depending on their internal systems or needs. If these records are available online they must be linked in the metadata using *related* or *source.*

- If a [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) entry exists for a person, organisation or place it should be used in preference to other authoritative sources. While Wikidata is not the authoritative source for information on these entities itself, it links to multiple such sources and can be a valuable disambiguation tool.

- It can be useful to see how metadata (catalogues) have changed when they are updated. Keeping historical metadata records and making them available online is optional. 

#### Artefact metadata
The artefact metadata relates to the artefacts themselves, and aids discovery and interoperability between other items. The baseline standard here allows for some properties of artefacts to be described in a simple way, whilst the extended and aspiration standard require more structured and controlled approaches to recording the metadata.

| **Compliance level** | **Metadata type** | **Property** | **Notes** |
| :--- | --- | --- | --- |
| Baseline | Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | Short text identifying the artefact. It could be a formal title or less formal name. |
| Baseline | Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | A unique and persistent identifier, usually an accession number or code. |
| Baseline | Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | Longer more descriptive text to identify an artefact. |
| Baseline | Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | The type of artefact – for example, ‘vase’. |
| Baseline | Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | The name of the person, group of people or organisation that made the artefact. Anonymous or unknown is acceptable. |
| Baseline | Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | The name of the person, group of people or organisation that have contributed in some way to the artefact.  |
| Baseline | Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | The date or period the artefact was created. Unknown is acceptable. |
| Baseline | Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | Associated places or spatial coverage of the artefact. |
| Baseline | Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | The language of the artefact, or of any inscriptions on the artefact. |
| Baseline | Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | A simple keyword related to the artefact. |
| Extended | Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | At the extended level, it is expected that a creator will be authority controlled, ideally linked with an external identifier like a Wikidata ID or ISNI. |
| Extended | Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | As above for creator at the extended level. |
| Extended | Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | At an extended level, created should use the [ISO8601](https://www.iso.org/standard/70908.html) standard date format, or an open standard like [PeriodO](https://perio.do/en/) for historical time periods. |
| Extended | Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | At an extended level, spatial must use a standard format such as [ISO 6709](https://en.wikipedia.org/wiki/ISO_6709) for geospatial coordiantes, [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) for country codes, Getty’s [TGN](https://www.getty.edu/vow/TGNHierarchy?find=&place=&nation=&english=Y&subjectid=7029392), or a [GeoName](https://www.geonames.org/) or Wikidata ID. |
| Extended | Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | At an extended level, language must use of one the [ISO639](http://www.oasis-open.org/cover/iso639a.html) or [RFC3066](http://www.ietf.org/rfc/rfc3066.txt) identifiers or Wikidata ID. |
| Extended | Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | A material should be specified using a controlled authority, linking to a Wikidata ID. |
| Extended | Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | Provenance information can be provided in free text and give context around the history of an artefact. Provide URLs to any evidence. |
| Extended | Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | Subjects and keywording should be a controlled vocabulary, with that vocabulary specified. For example, the [Library of Congress Subject Headings](https://www.loc.gov/aba/publications/FreeLCSH/freelcsh.html) or the [Social History and Industrial Classification](https://shcg.org.uk/resource/shic/) system. |
| Aspirational | Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | At the aspirational level, provenance should be recorded using an event-based system, making use of people, persons, organisation, place and time related authority-controlled terms too. |
 
#### Digital asset metadata
The digital asset metadata relates to the images, documents, 3D and other media reproductions of the artefacts. The metadata standard here follows the same approach as the artefact metadata. Initially allowing, at baseline level, for key data to be recorded that allows linkage, with the extended and aspiration levels requiring more structured and technical metadata.

| **Compliance** **level** | **Metadata type** | **Property** | **Notes** |
| --- | --- | --- | --- |
| Baseline | Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | A link to the native metadata record the digital asset relates to (either the organisation that published the record or the aggregator that shared it). |
| Baseline | Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | URL links to the media or the digitised artefact. For example a IIIF manifest. |
| Baseline | Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | The licence the digital asset and metadata is being released under. Include a URL to the licence terms. |
| Baseline | Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | The name of the rights holder for the digital asset. |
| Baseline | Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | A description of the format of the digital asset |
| Baseline | Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | A unique and persistent identifier for the digital asset. |
| Baseline | Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | The name of the person or organisation publishing the digital asset. |
| Baseline | Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | The date the digital asset and metadata data were created. |
| Extended | Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | At the extended level, it is expected that a rightsHolder will be authority controlled, ideally linked with an external identifier like a Wikidata ID or [ISNI](https://isni.org/). |
| Extended | Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | At the extended level, format should be recorded using a standardised media format description, [MIME type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-7). |
| Extended | Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | At an extended level, the publisher should be using a [ROR ID](https://ror.org/) from the Research Organisation Registry or a Wikidata ID. |
| Extended | Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | At an extended level, issued should use the [ISO8601](https://www.iso.org/standard/70908.html) standard date format. |
### Mappings
The Dublin Core fields can be mapped to equivalent fields in other interoperability standards. This specification allows for the use of the Europeana Data Model and LinkedArt as alternative publishing formats. The inclusion of Spectrum is aimed at supporting the connection between the N-RICH specification and the standard used by the Museum Data Service, and many other individual museums. These are more expressive models which can permit a more nuanced expression of object metadata (see OPTIONAL Event Metadata below). Whichever standards is chosen, they MUST be serialised as [RDF/XML](https://www.w3.org/TR/rdf-syntax-grammar/) or JSON-LD for harvesting.
#### Spectrum mapping


| **Metadata type** | **Dublin Core** | **Spectrum mapping** | **Notes** |
| :---: | :---: | :---: | :---: |
| Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | [Title](https://collectionstrust.org.uk/resource/title/)<br> If no formal title, then:<br> [Object name](https://collectionstrust.org.uk/resource/object-name/)<br> - [Object name type](https://collectionstrust.org.uk/resource/object-name-type/) | In Spectrum, Object name has a sub field of Object name type which should be used to denote if it is a simple name, specific or taxonomic name. |
| Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | [Object number](https://collectionstrust.org.uk/resource/object-number/) |  |
| Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | [Brief description](https://collectionstrust.org.uk/resource/brief-description/) |  |
| Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | [Object name](https://collectionstrust.org.uk/resource/object-name/)<br> - [Object name type](https://collectionstrust.org.uk/resource/object-name-type/) = object type | In Spectrum, Object name has a sub field of Object name type which should be used to denote if it is a simple name, specific or taxonomic name. For type, it should say ‘object type’. |
| Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | [Object production person](https://collectionstrust.org.uk/resource/object-production-person/)<br> [Object production organisation](https://collectionstrust.org.uk/resource/object-production-organisation/)<br> [Object production people](https://collectionstrust.org.uk/resource/object-production-people/) | Spectrum breaks this down into people, organisation and person. There isn’t a generic creator. |
| Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | [Associated person](https://collectionstrust.org.uk/resource/associated-person/)<br> [Associated organisation](https://collectionstrust.org.uk/resource/associated-organisation/)<br> [Associated people](https://collectionstrust.org.uk/resource/associated-people/)<br> - [Association type](https://collectionstrust.org.uk/resource/association-type/) | Spectrum breaks this down into people, organisation and person. There isn’t a generic creator.<br><br>  Association type is used to define the type of association / contribution. |
| Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | [Object production date](https://collectionstrust.org.uk/resource/object-production-date/) |  |
| Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | [Associated concept](https://collectionstrust.org.uk/resource/associated-concept/) | Spectrum does not have a generic subject or keyword. Associated concept is what Museum Data Service has used to record subjects and keywords in museum metadata. |
| Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | [Associated place](https://collectionstrust.org.uk/resource/associated-place/) <br>- [Association type](https://collectionstrust.org.uk/resource/association-type/) | Association type would be used to define the type of relationship to place. |
| Artefact | [temporal](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/temporal/) | [Associated date](https://collectionstrust.org.uk/resource/associated-date/)<br> - [Association type](https://collectionstrust.org.uk/resource/association-type/) | Association type would be used to define the type of relationship to the date / period. |
| Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | [Content - language](https://collectionstrust.org.uk/resource/content-language/) | This is quite specific for printed material, so doesn’t sit very clearly within Spectrum but it can be done via content-language. |
| Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | [Material](https://collectionstrust.org.uk/resource/material/) |  |
| Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | [Object history note](https://collectionstrust.org.uk/resource/object-history-note/) |  |
| Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) |  | There is no direct Spectrum Unit of Information for this. The N-RICH specification requires a URL to the metadata record and that should be recorded here. |
| Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | [Current reproduction location](https://collectionstrust.org.uk/resource/current-reproduction-location/) | Based on this being identified as the property that the IIIF manifest would be shared under. |
| Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | [Rights out type](https://collectionstrust.org.uk/resource/rights-out-type/) |  |
| Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | [Right holder – Person](https://collectionstrust.org.uk/resource/right-holder/)<br> [Right holder – Organisation](https://collectionstrust.org.uk/resource/right-holder/)<br> [Right holder - People](https://collectionstrust.org.uk/resource/right-holder/) |  |
| Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | [Reproduction format](https://collectionstrust.org.uk/resource/reproduction-format/) |  |
| Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | [Reproduction number](https://collectionstrust.org.uk/resource/reproduction-number/) |  |
| Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | [Reproduction creator](https://collectionstrust.org.uk/resource/reproduction-creator/) |  |
| Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | [Reproduction date](https://collectionstrust.org.uk/resource/reproduction-date/) |  |
#### LinkedArt Mapping


| **Metadata type** | **Dublin Core** | **Linked Art mapping** | **Notes** |
| :---: | :---: | :---: | :---: |
| Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | Identified_by<br> - Type: “Name”<br> - Label: | The name or title of the artefact should be recorded under the label property |
| Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | Identified_by<br> - Type: “Identifier”<br> - Label: | The identifier is specified in the label property |
| Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | Referred_to_by<br> - Type: “LinguisticObject”<br> - Classified_as<br> - Type: "Description"<br> - Content: | The description is recorded under the content property. |
| Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | Classified_as<br> - Type<br> -Type_of_work |  |
| Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | Produced_by<br> - Type: “Production”<br> - Carried_out_by |  |
| Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | Produced_by<br> - Type:<br> - Carried_out_by | The type specifies the contribution |
| Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | Produced_by<br> - Timespan |  |
| Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | Type: “VisualItem”<br> - About |  |
| Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | Produced_by<br> - Type:<br> - Took_place_at | Type can be used to define to relationship to the spatial |
| Artefact | [temporal](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/temporal/) | Produced_by<br> - Type:<br> - timespan | Type can be used to define to relationship to the temporal |
| Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | Type: “LinguisticObject”<br> - Classified_as<br> - Language |  |
| Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | Made_of<br> - Type: “Material”<br> - Label: | The actual material is recorded in label |
| Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | Type: “Activity”<br> - Type: “Provenance Activity” | LinkedArt has quite a structured approach to provenance, so under the activity type, defined as provenance activity, there are a range of other properties relating to timespan, acquisition, transfer of title, payment etc. |
| Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | Type: “DigitalObject”<br> - Access_point<br> - ID<br> - Type: “Digital object” | ID would be where a URL would be added |
| Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | Subject_of<br> - Type: “LinguisticObject”<br> - Digitally_carried_by<br> - Type: “DigitalObject”<br> - Access_point<br> - ID<br> - Type: “Digital Object” | The ID is where the IIIF manifest would be added |
| Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | Type: “VisualItem”<br> - Referred_to_by<br> - Type: “LinguisticObject”<br> - Classified_as<br> - Label: "Copyright/License Statement"<br> - Content: | Content would be used to specify the actual licence. |
| Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | Type: “VisualItem”<br> - Subject_to<br> - Type: “Right”<br> - Classified_as<br> - Label: [insert type of right]<br> - Possessed_by<br> - Label: [insert name of rights holder] | By using type of visual item, we are referring to a right of the visual, rather than the actual object.  The label of classified by specifies the type or right and the possessed by property allows you to give the name of the rights holder. |
| Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | Type: “DigitalObject”<br> - format |  |
| Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | Type: “DigitalObject”<br> - Identified_by<br> - Type: “Identifier”<br> - Content | The identifier will be recorded under content |
| Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | Type: “DigitalObject”<br> - Created_by<br> - Type:<br> - Carried_out_by | Type could be ‘Creation’ or ‘Published’ with the person or organisation under ‘carried out by’. |
| Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | Type: “DigitalObject”<br> - Created_by<br> - Type: “Creation”<br> - Timespan |  |
#### Europeana Data Model Mapping


| **Metadata type** | **Dublin Core** | **European Data Model mapping** | **Notes** |
| :---: | :---: | :---: | :---: |
| Artefact | [title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/) | edm:ProvidedCHO<br> - dc:title |  |
| Artefact | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/identifier/) | edm:ProvidedCHO<br> - dc:identifier |  |
| Artefact | [description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/) | edm:ProvidedCHO<br> - dc:description |  |
| Artefact | [type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/type/) | edm:ProvidedCHO<br> - dc:type |  |
| Artefact | [creator](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/creator/) | edm:ProvidedCHO<br> - dc:creator |  |
| Artefact | [contributor](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/contributor/) | edm:ProvidedCHO<br> - dc:contributor |  |
| Artefact | [created](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/created/) | edm:ProvidedCHO<br> - dc:created |  |
| Artefact | [subject](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/subject/) | edm:ProvidedCHO<br> - dc:subject |  |
| Artefact | [spatial](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/spatial/) | edm:ProvidedCHO<br> - dcterms:spatial |  |
| Artefact | [temporal](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/temporal/) | edm:ProvidedCHO<br> - dcterms:temporal |  |
| Artefact | [language](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/language/) | edm:ProvidedCHO<br> - dc:language |  |
| Artefact | [medium](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/medium/) | edm:ProvidedCHO<br> - dc:format |  |
| Artefact | [provenance](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/provenance/) | edm:ProvidedCHO<br> - dc:provenance |  |
| Digital asset | [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | edm:WebResource<br> - dc:source | A URL |
| Digital asset | [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | edm:WebResource<br> - dcterms:isReferencedBy | Where a IIIF manifest would sit |
| Digital asset | [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | edm:WebResource<br> - edm:rights | The EDM Rights property is different to the dc:rights property below. The edm:rights property requires specific licences to be identified per digital asset / representation. |
| Digital asset | [rightsHolder](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/rightsHolder/) | edm:WebResource<br> - dc:rights | The dc:rights property can be used for more generic rights statements or to identify rights holders. |
| Digital asset | [format](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/format/) | edm:WebResource<br> - dc:format |  |
| Digital asset | [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | edm:WebResource<br> - dc:identifer |  |
| Digital asset | [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | edm:WebResource<br> - dc:publisher |  |
| Digital asset | [issued](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/issued/) | edm:WebResource - dcterms:issued |  |
<br>
Note: for the EDM to connect the artefact and digital asset metadata, an aggregation class is needed with the following set of propertie

| **Dublin Core** | **EDM** | **Notes** |
| --- | --- | --- |
| [identifier](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/identifier/) | ore:aggregatedCHO | This is the identifier of the artefact |
| [source](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/source/) | edm:isShownBy | This would be the same URL or IIIF manifest represented in either edm:WebResource, dc:source (URL) or edm:WebResource, dcterms:isReferencedBy (specifically for IIIF). |
| [references](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/references/) | edm:hasView | IF there is more than one digital asset, this is used to represent secondary views. |
| [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | edm:dataProvider | The name of the data provider for the artefact. This doesn’t directly relate to the N-RICH data standard, but would be relevant if using the EDM as there would need to be an organisation ID on Europeana for any organisation using EDM. |
| [publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/) | edm:provider | If there is a third party, ie the Museum Data Service, then their Europeana organisation ID is noted here. |
| [license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/) | edm:rights |  |

#### Other Mappings
Other useful mappings have already been published elsewhere, although they are much more detailed than required by this specification. 

- Europeana have published a [Mapping from MARC to EDM](https://pro.europeana.eu/files/Europeana_Professional/EuropeanaTech/EuropeanaTech_taskforces/Mapping_Refinement_Extension/Case_studies/Polymath/Mapping%20EDM%20explanations.doc).

- Archives Portal Europe have published a [Mapping from ISAD(G) to EDM](https://www.archivesportaleurope.net/uploads/files/2023_ISAD(G)2EDM.pdf).
### 
### Event-based Metadata
The aspirational level of the N-RICH specification proposes the use of event-based metadata structure to enable deep contextual information about artefacts to be recorded.

- EDM and LinkedArt both support an event based approach to metadata (LinkedArt uses the term "Activity"). Collection holders publishing metadata using these formats can include arbitrary additional event-based metadata. This mechanism allows the expression of complex narratives around digital objects covering history, provenance and cultural impact.   

- Events/activities must conform to the same requirements as other metadata:

  - Times/Dates must use [ISO8601](https://www.iso.org/standard/70908.html) with EDTF

  - Locations must use one of [ISO 6709](https://en.wikipedia.org/wiki/ISO_6709) (geospatial coordinates), [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) (country codes), a [GeoNames](https://www.geonames.org/) URL or a Wikidata URL referencing for a geopolitical entity.

  - People, persons and organisations must reference a recognised identity resource such as a Wikidata URL (as mentioned above) or an [ISNI](https://isni.org/) reference URL.  
### Guidelines
- Some objects might only be described at an aggregate level (e.g. boxes of material). This can be readily accommodated since a record can link to multiple digitised objects (*references*).

- Some objects, may not be able to be made available online for GDPR, CARE sensitivity or other cultural or legal reasons. It is still possible to publish a useful metadata record that records the existence of the object and document how it can be accessed. In this case there may be no *references* in the metadata record. This can also apply to undigitised items.

  - Resources such [Early Modern Letters Online](https://emlo.bodleian.ox.ac.uk/) demonstrate the significant research value of a suitably structured metadata catalogue even in the absence of digitised surrogates.

- Converting from plaintext metadata in the *baseline* to the controlled vocabularies and authorities required by *extended* compliance is a non-trivial task. While improving metadata *at source* is an aspirational goal, there is a need for retrospective conversion. Reconciliation and some AI tools can be used to partially automate such as transition.

## Imaging
This section focuses on minimum quality guidelines for 2D imaging materials. While it is possible to go into considerable detail on quality standards, many organisations will lack the technical capacity to conform to, or verify compliance, with such standards, rendering them moot.
### Specification 


| **Compliance level** | **Imaging property** | **Specification** **notes** |
| --- | --- | --- |
| Baseline | Colour | 24-bit colour (8-bits per colour channel). |
| Baseline | Resolution | Minimum of 4.5 megapixels. |
| Baseline | Resolution | Material between A5 and A3 in size to be captured at a minimum of 300 DPI, giving images between 4.5 and 17.5 megapixels. |
| Baseline | Resolution | Smaller objects must be imaged at an appropriately higher resolution to give a similar final image size, e.g.: 6x4 inch photographs at a minimum of 600 DPI or 35mm transparencies at a minimum 4000 DPI. |
| Baseline | Resolution | PPI requirement? |
| Baseline | Composition | Images must be captured against a neutral background |
| Baseline | Composition | The artefact must occupy at least 90% of the image in at least one direction.This allows for long-thin objects to be sufficiently captured. |
| Baseline | Tiling | If a single image cannot capture an object in its entirety, there must be sufficient overlap between adjacent images (>10%) to allow images to be stitched together programatically. |
| Baseline | Format | Images must be captured in a lossless format such as JPEG2000. |
| Extended | Colour | The [Enumerated sRGB](https://webstore.iec.ch/en/publication/6169) colourspace profile should be used. |
| Extended | Colour | A daylight wite balance (5000-6000k colour temperature) should be aimed for. |
| Extended | Resolution | Documents imaged on film, images should correspond to resolution equivalent to at least 300 DPI for the original document. |
| Extended | Resolution | Objects with levels of detail SHOULD be imaged at a higher resolution sufficient to capture the detail. |
| Aspirational | Colour | Microfilm and other monochrome materials may be captured in 8-bit grayscale using the Enumerated greyscale colourspace profile. |
### Guidelines
These specifications are based on the National Archives’ “[Guidance on techniques for digitising documents and other materials](https://cdn.nationalarchives.gov.uk/documents/information-management/digitisation-at-the-national-archives.pdf)” which provide a good balance of detail vs practicality. The  Guidance document not only defines quality standards but provides useful guidance for a complete digitisation workflow, including handling guidance, metadata, and code recipes to create conformant [JPEG 2000](https://www.iso.org/standard/87632.html) files and validate them.
## 
## Preservation
The specification leverages existing digital preservation practice and certification rather than creating additional requirements.
### Specification


| **Compliance level** | **Preservation area** | **Notes** |
| --- | --- | --- |
| Baseline |  | Preservation is not a baseline requirement |
| Extended | Storage | Materials should be archived in a [CoreTrustSeal](https://www.coretrustseal.org/) certified repository or service. |
| Extended | Format | Digitised material SHOULD be archived in a format that is suitable for long-term preservation. For 2D imaged materials, [TIFF](https://www.iso.org/standard/34342.html) or uncompressed JPEG2000 are acceptable formats. |
| Extended | Metadata | Metadata should be stored alongside image data in the native format used by the originating organisation. |
| Aspirational | Metadata | Archive additional versions of the metadata formatted for compliance with N-RICH |
### Guidelines
The [Digital Preservation Handbook](https://www.dpconline.org/handbook) is a good introduction to digital preservation theory and practice. 
## 
## Access
### Specification


| **Compliance level** | **Access area** | **Notes** |
| --- | --- | --- |
| Baseline | Organisational documentation | N-RICH compliant documentation such as selection policies MUST use one of the following file formats:<br>- PDF/A: Specifically, PDF/A-1 ([ISO 19005-1](https://www.iso.org/standard/38920.html)) or PDF/A-2 ([ISO 19005-2](https://www.iso.org/standard/50655.html))<br> - [UTF-8 plaintext](https://www.w3schools.com/charsets/ref_html_utf8.asp)<br> - [Markdown](https://www.markdownguide.org/)<br> - [TeX](https://en.wikipedia.org/wiki/TeX) |
| Baseline | Metadata | Metadata (whether Dublin Core, EDM or LinkedArt) MUST be published using one of the following Linked-Data file formats:<br>- [RDF-XML](https://www.w3.org/TR/rdf12-xml/)<br>- [JSON-LD](https://json-ld.org/) |
| Baseline | Images | Digital assets and artefact metadata must be referenceable and accessible via persistent identifiers. |
| Baseline | Images | Digitised images must be made available via an [International Image Interoperability Framework](https://iiif.io) V2.1+ image service at compliance level 1 or greater.<br><br> IIIF services can operate over both JPEG2000 and TIFF images, so are compatible with preservation recommendations. |
| Baseline | Images | Digitised artefacts must be described online by a IIIF V2.1+ presentation API manifest.<br><br>When the URL to the IIIF manifest is invoked, it should return the manifest loaded into a IIIF viewer. The URL to the IIIF manifest must be linked in the *references* element of the object metadata. |
| Extended | Metadata | Metadata SHOULD be available for harvest via [OAI-PMH](https://www.openarchives.org/pmh/) |
| Extended | Images | [ARK](https://arks.org/) or [DataCite DOI](https://datacite.org/) persistent identifiers should be used since they have provision for resolver services that can handle movement of objects between providers. |
| Aspirational | Metadata | Collection holders can harvest metadata back from the N-RICH Infrastructure via OAI-PMH to take advantage of enrichments made by researchers and other third parties, incorporating the additional information into their collection management or cataloguing systems. |

