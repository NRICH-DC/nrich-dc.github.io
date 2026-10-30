# N-RICH Digitisation Capabilities Prototype - Design Principles

Most of the principles outlined here are not specific to the cultural heritage
domain, since they are derived primarily from simple cost-benefit considerations
for any organisation looking to adopting standards.

## Standards
- Standards should not be costly to implement:

  - Standards should be focussed on addressing a specific problem or
requirement. The business case for adopting such a standard can thus be
relatively simply constructed.

  - Expansive standards that attempt to solve multiple problems at once tend to
be less effective at meeting any of their requirements, more expensive to
implement and harder to justify unless an organisation has exactly the same
requirements that the standard was designed for.

  - Good standards should generally be accompanied by a complete reference
implementation to prove that the standard is implementable, and to act as a
second source of truth in the event of ambiguity.

  - Good standards should also be accompanied by a validation process to enable
implementers to verify compliance. If this cannot be easily accomplished then
the standard is likely to be insufficiently well specified.

- Standards should not be costly to maintain:

  - Standards concerning the long-term retention of materials should evolve
slowly and thoughtfully with consideration given to backwards compatibility so
that material does not have to be frequently reworked to maintain compliance.

  - At the same time, standards do need to accommodate developments in the wider
world, especially with respect to software and hardware tools. Otherwise,
standards can become an obsolescence and/or security risk in their own right.

  - When standards do evolve in a manner that breaks backwards compatibility, a
migration route should be designed (and implemented, to prove it works).

  - Standards need to accompanied by ongoing support, documentation and training
to ensure the necessary workplace skills continue to exist.

- Standards should deliver both short- and long-term benefits

  - A good driver for standards adoption is the availability of tools based on
the standards that deliver value to the organisation. This is a more likely
outcome if the standard is easy to implement. For example, the rapid adoption of
IIIF is partly attributable to the availability of both complete software
implementations and “shim” code that enabled existing platforms to be compliant.

  - Workforce familiarity as a result of effective training and documentation
can help to drive standards adoption, but is equally an organisational benefit
if it ensures that a longer term workforce skills base is developed so that
maintenance and staffing is less of an issue.

  - Interoperability is a longer term benefit, and therefore less satisfactory
as a primary driver for adoption although it can be valuable when considering
exit strategies and risk managements.

## Guidelines

- Guidelines can be more dynamic than standards since they are, by
definition, less prescriptive. As such, they can be used by organisations as a
strategic tool, to track the changing technology and standards landscape and
make appropriate plans within the constraints of organisational resources and
timescales

- Guidelines can recommend standards and may recommend more than one standard
if there is not a single optimal path. In that case, guidelines should discuss
the pros and cons of the various approaches, and also indicate possible
migration routes or mapping between them. If such routes don’t exist then it is
likely the different standards address distinct problem domains.

- Guidelines can recommend *how* to implement standards. There are many rather
less well-defined or expansive standards that are not cost-effective to
implement in their entirety. Guidelines can help identify useful subsets or
specific interpretations of such standards which can be more practical and
useful, essentially mitigating the problem. This can be particularly valuable
when considering interoperability, where focussing overly on handling specific,
niche details can hamper progress and limit benefits realisation. Guidelines can
sometimes also recommend or discourage the use of certain *versions* of a
particular standard for similar reasons. For example, BIBFRAME V2.X is very
different and a great improvement on V1.0 which should be avoided since it
replicated many of the issues of its predecessor, MARC.

- As guidelines operate at a more strategic level than standards they can
indicate when standards are becoming obsolete-as happens to all technologies. In
this case, they should also identify exit strategies and migration paths.

## Common design pitfalls in standards and guidelines development

- Over prescriptive guidelines or standards can be a significant long term
dis-benefit by hampering the use of new technologies and techniques. Good
approaches are:

  - Standards should be simple and focussed on a well-defined
requirement/problem (see previous).

  - Prescribe only the minimum elements required to achieve the goals of the
standard. This reduces both the cost of implementation but also minimises the
cost of interoperability and migration efforts downstream.

  - Evaluate design decisions in terms of what functionalities they prevent as
well as what they enable. All standards involve some trade-offs and this is
especially true for long term preservation applications. For example, the choice
of PDF format for archiving publications was good for human readability but did
not consider machine readability as a requirement, not only making subsequent
text mining and analytics of such materials difficult but also reducing the
effectiveness of accessibility tools such as screen readers.

  - Beyond the minimal core requirements it may be useful to provide or document
an optional extension mechanism that makes a clear distinction between core
functionality and functionality that is considered more friable in the long
term.

- Over complex standards that are expensive and time consuming to implement are
likely to be avoided on a simple cost basis. Even when there is adoption, it is
likely that only a subset of the standard or guideline is implemented (to solve
the adoptees particular use case), resulting in multiple incompatible variants
that effectively undermine the notion of a standard. As noted above, guidelines
can address this issue.

- Vaguely defined standards suffer from a similar problem, stemming from
different interpretations of the standard. Requiring a validation mechanism goes
a long way to eliminating such cases.

- Guidelines that recommend inappropriate standards for particular applications
can also cause problems. Technologies are not objective creations and should be
approached critically. It is important to understand the original design goals
for a standard, and also the socio-cultural biases and assumptions under which
it was created. A lot of standards in the technology area are very Anglo-centric
– making assumptions about names, places and dates that don’t translate well to
other cultures. Just because a standard *can* support a particular use case does
not mean it is necessarily a *good* solution for that use case.

- Standards often suffer from scope creep over time. Standards gradually expand
functionality and use cases through successive versions, each iteration becoming
slightly less effective at addressing the original design goals, and generally
addressing the newly added goals far less effectively than a dedicated standard.
Guidelines can identify these cases and discourage the use of the offending
versions or recommend the adoption of a more considered subset.

## Ensuring implementability across institutions with varying capacities

To some extent this question is mainly answered by adopting the best practices 
and avoiding the pitfalls described above, but with a couple of additional points.

- Guidelines should include case studies that clearly demonstrate the value of
adoption to all sizes of organisation, effectively providing business cases for
potential adoptees. The construction of these studies can also be a valuable
point of engagement with the target community.

- Aim for small, focussed, granular standards that are cheap to implement. A
smaller organisation can adopt these more easily over time, since they can
validate compliance at each stage and gain a sense of achievement, rather than
attempting a large implementation and compliance exercise that is time and
resource consuming with a high chance of failure.

- Standards and guideless should change slowly over time, and should be
recognised as doing so. This encourages smaller organisations to seek compliance
since it is an achievable goal rather than a continuously receding target.

- Aim for open standards that have open-source implementations so the cost of
entry can be close to zero. Larger organisations can help support the
development of such tools (and associated training and support) to enable them
to be freely available to smaller organisations. IIIF, for example has both
commercial and open-source implementations and is supported by a consortium
funded by larger libraries and other organisations around the world.

## Ensuring standards and guidelines remain relevant

- Guidelines should be recognised as being driven by the community that the
guidelines are aimed at rather than imposed externally. This not only provides
engagement that helps adoption but also provides a mechanism for developing and
maintaining skills and expertise at a national level.

- Ideally, national guidelines should, as much as possible, make use of
internationally recognised standards since they will be better supported in the
longer term both in terms of technology and skills. Engagement with the
international organisations concerned would be a great development opportunity
for local staff.

- Avoid defining new standards if possible since, at least to begin with, they
are likely to only have local support. Instead, aim to engage with and co-opt
existing standards initiatives to guide international standards in the desired
direction.

- Define a process and timetable for reviewing and updating the guidelines and
engage with local staff to participate – possibly with funding or other support.
While the initial work may involve external consultancy, over time this should
ideally be reduced to encourage local talent development.

