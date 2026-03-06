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
  I-D.fossati-seat-early-attestation-00:
  RFC8773bis:
  I-D.ietf-tls-mlkem:
  I-D.wang-tls-service-affinity:

--- abstract

This document applies only to non-trivial extensions of TLS, which require formal analysis. It proposes the authors provide a threat model and informal security goals in the Security Considerations section, as well as motivation and a protocol diagram in the draft.
We also briefly present a few pain points of the team doing the formal analysis which -- we believe -- require refining the process:

* Contacting FATT
* Understanding the opposing goals
* No response from some authors
* Slots at meeting
* Provide protection against FATT-bypass by other TLS-related WGs
* Process not being followed


--- middle

# Introduction
While the TLS FATT process {{TLS-FATT}} marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group (WG) process, the current FATT process has some practical limitations. Given a relatively smaller formal methods community, and a steep learning curve as well as very low consideration of usability in the existing formal analysis tools, this document proposes some solutions to make the FATT process sustainable.

Specifically, the TLS FATT process does not outline the division of responsibility between the authors and the team doing the formal analysis (the latter is hereafter referred to as the "Verifier"). This document aims to propose some solutions without putting an extensive burden on either party.

An argument is often presented by the authors that an Internet-Draft is written for the implementers. We make several counter-arguments here:

* Researchers and protocol designers are also stakeholders of such specifications {{I-D.irtf-cfrg-cryptography-specification}}.
* Even implementers may like to understand the security implications before blindly starting to implement it.
* With the FATT process, this argument is clearly invalid. The Verifier may not be the same as the implementer.

This document outlines the corresponding changes in the way Internet-Drafts are typically written.
For the Internet-Draft to be useful for the formal analysis, this document proposes that the draft should contain four main items, namely:

* motivation,
* a threat model,
* informal security goals, and
* a protocol diagram ({{sec-prot-diagram}}).

Each one of these is summarized in {{sec-res-authors}}. Future versions of this draft will include concrete examples.

Responsibilities of the Verifier are summarized in {{sec-res-verifier}}.

## Motivation
A clear separation of responsibilities would help IRTF UFMRG to train the authors and verifiers separately to fulfill their own responsibilities.

Moreover, we believe that the experiences can help improve the FATT process. The goal is to document the identified gaps with concrete examples, discuss those and mutually find the best way forward.

## Scope
The scope of this document is only non-trivial extensions of TLS, which require formal analysis.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Protocol Diagram
{: #sec-prot-diagram }

In the context of this document, a Protocol Diagram specifies the proposed cryptographically-relevant changes compared to the standard TLS protocol {{I-D.ietf-tls-rfc8446bis}}. This is conceptually similar to the Protocol Model in {{RFC4101}}. However, while {{RFC4101}} only recommends diagrams, we consider diagrams to be essential.

## Verifier
In this document, the Verifier refers to the person (team) doing the formal analysis.
Note that it is not a new formal role in the WG process.

## Definition of Attack
Any ambiguity originating from the threat model, informal security goals, and a Protocol Diagram is to be considered as an attack.
The authors are, therefore, encouraged to be as precise as possible.
The Verifier may propose text for consideration by authors/WG to disambiguate or propose a fix to the attack.

# Pain Points of Verifier
{: #sec-pain-points }

From the two extremes -- {{I-D.ietf-tls-8773bis}} where Russ kindly provided all requested inputs and we were able to get it through (with a [small change](https://mailarchive.ietf.org/arch/msg/tls/6Wk82oBGd61rTK23DgfYb7BmRKM/)) without any formal analysis to {{I-D.fossati-tls-attestation-08}} where formal analysis revealed vulnerabilities {{ID-Crisis}} and resulted in a separate WG to tackle this problem -- we summarize the pain points of the Verifier with the hope that we can refine the process.

Note that we are not at all asserting that the authors have no pain points. They very likely have their own -- that is another indication that the process needs a refinement.

## Provide Protection Against FATT-bypass by Other TLS-related WGs
TLS-related WGs in particular those where the representation of TLS WG is a minority -- including the one (SEAT WG) that the author has defended himself as one of the six proponents -- MUST NOT be allowed to make changes to the TLS protocol beyond what is explicitly allowed in their charter.

If rechartering of such WGs is *absolutely unavoidable* and includes non-trivial changes to the TLS protocol, it MUST only be done after agreement with the TLS WG. This will prevent the short-circuit path for FATT. If the WG does not have proper FATT-like process, TLS WG may request FATT review before WGLC.

In short, our concern is:

~~~
What's the point of such a TLS FATT process when other WGs
can simply bypass this process to make key schedule level changes?
~~~

For example, {{I-D.fossati-seat-early-attestation-00}} makes key schedule level changes, breaks the SEAT WG charter and SEAT WG has no formal FATT-like process.

## Process not being followed

The process {{TLS-FATT}} states:

{:quote}
>  When a document is adopted by the working group the chairs will make a determination whether the change proposed by the document requires review by the FATT to determine if formal protocol analysis is necessary for the change. For example a proposal that modifies the TLS key schedule or the authentication process or any other part of the cryptographic protocol that has been formally modeled and analyzed in the past would likely result in asking the FATT, whereas a change such as modifying the SSLKEYLOG format would not. The working group chairs will inform the working group of this decision.

However, such information has not been provided to the WG for at least the following 2 documents:

### ML-KEM
For the draft {{I-D.ietf-tls-mlkem}}, the [chairs acknowledge](https://mailarchive.ietf.org/arch/msg/tls/L2bWqpT3q8HVmACwD1Ta3NFimw0/) that the process was not followed:

{:quote}
>  Unfortunately, the chairs did not announce this decision on the list (this is something that should be corrected in the process).

However:

~~~
It remains unclear what exactly "corrected in the process" entails.
~~~

[The chairs further say](https://mailarchive.ietf.org/arch/msg/tls/L2bWqpT3q8HVmACwD1Ta3NFimw0/) :

{:quote}
>  The chairs made this decision because the mechanism in this draft fits into a well defined place in the TLS protocol and does not change the protocol itself.

We believe this argument does not stand, given the single data point that has gone through the FATT process -- {{RFC8773bis}}. Both of the mentioned conditions apply equally to {{RFC8773bis}} which indeed went through FATT process. The mechanism defined in {{RFC8773bis}} "fits into a well defined place in the TLS protocol" and "did not change the protocol itself". So we request clarification of the matter in comparison to {{RFC8773bis}}.

~~~
We believe the security considerations of {{I-D.ietf-tls-mlkem}} are
insufficient. We also believe FATT review could have significantly
improved it, including but not limited to the key reuse ambiguity.
We have provided significant feedback during the two WGLCs. However,
almost none of that is actually reflected in the updated editor's
version.
~~~

### Key Update

The process {{TLS-FATT}} states:

{:quote}
>  The output of the FATT is posted to the working group by the FATT point person.

Based on [authors' email](https://mailarchive.ietf.org/arch/msg/tls/KFUD3FPcrUlJmnXSyb3s25UFbdo/), while it is great that FATT could find some threat, in our observation, the FATT process does not seem to be followed in spirit.


## Contacting FATT
The FATT process restricts the Verifier from contacting the FATT directly.
We argue that the Verifier should be allowed to contact the FATT (at least the FATT person for a specific draft) because of the following reasons:

* Formal methods community is small and within this small community, those with deep knowledge of TLS are quite limited.

~~~
Such a restriction would not have been there if the Verifier
were not a member of the TLS WG and analyzing the same draft
and free to contact the same FATT for advice. Being a member
of the TLS WG actually puts the Verifier at unnecessary disadvantage.
~~~

* The feedback we receive on the list is really limited.

* Communication via chairs is a source of misunderstandings, as it has already happened with the chairs summarizing the intent of "Tamarin-like" to just "Tamarin".

## Understanding the Opposing Goals
The authors need to understand that the task of the Verifier is to find the subtle corner cases where the protocol may fail.
This is naturally opposed to the goal of the authors -- that is, to convince the WG that the protocol is good enough to be adopted/published.

~~~
Unless the Verifier remains really focused on checking subtleties,
there is little value of formal analysis.
~~~

In particular, some topics like remote attestation need more precise specifications because small changes or ambiguites may make a big difference.

[comment]: <> (We also argue that in the current process, the stakeholder at most disadvantage is . We all have a shared goal of producing high-quality specifications.)

## Response within reasonable time frame
If authors do not respond to our questions within a reasonable time frame, we may not pursue formal analysis of their draft.

## Slots at Meeting

~~~
Formal analysis -- just like any other code development -- is an
iterative process and needs to be progressively discussed with
the WG (and not just authors!) to be able to propose secure
solutions.
~~~

So at least some time should be allocated in the meetings for discussion of formal analysis.

* If the authors are doing the formal analysis themselves, they should also present the current state of formal analysis for discussion. This will help the Verifier give any feedback and avoid any repititive effort.

[comment]: <> (The goal of authors of Internet-Draft is to ...)

# Proposed solutions
In addition to those mentioned inline in the previous section, we propose the following:

  * The process should be as transparent to the WG as possible.
   * It should be the **WG** (and not the chairs) that deems whether some FATT analysis is
   required. At the very least, WG should be given the right to argue against the decision of the
    chairs regarding whether FATT analysis is required. We believe the opinions of those who are doing the
    formal analysis of the drafts of the WG, OR actively contributing to it, OR have done formal analysis
   in the past, OR have reasonably good knowledge of it, OR have relevant expertise should be heard.
   * Surely not every draft needs to go to FATT but the controversial
    ones do need to go to FATT, regardless of the nature of the draft
    and whatever the chairs believe (As a reminder, 'nothing required'
    is a perfectly valid outcome of initial FATT review.)

   * Be more explicit on:
      * what is the scope of FATT?
      * what kind of drafts need FATT review and why?

# Responsibilities of Authors
{: #sec-res-authors }

This document proposes that the authors provide the following four items:

## Motivation
The motivation of the work (i.e., the proposed extension of TLS) needs to primarily come from the authors.
The Verifier can ask questions to improve it, but he cannot just cook it up.

## Threat Model
A threat model outlines the assumptions and known weaknesses of the proposed protocol. The threat model could be the classical Dolev-Yao adversary. In addition, it could specify any keys (e.g., long-term keys or session keys) which may be compromised (i.e., available to the adversary).

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. should be outlined in the Internet-Draft.
If the informal security goals are not spelled out in the Internet-Draft, it is safe to assume that the goals are still unclear to the authors.

[section]: <> (In such a case, the Internet-Draft should not be considered as ready for adoption. These goals could be part of the security considerations or the Appendix.)


## Protocol Diagram
A Protocol Diagram should clearly mention the initial knowledge of the protocol participants, e.g., which authentic public keys are known to the protocol participants at the start of the protocol. An example of a Protocol Diagram for {{I-D.fossati-tls-attestation-08}} is provided in Figure 5 in {{ID-Crisis}}.

# Document Structure
While the needs may differ for some drafts, we propose the following baseline template, with an example of {{I-D.wang-tls-service-affinity}}:

TODO: Currently it is almost a copy of the [guidance email](https://mailarchive.ietf.org/arch/msg/tls/LfIHs1OVwDKWmDuCEx0p8wP-KPs/) to the authors. We will add details in next version.

## Introduction
   * Problem statement: Say in general what the problem is.
   * For {{I-D.wang-tls-service-affinity}}, we believe this
      should *not* include CATS. Anyone unfamiliar with CATS should be
      able to understand your problem.

## Terminology
   * Define any terms not defined in RFC8446bis or point to other drafts from where the definition is used.

## Motivation and design rationale
   * We really like how Russ motivates the problem statement in {{I-D.ietf-tls-8773bis}}. Use it as a sample.
   * Here authors should address all the concerns from WG, including
      justification with compelling arguments and authentic references
      why authors think it should be done within TLS WG (and within handshake).
   * For {{I-D.wang-tls-service-affinity}}, authors could put CATS here as a motivational use case.

## Proposed solution (one or more sections)
   * Protocol design with Protocol Diagram: we work on the formal analysis of TLS 1.3 exclusively. Please contact someone else if your draft relates to older versions.

## Security considerations

### Threat model

### Desired security goals

As draft proceeds these desired security goals will become what the draft actually achieves.

### Other security implications/considerations

# Responsibilities of Verifier
{: #sec-res-verifier }

When the authors declare the version as ready for formal analysis, the Verifier takes the above inputs, performs the formal analysis, and brings the results back to the authors and the WG. Based on the analysis, the verifier may propose updates to the Security Considerations section or other sections of the Internet-Draft.

[comment]: <> (This most likely needs some coordination with the authors.)

# Security Considerations

The whole document is about improving security considerations.

Like all security proofs, formal analysis is only as strong as its assumptions and model. The scope is typically limited, and the model does not necessarily capture real-world deployment complexity, implementation details, operational constraints, or misuse scenarios. Formal methods should be used as complementary and not as subtitute of other analysis methods.


# IANA Considerations

This document has no IANA actions.


--- back

# Appendix
{:unnumbered}

## Document History
{:unnumbered}

-03

* Limitations of formal analysis

-02

* Added document structure
* FATT-bypass by Other TLS-related WGs
* FATT process not being followed

-01

* Pain points of Verifier {{sec-prot-diagram}}
* Small adjustment of phrasing

# Acknowledgments
{:numbered="false"}
We thankfully acknowledge Eric Rescorla and John Mattsson for their valuable input.
