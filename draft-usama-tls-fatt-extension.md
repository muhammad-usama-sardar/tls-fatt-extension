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
    organization: TU Dresden, Germany
    email: "muhammad_usama.sardar@tu-dresden.de"
 -
    fullname: "Songbo Bu"
    organization: Shanghai Guan An Information Technology Co., Ltd., China
    email: "bluedognull@gmail.com"


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
  I-D.fossati-tls-attestation-09:
  RFC4101:
  ID-Crisis: DOI.10.1145/3779208.3785387
  ID-Crisis-repo:
    title: "Identity Crisis in Confidential Computing: Formal Analysis of Attested TLS"
    date: November 2025,
    target: https://github.com/CCC-Attestation/formal-spec-id-crisis
    author:
      - ins: M. U. Sardar
      - ins: M. Moustafa
      - ins: T. Aura
  I-D.ietf-tls-8773bis:
  I-D.wang-tls-service-affinity:
  I-D.sheffer-tls-pqc-continuity:
  Intra-handshake.fail:
    title: "Intra-handshake.fail (CVE-2026-33697): High-severity CVE in Attested TLS"
    date: June 2026,
    target: https://www.researchgate.net/publication/408219182_Intra-handshakefail_CVE-2026-33697_High-severity_CVE_in_Attested_TLS
    author:
      - ins: M. U. Sardar
      - ins: V. Dubeyko
      - ins: J-M. Jacquet
  Intra-handshake.fail-repo:
    title: "Intra-handshake.fail (CVE-2026-33697): High-severity CVE in Attested TLS"
    date: June 2026,
    target: https://github.com/CCC-Attestation/formal-spec-KBS
    author:
      - ins: M. U. Sardar
      - ins: V. Dubeyko
      - ins: J-M. Jacquet
  Intra-handshake-attestation:
    title: "Attestation and TLS"
    date: 8 November 2024,
    target: https://datatracker.ietf.org/meeting/121/materials/slides-121-tls-tls-and-attestation-00.pdf
    author:
      - ins: Hannes Tschofenig
  CVE-2026-33697:
     author:
        org: CVE
     title: CoCoS attested TLS is vulnerable to relay attacks via extracted ephemeral TLS keys
     target: https://www.cve.org/CVERecord?id=CVE-2026-33697
     date: March 2026



--- abstract

This document applies only to non-trivial extensions of TLS, which require formal analysis.
FATT process has successfully discovered CVEs of **CVSS 7.5** and most recently expected **CVSS 9.1** in the **production** implementations of the drafts proposed for adoption in the TLS WG.
To achieve high cryptographic assurances, this document proposes the drafts specify a clear threat model and informal security goals in the Security Considerations section, as well as motivation and a protocol diagram in the draft.

--- middle

# Introduction
While the TLS FATT process {{TLS-FATT}} marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group (WG) process, it would be helpful to adapt the way in which drafts are typically written to get the benefits.


## Motivation
Unverified protocol designs, imprecisely stated threat model and security goals have led to high and critical severity vulnerabilities of the extensions proposed in the drafts.

### Concrete Motivational Example: Practical Exploits in Production Systems
{: #sec-mot-example }

As an illustrative example, authors of {{I-D.fossati-tls-attestation-08}} asked for adoption in IETF 121, explicitly requesting us (by name) for formal analysis {{Intra-handshake-attestation}}. We carried out formal analysis of draft in support for FATT process. The formal analysis led to three orthogonal issues:

- Formal analysis {{ID-Crisis-repo}} found **diversion** attacks for {{I-D.fossati-tls-attestation-08}}. For technical details, please see the corresponding paper {{ID-Crisis}}.

- Formal analysis {{Intra-handshake.fail-repo}} of several **production** implementations of {{I-D.fossati-tls-attestation-09}} led to discovery of {{CVE-2026-33697}} of **CVSS 7.5** for **relay** attacks. For technical details, please see the corresponding paper {{Intra-handshake.fail}}.

- Further formal analysis of **production** implementation of {{I-D.fossati-tls-attestation-09}} has led to discovery of another class of attacks and will potentially lead to three CVEs (currently under *responsible* disclosure) each with an expected **CVSS 9.1**.

This shows the value of FATT process in the design of secure protocols to find subtle vulnerabilities, which could otherwise be missed.

## Proposal
To produce high-quality specifications, this document outlines the corresponding changes in the way drafts are typically written.
For the draft to be useful for the formal analysis, this document proposes that it would be helpful for the formal analysis if the draft contains four main items, namely:

* motivation,
* a threat model,
* informal security goals, and
* a protocol diagram ({{sec-prot-diagram}}).

Each one of these is summarized in {{sec-res-authors}}. Future versions of this draft will include further concrete examples.

## Scope
The scope of this document is only non-trivial extensions of TLS, which require formal analysis.
As per FATT process {{TLS-FATT}}, this includes changes in the key schedule or the authentication process or any other part of the cryptographic protocol that has been formally modeled and analyzed in the past.
As per FATT process {{TLS-FATT}}, the chairs make a determination whether the change proposed by the document requires review by the FATT to determine if formal protocol analysis is necessary for the change.
Hence, such a determination is out of scope of this document.

# Conventions and Definitions

[comment2]: <> ({::boilerplate bcp14-tagged})

## Protocol Diagram
{: #sec-prot-diagram }

In the context of this document, a Protocol Diagram specifies the proposed cryptographically-relevant changes compared to the standard TLS protocol {{I-D.ietf-tls-rfc8446bis}}. This is conceptually similar to the Protocol Model in {{RFC4101}}. However, while {{RFC4101}} only recommends diagrams, we consider diagrams to be essential to reduce the gap between:

* the specifications and formal analysis
* the specifications and implementation


# Contents of Drafts
{: #sec-res-authors }

The following contents are expected in drafts:

## Motivation
Drafts are expected to provide the motivation of the work (i.e., the proposed extension of TLS).

## Threat Model
{: #sec-th-model }

A threat model identifies which threats are in scope for the protocol design. So it can answer questions like:

* What are the capabilities of the adversary? What can the adversary do?
* Whether post-quantum threats are in scope?
* What can go wrong in the system? etc.
* What are the computational and memory resources available to the adversary?

### Typical Dolev-Yao adversary
A typical threat model assumes the classical Dolev-Yao adversary, who has full control over the communication channel.

Any additional adversary capabilities and assumptions ought to be explicitly stated.

### Keys
This is particularly relevant for proposals of hybrid key establishment or hybrid authentication.
This section ought to specify any keys in the system (e.g., long-term keys of the server) in addition to the standard TLS key schedule. Theoretically and arguably practically, any key may be compromised (i.e., become available to the adversary).

For readability, we propose defining each key clearly as in Section 4.1 of {{ID-Crisis}}. Alternatively, present as a table with the following entries for each key:

* Name (or symbol) of the key
* Purpose of the key
* (optionally but preferably -- particularly when the endpoint is not fully trusted) Which software in the system has access to the key?

If more than one servers are involved (such as migration cases), the keys for servers ought to be distinguished in an unambiguous way.

### Template
For the threat model, useful fields might include:

- protocol participants and roles;
- assets or properties to protect;
- initial authenticated knowledge;
- adversary capabilities;
- trust boundaries;
- key-compromise assumptions;
- downgrade and negotiation assumptions;
- deployment or migration assumptions;
- explicit non-goals.

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. ought to be outlined in the draft.

[section]: <> (In such a case, the Internet-Draft should not be considered as ready for adoption. These goals could be part of the security considerations or the Appendix.)

Examples:

* Integrity of message X holds unless some key Y is leaked.
* (stated differently) Integrity of message X holds as long as some key Y is protected.
* Freshness of message X holds unless some key Y or some key Z is leaked.
* Server Authentication holds unless some key Y or some key Z is leaked.

See Section 5.1 of {{ID-Crisis}} for concrete examples.

### Template

- Property:
- Protected object:
- Adversary capability:
- Required assumptions:
- Failure condition:
- Non-goals:
- Candidate formal query or correspondence:

## Protocol Diagram
A Protocol Diagram ought to clearly mention the initial knowledge of the protocol participants, e.g., which authentic public keys are known to the protocol participants at the start of the protocol. An example of a Protocol Diagram for {{I-D.fossati-tls-attestation-08}} is provided in Figure 5 in {{ID-Crisis}}.

# Document Structure
While the needs may differ for some drafts, we propose the following baseline template, with examples of {{I-D.wang-tls-service-affinity}} and {{I-D.sheffer-tls-pqc-continuity}}:

The template is easy for:

* readers
* reviewers
* formal analysis team

TODO: Currently it is almost a copy of the [guidance email](https://mailarchive.ietf.org/arch/msg/tls/LfIHs1OVwDKWmDuCEx0p8wP-KPs/) to the authors. We request feedback on what to add in next versions.

## Introduction
   * Problem statement: Say in general what the problem is.
   * For {{I-D.wang-tls-service-affinity}}, we believe this
      may preferably *not* include CATS. Anyone unfamiliar with CATS ought to be
      able to understand the problem statement.

## Terminology
   * Define any terms not defined in RFC8446bis or point to other drafts from where the definition is used.

## Motivation and design rationale
   * We really like how the author of {{I-D.ietf-tls-8773bis}} motivates the problem statement. Use it as a sample.
   * Here authors can address all the concerns from WG, including
      justification with compelling arguments and authentic references
      why authors think it ought to be done within TLS WG (and within handshake).
   * For {{I-D.wang-tls-service-affinity}}, authors could put CATS here as a motivational use case.
   * For {{I-D.sheffer-tls-pqc-continuity}}, it should clarify why the problem is specific to PQ-only and why did the WG do such a thing for the transition for other primitives, as requested by several WG participants.

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

The whole document is about improving security considerations. As mentioned in {{sec-mot-example}}, unverified specifications have led to high and critical severity exploits.

Like all security proofs, formal analysis is only as strong as its assumptions and model. The scope is typically limited, and the model does not necessarily capture real-world deployment complexity, implementation details, operational constraints, or misuse scenarios. Formal methods should be used as complementary and not as subtitute of other analysis methods.


# IANA Considerations

This document has no IANA actions.


--- back

# Appendix
{:unnumbered}

## Document History
{:unnumbered}

-09

* Template for threat model and informal security goals
* Added Songbo as co-author

-08

* Focused on document structure only
* Motivational examples

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
* David Benjamin for review of -06.
* Mike Ounsworth for review of -07.

We gratefully acknowledge the valuable contributions of co-authors of papers for their instrumental contributions in formal analysis: Mariam Moustafa, Tuomas Aura, Viacheslav Dubeyko, and Jean-Marie Jacquet.

We sincerely thank the contributors of the formal analyses {{ID-Crisis-repo}} and {{Intra-handshake.fail-repo}} mentioned in the respective repositories.

We express our appreciation to Yaakov Stein and Ilari Liusvaara for their substantial technical guidance, valuable feedback, and contributions in early attempts to formally model ML-KEM.

The research work is funded by German Research Foundation ("Deutsche Forschungsgemeinschaft.")
