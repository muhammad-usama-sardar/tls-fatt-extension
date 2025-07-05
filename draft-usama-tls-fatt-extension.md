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

...

--- abstract

While the TLS FATT process marks a historic change in achieving high cryptographic assurances by tightly integrating formal methods in the working group process, the current FATT process has some practical limitations. Given a relatively smaller formal methods community, and a steep learning curve as well as very low consideration of usability in the existing security analysis tools, this document proposes some solutions to make the FATT process sustainable. This document applies only to non-trivial extensions of TLS, which require formal analysis.


--- middle

# Introduction
The FATT process does not outline the division of responsibility between the authors and the one doing the formal analysis (the latter is hereafter referred to as the "verifier"). This document aims to fill this gap without putting an extensive burden on either party. This document also outlines the corresponding changes in the way Internet-Drafts are typically written.

An argument is often presented by the authors that an Internet-Draft is written for the implementers. With the FATT process, this argument is no longer valid. For the Internet-Draft to be useful for the formal analysis, it should contain three main items, namely a threat model, informal security goals, and a protocol diagram highlighting the proposed changes to the standard TLS protocol. Each one of these is summarized in the following sections.

[comment]: <> (The goal of authors of Internet-Draft is to ...)

# Responsibilities of Authors

## Threat Model
A threat model outlines the assumptions and known weaknesses of the proposed protocol. The threat model could be the classical Dolev-Yao adversary. In addition, it could specify any keys which are assumed to be available to the adversary.

## Informal Security Goals
Knowing what you want is the first step toward achieving it. Hence, informal security goals such as integrity, authentication, freshness, etc. should be outlined in the Internet-Draft. These goals could be part of the security considerations or the Appendix.
If the informal security goals are not spelled out in the Internet-Draft, it is safe to assume that the goals are still unclear to the authors. In such a case, the Internet-Draft should not be considered as ready for adoption.

## Protocol Diagram
A protocol diagram highlights the proposed changes compared to the standard TLS protocol.

# Responsibilities of Verifier
When the authors declare the version as ready for formal analysis, the verifier takes the above inputs, performs the formal analysis, and brings the results back to the authors and the working group.

[comment]: <> (This most likely needs some coordination with the authors.)

# Definition of Attack
Any possible ambiguity is to considered as an attack. The authors are, therefore, encouraged to be as precise as possible.

# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

The whole document is about security considerations.


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
