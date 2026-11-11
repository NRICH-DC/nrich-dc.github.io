# N-RICH Digitisation Capabilities Prototype - Overview

## Overview

N-RICH aims to create a national research infrastructure bringing together
digital (both digitised and born-digital) cultural heritage materials of all
kinds from a wide variety of collection holders. Some will have the in-house
infrastructure to make their materials available directly while others will
require varying levels of service provision in order to participate
meaningfully. This can be distilled down to several key objectives:

- Digital collections should be machine actionable and compute-ready

- Standards and guidelines should be widely adoptable by the majority of
collection holders

- Recommendations should target both researcher and public access use cases

- [FAIR](https://www.go-fair.org/) is a reasonable encapsulation of researchers’
broad requirements with respect to data, namely:

  - **Findable** – metadata should be sufficient to allow the construction of a
discovery service what will allow a researcher to find the object that they
require, and provide enough detail about the identity of the object to verify
that its authenticity and suitability.

  - **Accessible** – data and metadata should be available for both human and
machine consumption without undue technical or policy barriers. The route to
more detailed information (e.g. collection specific metadata) should be clearly
signposted.

  - **Interoperable** – as much as possible, common ontologies, terminologies
and authorities should be used between collections. Mechanisms for access and
retrieval should be standardised for any particular type of material or data.

  - **Reusable** – data and metadata should be preserved for long term access,
and provide Persistent Identifiers (PIDs) to ensure ongoing citability. As
metadata can be updated over time, versioning should also be supported to ensure
referential integrity over the longer term.

## Scope

Bearing this in mind, it is not feasible for a cost-effective and scalable
infrastructure to meet all possible use cases. Therefore, the aim is to satisfy
the majority of common research and public engagement requirements and to
provide a “deep-dive" mechanism to reach collection specific data for
exceptions.

As a first step, these specifications are aimed primarily at materials that can 
be digitised by 2D scanning or imaging, such as manuscripts, maps, prints, 
drawings etc. Alongside the standards and guidelines themselves, the aim is 
to demonstrate a process which can be used to expand the recommendations to 
a broader range of cultural heritage materials in the longer term.

## Structure

These specifications are provided in three parts:

**Principles** Describes the difference between *standards* and *guidelines* and 
outlines the guiding principles used to design this specification. In particular,
it considers the drivers and disincentives to adoption and how these impact the 
final design.   

**Explanatory Notes** Provides a discursive, verbal description of the 
specification along with details about why certain design decisions were made.

**Specification** A formal version of the specification using language 
compatible with W3C standards. It references many existing standards and 
guidelines and only describes in detail the additions or qualifications that 
are needed by N-RICH.

## Further Development

Resource and time constrains mean that this specification cannot and does not 
cover the rich diversity of cultural heritage materials and metadata, focusing 
as it does on 2D imaging. However, the specifications have been drafted with 
these additional cases in mind and it is hoped that they will prove to be 
sufficiently flexible and extensible to accommodate them.

The [IIIF Presentation API V4.0](https://iiif.io/api/presentation/4.0/) adds 
support for a variety of 3D and time-based media (video and audio) formats so
the specification can support additional forms of digitisation.

EDM and LinkedArt have good support for event-based metadata that can be used 
to support performance-based and other intangible cultural heritage.   
