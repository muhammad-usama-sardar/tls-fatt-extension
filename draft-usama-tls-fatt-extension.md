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
  I-D.ietf-tls-8773bis:
  I-D.fossati-seat-early-attestation-00:
  I-D.ietf-tls-mlkem:
  I-D.wang-tls-service-affinity:
  RFC2418:

--- abstract

This document applies only to non-trivial extensions of TLS, which require formal analysis. It proposes the authors specify a threat model and informal security goals in the Security Considerations section, as well as motivation and a protocol diagram in the draft.
We also briefly present a few pain points of the team doing the formal analysis which -- we believe -- require refining the process:

* Provide protection against FATT-bypass by other TLS-related WGs
* Contacting FATT
* ML-KEM
* Understanding the opposing goals
* Response within reasonable time frame

--- middle

# Introduction
While the TLS FATT process {{TLS-FATT}} marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group (WG) process, the current FATT process has some practical limitations. Given a relatively smaller formal methods community, and a steep learning curve as well as very low consideration of usability in the existing formal analysis tools, this document proposes some solutions to make the FATT process sustainable.

Specifically, the TLS FATT process does not outline the division of formal analysis work between the authors and the WG members doing the formal analysis (the latter is hereafter referred to as the "Verifier" for convenience). This document aims to propose some solutions without putting an extensive burden on either party.

An argument is often presented by the authors that an Internet-Draft is written for the implementers. We make several counter-arguments here:

* Researchers and protocol designers are also stakeholders of such specifications {{I-D.irtf-cfrg-cryptography-specification}}.
* Even implementers may like to understand the security implications before blindly starting to implement it.
* With the FATT process, this argument is clearly invalid. The Verifier may not be an implementer.

This document outlines the corresponding changes in the way Internet-Drafts are typically written.
For the Internet-Draft to be useful for the formal analysis, this document proposes that the draft should contain four main items, namely:

* motivation,
* a threat model,
* informal security goals, and
* a protocol diagram ({{sec-prot-diagram}}).

Each one of these is summarized in {{sec-res-authors}}. Future versions of this draft will include concrete examples.

Expected contributions of the Verifier are summarized in {{sec-res-verifier}}.

## Motivation
A clear separation of expected contributions would help IRTF UFMRG to train the authors and Verifiers separately to fulfill their own formal analysis work.

Moreover, we believe that the experiences can help improve the FATT process. The goal is to document the identified gaps with concrete examples, discuss those and mutually find the best way forward.

## Scope
The scope of this document is only non-trivial extensions of TLS, which require formal analysis.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Protocol Diagram
{: #sec-prot-diagram }

In the context of this document, a Protocol Diagram specifies the proposed cryptographically-relevant changes compared to the standard TLS protocol {{I-D.ietf-tls-rfc8446bis}}. This is conceptually similar to the Protocol Model in {{RFC4101}}. However, while {{RFC4101}} only recommends diagrams, we consider diagrams to be essential.

## Verifier
In this document, the Verifier refers to the **WG members** doing the formal analysis.
Note that it is **NOT** a new formal role in the WG process.

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

## Contacting FATT
According to FATT process {{TLS-FATT}}, FATT is a 'design team' as per {{RFC2418}} (also see [this](https://datatracker.ietf.org/doc/statement-iesg-on-design-teams-20011221/)).

The FATT process restricts the WG members -- except for **authors** -- from contacting the FATT directly.
This creates an unjustified situation where the authors have an **exclusive** access to FATT.
We argue that WG members -- including the Verifier -- should also be allowed to contact the FATT because of the following reasons:

* Formal methods community is small and within this small community, those with deep knowledge of TLS are quite limited.

~~~
Such a restriction would not have been there if the Verifier
were not a member of the TLS WG and analyzing the same draft
and free to contact the same FATT for advice. Being a member
of the TLS WG actually puts the Verifier at unnecessary disadvantage.
~~~

* The feedback we receive on the list is really limited.

* Communication via chairs is a source of misunderstandings, as it has already happened with the chairs summarizing the intent of "Tamarin-like" to just "Tamarin".

Our proposed solution for this point is in {{sec-contact-fatt}}.

## ML-KEM
{: #sec-ml-kem }

~~~
We believe the security considerations of {{I-D.ietf-tls-mlkem}} are
insufficient. We also believe FATT review could have significantly
improved it, including but not limited to the preference of hybrids.
We have provided significant feedback during the two WGLCs. However,
almost none of that is actually reflected in the updated editor's
version.
~~~

Our proposed solution for this point is in {{sec-sol-ml-kem}}.

### Formal analysis (Work-in-progress)
We have presented observation from our ongoing symbolic security analysis
(cf. limitations in {{sec-sec-cons}}) using ProVerif on the mailing list.

We argue that in general:

1. Migration from ECDHE to hybrid is security improvement.
2. Migration from hybrid to non-hybrid ML-KEM is security regression.


#### Hybrid PQ/T

More formally, the property hybrid PQ/T should provide is:

~~~
Hybrid PQ/T is secure unless both ECDHE and ML-KEM are broken.
~~~

Hybrid preserves ECDHE, and adds ML-KEM as an additional factor. So as
long as one of them is not broken, the system is secure. In particular, even if ML-KEM is
completely broken, the system retains the security level of ECDHE.

#### Non-hybrid PQ

On the other hand, the formal property non-hybrid PQ provides is:

~~~
Non-hybrid PQ is secure unless ML-KEM is broken.
~~~

If ML-KEM is broken, the whole system is broken.

#### Comparison
Leak out the ECDHE key from hybrid PQ/T and you get a non-hybrid ML-KEM. Clearly, hybrid is
in general more secure, unless ECDHE is fully broken, in which case it still falls
equivalent to non-hybrid ML-KEM, or in the hypothetical scenario that there is an implementation
bug in the ECDHE part which is triggered only in composition.


### "Cost"
"Cost" has been presented on the list as the motivation for ML-KEM but no authentic reference has yet been presented. There seems to be a need for a thorough study to understand the "cost."


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
If authors do not respond to the Verifier's questions within a reasonable time frame (say a few weeks but not months), the Verifier may not pursue formal analysis of their draft.


[comment]: <> (The goal of authors of Internet-Draft is to ...)

# Proposed solutions
In addition to those mentioned inline in the previous section, we propose the following:

## Contacting FATT: Separate List for FATT and WG members
{: #sec-contact-fatt }

We propose creating a public mailing list (something like tls-fatt) for discussions between interested WG members and FATT.

In our understanding, the idea -- in a nutshell -- is something like **hybrid** design team, i.e.,:

* FATT continues to use whatever they currently use for their internal communication ("closed")
* The proposed list additionally allows public FATT-WG engagement ("open") for questions and discussion of WG members or FATT


### Potential need of FATT-WG engagement

In addition to the questions from the WG for the FATT, FATT also needs to engage with the WG:

* At **initial** FATT review (just after adoption), FATT may have questions from authors as well as Verifiers. For the former, to understand better the threat model and desired security goals, etc. to be able to suggest which approach is best-suited. For the latter, to better understand what formal analysis approach and tool is being planned/currently used (if any).
* During **final** FATT review (just before WGLC), FATT may have questions on what the Verifier has done, especially in cases where a peer-reviewed publication is not yet available. We believe evaluating someone else's code is not easy, or at least if FATT has the opportunity to talk to the Verifier, it will decrease the brain cycles that they will have to spend on it.

### Design goals

* **minimal process change**: some private discussions typically happen between authors and FATT; move them to public list for transparency. Keep intra-FATT communication private as it is.
* **balanced workload**: not to increase anyone's workload on average over a finite period of time (say lifetime of one document): joining list is voluntary; responding to list questions is voluntary
* **all stakeholders benefit**: ensure all stakeholders (FATT, authors, WG members, chairs) benefit compared to current process

### Benefits
In addition to transparency where this removes the current situation where only the authors have an exclusive access to FATT, we think the proposal has merits where all stakeholders benefit:

* **Chairs** get relief from carrying messages back and forth between WG and FATT.
* **FATT** gets involved early in the process and has to do lesser work later on (e.g., checking artifacts before WGLC).
* **Interested WG members** get a direct contact with experts.
* **Uninterested WG members** get lesser noise on TLS list. They can check the public archives by searching for a specific draft if they would like to.

### Risks

* We acknowledge the risk of '**no response from FATT**' identified on list. In such cases, WG can continue with its best judgement based on its understanding of the available literature.

### Open questions

Opinion of FATT is critical in this proposal whether the middle ground of hybrid is acceptable to (some of) them.

## ML-KEM: FATT review
{: #sec-sol-ml-kem }

We have formally requested the chairs to initiate the FATT process for {{I-D.ietf-tls-mlkem}}.
See [this](https://mailarchive.ietf.org/arch/msg/tls/rClgrWm2hnhESXHx56U8InbwQQs/) and [this](https://mailarchive.ietf.org/arch/msg/tls/7lj6fYAweMBwNMxFerNl7xhY0pk/).

We believe formal methods can provide additional value for security considerations of this draft in order to maintain the high cryptographic assurance of TLS.

* As an example, it can help justify design choices, such as the preference for hybrids.
It can also help identify ways in which ML-KEM can break.
* As a relevant data point in the context of standardization, LAKE WG has done formal analysis for EDHOC-PSK with KEM ([ref](https://mailarchive.ietf.org/arch/msg/lake/2XGOI9OCwylJUfSCasvvwM2FXmw/)).


## Scope of FATT
   * Be more explicit on:
      * what is the scope of FATT?
      * what kind of drafts need FATT review and why?
Discussion on this is happening in [issue 19](https://github.com/tlswg/tls-fatt/issues/19).

## Discussion at Meeting
{: #sec-discuss-meetings }


~~~
Formal analysis -- just like any other code development -- is an
iterative process and needs to be progressively discussed with
the WG (and not just authors!) to be able to propose secure
solutions.
~~~

So at least some time should be allocated in the meetings for discussion of formal analysis.

If the authors are doing the formal analysis themselves, it would be helpful to also present the current state of formal analysis in meetings for discussion. This may be a single slide describing:

* Approach used: symbolic or computational
* Tool used: ProVerif, CryptoVerif etc.
* Properties established

This will help the WG give any feedback and avoid other Verifiers doing redundant effort using potentially same tools.


# Contribution of Authors
{: #sec-res-authors }

The following contributions are expected from the authors:

## Real Motivation
Authors are expected to provide the real motivation of the work (i.e., the proposed extension of TLS).
The Verifier can then ask questions to improve it.

## Threat Model
{: #sec-th-model }

A threat model identifies which threats are in scope for the protocol design. So it should answer questions like:

* What are the capabilities of the adversary? What can the adversary do?
* Whether post-quantum threats are in scope?
* What can go wrong in the system? etc.

### Typical Dolev-Yao adversary
A typical threat model assumes the classical Dolev-Yao adversary, who has full control over the communication channel.

Any additional adversary capabilities and assumptions must be explicitly stated.

### Potential Weaknesses of Cryptographic Primitives
In general, it also outlines the potential weaknesses of the cryptographic primitives used in the proposed protocol extension. Examples include:

* weak hash functions
* weak Diffie-Hellman (DH) groups
* weak elements within strong DH groups

### Keys
This section should specify any keys in the system (e.g., long-term keys of the server) in addition to the standard TLS key schedule. Theoretically and arguably practically, any key may be compromised (i.e., become available to the adversary).

For readability, we propose defining each key clearly as in Section 4.1 of {{ID-Crisis}}. Alternatively, present as a table with the following entries for each key:

* Name (or symbol) of the key
* Purpose of the key
* (optionally but preferably -- particularly when the endpoint is not fully trusted) Which software in the system has access to the key?

If more than one servers are involved (such as migration cases), the keys for servers should be distinguished in an unambiguous way.

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. should be outlined in the Internet-Draft.
If the informal security goals are not spelled out in the Internet-Draft, it is safe to assume that the goals are still unclear to the authors.

[section]: <> (In such a case, the Internet-Draft should not be considered as ready for adoption. These goals could be part of the security considerations or the Appendix.)

Examples:

* Integrity of message X holds unless some key Y is leaked.
* (stated differently) Integrity of message X holds as long as some key Y is protected.
* Freshness of message X holds unless some key Y or some key Z is leaked.
* Server Authentication holds unless some key Y or some key Z is leaked.

See Section 5.1 of {{ID-Crisis}} for concrete examples.

## Protocol Diagram
A Protocol Diagram should clearly mention the initial knowledge of the protocol participants, e.g., which authentic public keys are known to the protocol participants at the start of the protocol. An example of a Protocol Diagram for {{I-D.fossati-tls-attestation-08}} is provided in Figure 5 in {{ID-Crisis}}.

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

# Contribution of Verifier
{: #sec-res-verifier }

When the authors declare the version as ready for formal analysis, the Verifier takes the above inputs, performs the formal analysis, and brings the results back to the authors and the WG. Based on the analysis, the verifier may propose updates to the Security Considerations section or other sections of the Internet-Draft.

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
* Helpful discussions on formal analysis in meetings in {{sec-discuss-meetings}}
* Pointer to formal analysis and costs in {{sec-ml-kem}}

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

* Eric Rescorla for review of -02 and -05. Not all the feedback has yet been applied.
* John Mattsson for proposing text for security considerations.
* S. Moonesamy for identifying the 'no response' risk in the proposal for new list.

The research work is funded by German Research Foundation ("Deutsche Forschungsgemeinschaft.")
