---
title: "Extensions to TLS FATT Process"
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

informative:
  I-D.ietf-tls-rfc8446bis:
  I-D.fossati-tls-attestation-08:
  RFC4101:
  TLS-FATT:
     author:
        org: IETF TLS WG
     title: TLS FATT Process
     target: https://github.com/tlswg/tls-fatt
     date: June 2025
  Meeting-122-TLS-Slides:
       title: "Identity Crisis in Attested TLS for Confidential Computing"
       date: 20 March 2025,
       target: https://datatracker.ietf.org/meeting/122/materials/slides-122-tls-identity-crisis-00
       author:
       -
         ins: M. U. Sardar
       -
         ins: M. Moustafa
       -
         ins: T. Aura

--- abstract

This document proposes a new "Formal Analysis Considerations" section where the authors provide a threat model, informal security goals, and a protocol diagram.
This document applies only to non-trivial extensions of TLS, which require formal analysis.


--- middle

# Introduction
While the TLS FATT process {{TLS-FATT}} marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group process, the current FATT process has some practical limitations. Given a relatively smaller formal methods community, and a steep learning curve as well as very low consideration of usability in the existing formal analysis tools, this document proposes some solutions to make the FATT process sustainable.

Specifically, the TLS FATT process does not outline the division of responsibility between the authors and the one doing the formal analysis (the latter is hereafter referred to as the "verifier"). This document aims to fill this gap without putting an extensive burden on either party.

An argument is often presented by the authors that an Internet-Draft is written for the implementers. With the FATT process, this argument is no longer valid. This document outlines the corresponding changes in the way Internet-Drafts are typically written. For the Internet-Draft to be useful for the formal analysis, this document proposes a new "Formal Analysis Considerations" section containing three main items, namely:

* a threat model,
* informal security goals, and
* a protocol diagram ({{sec-prot-diagram}}).

Each one of these is summarized in {{sec-res-authors}}. Future versions of this draft will include concrete examples.

Responsibilities of the verifier are summarized in {{sec-res-verifier}}.

## Motivation
A clear separation of resposibilities would help IRTF UFMRG to train the authors and verifiers separately to fulfill their own responsibilities.

[comment]: <> (The goal of authors of Internet-Draft is to ...)


# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Protocol Diagram
{: #sec-prot-diagram }

In the context of this document, a protocol diagram specifies the proposed cryptographically-relevant changes compared to the standard TLS protocol {{I-D.ietf-tls-rfc8446bis}}. This is conceptually similar to the Protocol Model in {{RFC4101}}. However, while {{RFC4101}} only recommends diagrams, we consider diagrams to be essential.

## Definition of Attack
Any ambiguity originating from the threat model, informal security goals, and a protocol diagram is to be considered as an attack. The authors are, therefore, encouraged to be as precise as possible.

# Responsibilities of Authors
{: #sec-res-authors }

This document proposes a new "Formal Analysis Considerations" section where the authors provide the following three items:

## Threat Model
A threat model outlines the assumptions and known weaknesses of the proposed protocol. The threat model could be the classical Dolev-Yao adversary. In addition, it could specify any keys (e.g., long-term keys or session keys) which are assumed to be compromised (i.e., available to the adversary).

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. should be outlined in the Internet-Draft.
If the informal security goals are not spelled out in the Internet-Draft, it is safe to assume that the goals are still unclear to the authors. In such a case, the Internet-Draft should not be considered as ready for adoption.

[section]: <> (These goals could be part of the security considerations or the Appendix.)


## Protocol Diagram
A protocol diagram should clearly mention the initial knowledge of the protocol participants, e.g., which authentic public keys are known to the protocol participants at the start of the protocol. An example of a protocol diagram for {{I-D.fossati-tls-attestation-08}} is provided in Section 3 of {{Meeting-122-TLS-Slides}}.

# Responsibilities of Verifier
{: #sec-res-verifier }

When the authors declare the version as ready for formal analysis, the verifier takes the above inputs, performs the formal analysis, and brings the results back to the authors and the working group. Based on the analysis, the verifier may propose updates to the "Formal Analysis Considerations" section, Security Considerations section or other sections of the Internet-Draft.

[comment]: <> (This most likely needs some coordination with the authors.)

# Security Considerations

The whole document is about improving security considerations.


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
