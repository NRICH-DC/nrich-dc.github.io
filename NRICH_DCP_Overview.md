# N-RICH Digitisation Capabilities Prototype - Overview

## Objectives

N-RICH aims to create a national research infrastructure bringing together
digital (both digitised and born-digital) cultural heritage materials of all
kinds from a wide variety of collection holders. Some will have the in-house
infrastructure to make their materials available directly while others will
require varying levels of service provision in order to participate
meaningfully. This can be distilled down to several key objectives:

- Digital collections must be machine actionable and compute-ready

- Standards and guidelines must be widely adoptable by the majority of
collection holders

- Recommendations must target both researcher and public access use cases

- Recommendations must align with [UKRI Policy on Research Data](https://www.ukri.org/publications/uk-research-and-innovation-research-data-policy/ukri-research-data-policy/#section-responsibly-managing-and-sharing-data), in particular: 
  - [FAIR principles](https://www.go-fair.org/) require research data to be **Findable, Acessible, Interoperable** and **Reusable**.
  - [CARE Principles](https://www.gida-global.org/careprinciples) for Indigenous (and other culturally sensitive) materials requires consideration of **Collective Benefit, Authority to Control, Responsibility** and **Ethics**
  - A general principle of "as open as possible, and as closed as necessary"
  
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
