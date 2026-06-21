---
title: "Proposed Document Template for TLS FATT Process"
category: info

docname: draft-usama-tls-fatt-extension-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Security"
workgroup: "Transport Layer Security"
venue:
  group: "Transport Layer Security"
  type: "Working Group"
  mail: "tls@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/tls/"
  github: "muhammad-usama-sardar/tls-fatt-extension"
  latest: "https://muhammad-usama-sardar.github.io/tls-fatt-extension/draft-usama-tls-fatt-extension.html"

author:
 -
    fullname: "Muhammad Usama Sardar"
    organization: TU Dresden
    email: "muhammad_usama.sardar@tu-dresden.de"

normative:
  TLS-FATT:
     author:
        org: IETF TLS WG
     title: TLS FATT Process
     target: https://github.com/tlswg/tls-fatt
     date: June 2025

informative:
  I-D.ietf-tls-rfc8446bis:
  I-D.fossati-tls-attestation-08:
  RFC4101:
  ID-Crisis: DOI.10.1145/3779208.3785387
  I-D.ietf-tls-8773bis:
  I-D.wang-tls-service-affinity:
  I-D.sheffer-tls-pqc-continuity:

--- abstract

This document applies only to non-trivial extensions of TLS, which require formal analysis. It proposes the authors specify a clear threat model and informal security goals in the Security Considerations section, as well as motivation and a protocol diagram in the draft.

--- middle

# Introduction
While the TLS FATT process {{TLS-FATT}} marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group (WG) process, the current FATT process has some practical limitations. Given a relatively smaller formal methods community, and a steep learning curve as well as very low consideration of usability in the existing formal analysis tools, this document proposes some solutions to make the FATT process sustainable.

This document outlines the corresponding changes in the way Internet-Drafts are typically written.
For the Internet-Draft to be useful for the formal analysis, this document proposes that it would be helpful for the formal analysis if the draft contains four main items, namely:

* motivation,
* a threat model,
* informal security goals, and
* a protocol diagram ({{sec-prot-diagram}}).

Each one of these is summarized in {{sec-res-authors}}. Future versions of this draft will include concrete examples.

## Motivation
This helps make the formal analysis closer to the intention in specifications.

Implementers may like to understand the security implications before blindly starting to implement the spec.


## Scope
The scope of this document is only non-trivial extensions of TLS, which require formal analysis.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Protocol Diagram
{: #sec-prot-diagram }

In the context of this document, a Protocol Diagram specifies the proposed cryptographically-relevant changes compared to the standard TLS protocol {{I-D.ietf-tls-rfc8446bis}}. This is conceptually similar to the Protocol Model in {{RFC4101}}. However, while {{RFC4101}} only recommends diagrams, we consider diagrams to be essential.

# Contribution of Authors
{: #sec-res-authors }

The following contributions are expected from the authors:

## Real Motivation
Authors are expected to provide the real motivation of the work (i.e., the proposed extension of TLS).

## Threat Model
{: #sec-th-model }

A threat model identifies which threats are in scope for the protocol design. So it ought to answer questions like:

* What are the capabilities of the adversary? What can the adversary do?
* Whether post-quantum threats are in scope?
* What can go wrong in the system? etc.
* What are the computational and memory resources available to the adversary?

### Typical Dolev-Yao adversary
A typical threat model assumes the classical Dolev-Yao adversary, who has full control over the communication channel.

Any additional adversary capabilities and assumptions ought to be explicitly stated.

### Potential Weaknesses of Cryptographic Primitives
In general, it also outlines the potential weaknesses of the cryptographic primitives used in the proposed protocol extension. Examples include:

* weak hash functions
* weak Diffie-Hellman (DH) groups
* weak elements within strong DH groups

### Keys
This section ought to specify any keys in the system (e.g., long-term keys of the server) in addition to the standard TLS key schedule. Theoretically and arguably practically, any key may be compromised (i.e., become available to the adversary).

For readability, we propose defining each key clearly as in Section 4.1 of {{ID-Crisis}}. Alternatively, present as a table with the following entries for each key:

* Name (or symbol) of the key
* Purpose of the key
* (optionally but preferably -- particularly when the endpoint is not fully trusted) Which software in the system has access to the key?

If more than one servers are involved (such as migration cases), the keys for servers ought to be distinguished in an unambiguous way.

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. ought to be outlined in the Internet-Draft.
If the informal security goals are not spelled out in the Internet-Draft, it is safe to assume that the goals are still unclear to the authors.

[section]: <> (In such a case, the Internet-Draft should not be considered as ready for adoption. These goals could be part of the security considerations or the Appendix.)

Examples:

* Integrity of message X holds unless some key Y is leaked.
* (stated differently) Integrity of message X holds as long as some key Y is protected.
* Freshness of message X holds unless some key Y or some key Z is leaked.
* Server Authentication holds unless some key Y or some key Z is leaked.

See Section 5.1 of {{ID-Crisis}} for concrete examples.

## Protocol Diagram
A Protocol Diagram ought to clearly mention the initial knowledge of the protocol participants, e.g., which authentic public keys are known to the protocol participants at the start of the protocol. An example of a Protocol Diagram for {{I-D.fossati-tls-attestation-08}} is provided in Figure 5 in {{ID-Crisis}}.

# Document Structure
While the needs may differ for some drafts, we propose the following baseline template, with an example of {{I-D.wang-tls-service-affinity}}:

The template is:

* Easy for readers
* Easy for reviewers
* Easy for formal analysis

TODO: Currently it is almost a copy of the [guidance email](https://mailarchive.ietf.org/arch/msg/tls/LfIHs1OVwDKWmDuCEx0p8wP-KPs/) to the authors. We will add details in next versions.

## Introduction
   * Problem statement: Say in general what the problem is.
   * For {{I-D.wang-tls-service-affinity}}, we believe this
      should *not* include CATS. Anyone unfamiliar with CATS ought to be
      able to understand your problem.

## Terminology
   * Define any terms not defined in RFC8446bis or point to other drafts from where the definition is used.

## Motivation and design rationale
   * We really like how the author of {{I-D.ietf-tls-8773bis}} motivates the problem statement. Use it as a sample.
   * Here authors ought to address all the concerns from WG, including
      justification with compelling arguments and authentic references
      why authors think it ought to be done within TLS WG (and within handshake).
   * For {{I-D.wang-tls-service-affinity}}, authors could put CATS here as a motivational use case.
   * For {{I-D.sheffer-tls-pqc-continuity}}, it should clarify why the problem is specific to PQ-only and why did the WG do such a thing for the transition for other primitives.

## Proposed solution (one or more sections)
   * Protocol design with Protocol Diagram: we work on the formal analysis of TLS 1.3 exclusively. Please contact someone else if your draft relates to older versions.

## Security considerations

### Threat model

### Desired security goals

As draft proceeds these desired security goals will become what the draft actually achieves.

   * For {{I-D.sheffer-tls-pqc-continuity}}, it should clarify which property of the TLS protocol is broken and how does the proposal improve the security.

### Other security implications/considerations


[comment]: <> (This most likely needs some coordination with the authors.)

# Security Considerations
{: #sec-sec-cons }

The whole document is about improving security considerations.

Like all security proofs, formal analysis is only as strong as its assumptions and model. The scope is typically limited, and the model does not necessarily capture real-world deployment complexity, implementation details, operational constraints, or misuse scenarios. Formal methods should be used as complementary and not as subtitute of other analysis methods.


# IANA Considerations

This document has no IANA actions.


--- back

# Appendix
{:unnumbered}

## Document History
{:unnumbered}

-08

* Focused on document structure only

-07

* Failure of current process
* Students of FATT
* Lead FATT Person for Contact
* Feedback from the WG


-06

* Solution for ML-KEM: FATT analysis
* Solution for FATT contact: new mailing list
* Replaced responsibilities by expected contributions
* Clarified Verifier even further that it is just a WG member; no formal role
* s/pure/non-hybrid

-05

* Removed process-related stuff
* Moved discussion at meeting to solutions
* Added ML-KEM

-04

* Extended threat model {{sec-th-model}}
* Helpful discussions on formal analysis in meetings
* Pointer to formal analysis and costs

-03

* Limitations of formal analysis in security considerations
* Proposed solutions section
* More guidance for authors: Threat Model and Informal Security Goals

-02

* Added document structure
* FATT-bypass by Other TLS-related WGs
* FATT process not being followed

-01

* Pain points of Verifier {{sec-prot-diagram}}
* Small adjustment of phrasing

# Acknowledgments
{:numbered="false"}
We thankfully acknowledge the following for their valuable input:

* Eric Rescorla for review of -02, -05, and -06.
* John Mattsson for proposing text for security considerations.
* S. Moonesamy for identifying the 'no response' risk in the proposal for new list.
* David Benjamin for review of -06.
* Mike Ounsworth for review of -07.

The research work is funded by German Research Foundation ("Deutsche Forschungsgemeinschaft.")
