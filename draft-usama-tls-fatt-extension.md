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
  ID-Crisis:
    title: "Identity Crisis in Confidential Computing: Formal Analysis of Attested TLS"
    date: November 2025,
    target: https://www.researchgate.net/publication/398839141_Identity_Crisis_in_Confidential_Computing_Formal_Analysis_of_Attested_TLS
    author:
      - ins: M. U. Sardar
      - ins: M. Moustafa
      - ins: T. Aura
  I-D.irtf-cfrg-cryptography-specification:
  I-D.ietf-tls-extended-key-update:
  I-D.ietf-tls-8773bis:
  FormalAnalysisPAKE:
     title: "Formal analysis of draft-ietf-tls-pake"
     date: 02 January 2026,
     target: https://mailarchive.ietf.org/arch/msg/tls/igQGFE1INA6eR_Fdz8eTp74ffVc/
     author:
     - ins: M. U. Sardar
  FormalAnalysisKeyUpdate:
     title: "Comments on draft-ietf-tls-extended-key-update"
     date: 03 October 2025,
     target: https://mailarchive.ietf.org/arch/msg/tls/P_VdWSi20TZG0rJEaz7VCPKDIOg/
     author:
     - ins: M. U. Sardar

--- abstract

This document applies only to non-trivial extensions of TLS, which require formal analysis. It proposes the authors provide a threat model and informal security goals in the Security Considerations section, and a protocol diagram in the draft.
We also briefly present a few pain points of the one doing the formal analysis which require refining the process:

* Contacting FATT
* Understanding the opposing goals
* No response from some authors
* Slots at meeting


--- middle

# Introduction
While the TLS FATT process {{TLS-FATT}} marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group (WG) process, the current FATT process has some practical limitations. Given a relatively smaller formal methods community, and a steep learning curve as well as very low consideration of usability in the existing formal analysis tools, this document proposes some solutions to make the FATT process sustainable.

Specifically, the TLS FATT process does not outline the division of responsibility between the authors and the one doing the formal analysis (the latter is hereafter referred to as the "verifier"). This document aims to propose some solutions without putting an extensive burden on either party.

An argument is often presented by the authors that an Internet-Draft is written for the implementers. We make several counter-arguments here:

* Researchers and protocol designers are also stakeholders of such specifications {{I-D.irtf-cfrg-cryptography-specification}}.
* Even implementers may like to understand the security implications before blindly starting to implement it.
* With the FATT process, this argument is clearly invalid. The verifier may not be the same as the implementer.

This document outlines the corresponding changes in the way Internet-Drafts are typically written. For the Internet-Draft to be useful for the formal analysis, this document proposes that the draft should contain three main items, namely:

* a threat model,
* informal security goals, and
* a protocol diagram ({{sec-prot-diagram}}).

Each one of these is summarized in {{sec-res-authors}}. Future versions of this draft will include concrete examples.

Responsibilities of the verifier are summarized in {{sec-res-verifier}}.

## Motivation
A clear separation of resposibilities would help IRTF UFMRG to train the authors and verifiers separately to fulfill their own responsibilities.


# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Protocol Diagram
{: #sec-prot-diagram }

In the context of this document, a protocol diagram specifies the proposed cryptographically-relevant changes compared to the standard TLS protocol {{I-D.ietf-tls-rfc8446bis}}. This is conceptually similar to the Protocol Model in {{RFC4101}}. However, while {{RFC4101}} only recommends diagrams, we consider diagrams to be essential.

## Definition of Attack
Any ambiguity originating from the threat model, informal security goals, and a protocol diagram is to be considered as an attack. The authors are, therefore, encouraged to be as precise as possible.

## Verifier
In this document, verifier refers to the person doing the formal analysis.

# Pain Points of Verifier
{: #sec-pain-points }

From the two extremes -- {{I-D.ietf-tls-8773bis}} where Russ kindly provided all requested inputs and we were able to get it through without any formal analysis to {{I-D.fossati-tls-attestation-08}} where formal analysis revealed vulnerabilities {{ID-Crisis}} and resulted in a separate WG to tackle this problem -- we summarize the pain points of the verifier.

## Contacting FATT
The verifier should be allowed to contact the FATT at least once some draft is out from the TLS WG. Formal methods community is small and those with deep knowledge of TLS are quite limited. Not being able to contact them puts the verifier at great disadvantage.


## Understanding the Opposing Goals
The authors need to understand that the task of the verifier is to find the subtle corner cases where the protocol may fail. This is naturally opposed to the goal of the authors.
But unless the verifier remains really focused on doing that, there is little value of formal analysis.
In particular, some topics like remote attestation need more precise specifications because small changes may make a big difference.

[comment]: <> (We also argue that in the current process, the stakeholder at most disadvantage is . We all have a shared goal of producing high-quality specifications.)

## No Response from Some Authors
Some authors of adopted drafts do not respond for several months, despite repeated reminders {{FormalAnalysisPAKE}}.

## Slots at Meeting
Formal analysis -- just like any other code development -- is an iterative process and needs to be progressively discussed with the WG to be able to propose secure solutions. So at least some time should be allocated in the meetings for discussion of formal analysis.

* We requested a slot for 10 minutes (and 5 minutes if tight on schedule) for discussion of our questions about {{I-D.ietf-tls-extended-key-update}} at IETF 124. It seemed that the slots were spread over the meeting time to show that there is no time left for our topic. In the end, the meeting ended one hour earlier where 10 minutes from that could have been utilized for discussion on formal analysis of {{I-D.ietf-tls-extended-key-update}}. Given that the authors were informed {{FormalAnalysisKeyUpdate}} about the issues, what the authors presented was not very helpful in terms of progressing the formal analysis work and proposing some solutions. Key schedule is a subtle topic and not something we can talk effectively on the mic without a proper diagram on display. It is unclear why formal analysis is such a low priority to the chairs.

* If the authors are doing the formal analysis themselves, they should also present the current state of formal analysis for discussion. This will help the verifier give any feedback and avoid any repititive effort for the verifier.

[comment]: <> (The goal of authors of Internet-Draft is to ...)




# Responsibilities of Authors
{: #sec-res-authors }

This document proposes that the authors provide the following three items:

## Threat Model
A threat model outlines the assumptions and known weaknesses of the proposed protocol. The threat model could be the classical Dolev-Yao adversary. In addition, it could specify any keys (e.g., long-term keys or session keys) which may be compromised (i.e., available to the adversary).

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. should be outlined in the Internet-Draft.
If the informal security goals are not spelled out in the Internet-Draft, it is safe to assume that the goals are still unclear to the authors.

[section]: <> (In such a case, the Internet-Draft should not be considered as ready for adoption. These goals could be part of the security considerations or the Appendix.)


## Protocol Diagram
A protocol diagram should clearly mention the initial knowledge of the protocol participants, e.g., which authentic public keys are known to the protocol participants at the start of the protocol. An example of a protocol diagram for {{I-D.fossati-tls-attestation-08}} is provided in Figure 5 in {{ID-Crisis}}.

# Responsibilities of Verifier
{: #sec-res-verifier }

When the authors declare the version as ready for formal analysis, the verifier takes the above inputs, performs the formal analysis, and brings the results back to the authors and the WG. Based on the analysis, the verifier may propose updates to the Security Considerations section or other sections of the Internet-Draft.

[comment]: <> (This most likely needs some coordination with the authors.)

# Security Considerations

The whole document is about improving security considerations.


# IANA Considerations

This document has no IANA actions.


--- back

# Appendix
{:unnumbered}

## Document History
{:unnumbered}

-01

* Pain points of verifier {{sec-prot-diagram}}
* Small adjustment of phrasing

[comment]: <> (# Acknowledgments {:numbered="false"} TODO acknowledge.)
