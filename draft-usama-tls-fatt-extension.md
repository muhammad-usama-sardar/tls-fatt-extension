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
    organization: Stevens Institute of Technology
    city: New York
    country: USA
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
  Foreshadow:
     title: "Foreshadow"
     date: October 2025,
     target: https://foreshadowattack.eu/
     author:
      - ins: Jo Van Bulck
      - ins: Marina Minkin
      - ins: Ofir Weisse
      - ins: Daniel Genkin
      - ins: Baris Kasikci
      - ins: Frank Piessens
      - ins: Mark Silberstein
      - ins: Thomas F. Wenisch
      - ins: Yuval Yarom
      - ins: Raoul Strackx
  I-D.irtf-cfrg-cryptography-specification:
  RA-TLS:
    title: "Towards Validation of TLS 1.3 Formal Model and Vulnerabilities in Intel's RA-TLS Protocol"
    date: 13 November 2024,
    target: https://www.researchgate.net/publication/385384309_Towards_Validation_of_TLS_13_Formal_Model_and_Vulnerabilities_in_Intel's_RA-TLS_Protocol
    author:
      - ins: M. U. Sardar
      - ins: A. Niemi
      - ins: H. Tschofenig
      - ins: T. Fossati
  ID-Crisis: DOI.10.1145/3779208.3785387
  ID-Crisis-repo:
    title: "Identity Crisis in Confidential Computing: Formal Analysis of Attested TLS"
    date: November 2025,
    target: https://github.com/CCC-Attestation/formal-spec-id-crisis
    author:
      - ins: M. U. Sardar
      - ins: M. Moustafa
      - ins: T. Aura
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
  CVE-2026-33697:
     author:
        org: CVE
     title: CoCoS attested TLS is vulnerable to relay attacks via extracted ephemeral TLS keys
     target: https://www.cve.org/CVERecord?id=CVE-2026-33697
     date: March 2026
  RA-TLS: DOI.10.1109/ACCESS.2024.3497184
  Usama-TLS-26Feb25:
     title: "Impersonation attacks on protocol in draft-fossati-tls-attestation (Identity crisis in Attested TLS) for Confidential Computing"
     date: 26 February 2025,
     target: https://mailarchive.ietf.org/arch/msg/tls/Jx_yPoYWMIKaqXmPsytKZBDq23o/
     author:
      - ins: Muhammad Usama Sardar
  I-D.ietf-tls-rfc8446bis:
  RFC9261: rfc9261
  RFC9266: rfc9266
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
    date: July 2026,
    target: https://github.com/muhammad-usama-sardar/intra-handshake.fail
    author:
      - ins: M. U. Sardar
      - ins: V. Dubeyko
      - ins: J-M. Jacquet
  CVE-2026-33697:
     author:
        org: CVE
     title: CoCoS attested TLS is vulnerable to relay attacks via extracted ephemeral TLS keys
     target: https://www.cve.org/CVERecord?id=CVE-2026-33697
     date: 26 March 2026
  EUVD-2026-16488:
     author:
        org: ENISA
     title: CoCoS attested TLS is vulnerable to relay attacks via extracted ephemeral TLS keys
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-16488
     date: 26 March 2026
  CVE-2026-92701:
     author:
        org: CVE
     title: Cocos AI Intra-handshake attested TLS implementation is vulnerable to session-misbinding attacks for Intel TDX verifier path
     target: https://www.cve.org/CVERecord?id=CVE-2026-92701
     date: 18 Sept 2026
  CVE-2026-92702:
     author:
        org: CVE
     title: Cocos AI Intra-handshake attested TLS implementation can accept Evidence with nil, empty, or omitted reportData in the AMD SEV-SNP path
     target: https://www.cve.org/CVERecord?id=CVE-2026-92702
     date: 18 Sept 2026
  CVE-2026-108265:
     author:
        org: CVE
     title: CVE-2026-108265
     target: https://www.cve.org/CVERecord?id=CVE-2026-108265
     date: 9 Oct 2026
  CVE-2026-108266:
     author:
        org: CVE
     title: CVE-2026-108266
     target: https://www.cve.org/CVERecord?id=CVE-2026-108266
     date: 9 Oct 2026
  CVE-2026-108267:
     author:
        org: CVE
     title: CVE-2026-108267
     target: https://www.cve.org/CVERecord?id=CVE-2026-108267
     date: 9 Oct 2026
  CVE-2026-108268:
     author:
        org: CVE
     title: CVE-2026-108268
     target: https://www.cve.org/CVERecord?id=CVE-2026-108268
     date: 9 Oct 2026
  CVE-2026-108269:
     author:
        org: CVE
     title: CVE-2026-108269
     target: https://www.cve.org/CVERecord?id=CVE-2026-108269
     date: 9 Oct 2026
  EUVD-2026-83194:
     author:
        org: ENISA
     title: EUVD-2026-83194
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-83194
     date: 18 Sept 2026
  EUVD-2026-83192:
     author:
        org: ENISA
     title: EUVD-2026-83192
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-83192
     date: 18 Sept 2026
  GHSA-Cocos-AI:
    title: "CoCoS attested TLS is vulnerable to relay attacks via extracted ephemeral TLS keys"
    date: 23 March 2026
    target: https://github.com/ultravioletrs/cocos/security/advisories/GHSA-vfgg-mvxx-mgg7
    author:
      - ins: Ultraviolet Cocos AI
  GHSA-Cocos-AI2:
    title: "Cocos AI intra-handshake attested TLS implementation is vulnerable to session-misbinding attacks for Intel TDX verifier path"
    date: 16 August 2026
    target: https://github.com/ultravioletrs/cocos/security/advisories/GHSA-4px3-wj2x-xx47
    author:
      - ins: Ultraviolet Cocos AI
  GHSA-Cocos-AI3:
    title: "Cocos AI intra-handshake attested TLS implementation can accept Evidence with nil, empty, or omitted reportData in the AMD SEV-SNP path"
    date: 16 August 2026
    target: https://github.com/ultravioletrs/cocos/security/advisories/GHSA-4r6g-mp48-j2rw
    author:
      - ins: Ultraviolet Cocos AI
  GHSA-Edgeless-Systems:
    title: "Remote attestation is susceptible to relay attacks"
    date: August 2026
    target: https://github.com/edgelesssys/contrast/security/advisories/GHSA-hjgc-jc5v-fw7h
    author:
      - ins: Edgeless Systems
  GHSA-Edgeless-Systems2:
    title: "Generated policies don't detect all image substitutions"
    date: August 2026
    target: https://github.com/edgelesssys/contrast/security/advisories/GHSA-m2qg-wrxv-h898
    author:
      - ins: Edgeless Systems
  GHSA-Edgeless-Systems3:
    title: "Existing Mesh CA key can cross manifest boundaries during Contrast peer recovery"
    date: September 2026
    target: https://github.com/edgelesssys/contrast/security/advisories/GHSA-rxcv-p3px-m3c3
    author:
      - ins: Edgeless Systems
  GHSA-Edgeless-Systems4:
    title: "Node installer leaves the host containerd configuration world-writable (0666), allowing local privilege escalation"
    date: September 2026
    target: https://github.com/edgelesssys/contrast/security/advisories/GHSA-376m-h37w-4rvq
    author:
      - ins: Edgeless Systems
  GHSA-Edgeless-Systems5:
    title: "Contrast before 1.16.0 is susceptible to remote attestation relay attacks"
    date: August 2026
    target: https://github.com/advisories/GHSA-jw33-f4wc-8736
    author:
      - ins: Edgeless Systems
  SEAT-vulnerability-report:
    title: "Relay Attacks in Intra-handshake Attestation for Confidential Agentic AI Systems"
    date: 11 Jan 2026,
    target: https://mailarchive.ietf.org/arch/msg/seat/x3eQxFjQFJLceae6l4_NgXnmsDY/
    author:
      - ins: M. U. Sardar
  GHSA-Privasys-rustls:
    title: "Privasys RA-TLS challenge mode did not bind attestation evidence to the TLS session"
    date: 3 September 2026
    target: https://github.com/Privasys/rustls/security/advisories/GHSA-j6qv-435v-r492
    author:
      - ins: Privasys
  GHSA-Privasys-go:
    title: "Privasys Go fork: RA-TLS challenge mode did not bind attestation evidence to the TLS session"
    date: 3 September 2026
    target: https://github.com/Privasys/go/security/advisories/GHSA-7jfw-53rm-phh2
    author:
      - ins: Privasys
  GHSA-Privasys-eov:
    title: "enclave-os-virtual: RA-TLS challenge certificates were not bound to the TLS session"
    date: 3 September 2026
    target: https://github.com/Privasys/enclave-os-virtual/security/advisories/GHSA-p5fp-g94g-g9m9
    author:
      - ins: Privasys
  GHSA-Privasys-eom:
    title: "enclave-os-mini: RA-TLS challenge certificates were not bound to the TLS session"
    date: 3 September 2026
    target: https://github.com/Privasys/enclave-os-mini/security/advisories/GHSA-49qm-4pj3-w2c6
    author:
      - ins: Privasys
  GHSA-Privasys-rtc:
    title: "ra-tls-clients: RA-TLS challenge verifier accepted quotes not bound to the TLS session"
    date: 3 September 2026
    target: https://github.com/Privasys/ra-tls-clients/security/advisories/GHSA-5qrc-v874-mxvx
    author:
      - ins: Privasys
  GHSA-Privasys-rtc-da:
    title: "Privasys Intra-handshake attested TLS implementation is vulnerable to Diversion Attacks"
    date: 6 September 2026
    target: https://github.com/Privasys/ra-tls-clients/security/advisories/GHSA-pj2x-5wqv-fh57
    author:
      - ins: Privasys
  GHSA-Privasys-rtc-tcu:
    title: "Privasys Intra-handshake attested TLS implementation is vulnerable to TOCTOU Attacks"
    date: 6 September 2026
    target: https://github.com/Privasys/ra-tls-clients/security/advisories/GHSA-gg8q-mfhh-wrrc
    author:
      - ins: Privasys
  GHSA-Cocos-AI4:
    title: "Cocos Intra-handshake attested TLS implementation is vulnerable to Diversion Attacks"
    date: 25 September 2026
    target: https://github.com/ultravioletrs/cocos/security/advisories/GHSA-v5m8-5wxc-vjgp
    author:
      - ins: Ultraviolet Cocos AI
  GHSA-Cocos-AI5:
    title: "Cocos AI Intra-handshake attested TLS implementation is vulnerable to TOCTOU Attacks"
    date: 25 September 2026
    target: https://github.com/ultravioletrs/cocos/security/advisories/GHSA-ghwv-vrp2-2975
    author:
      - ins: Ultraviolet Cocos AI
  ID-Crisis: DOI.10.1145/3779208.3785387
  ID-Crisis-repo:
    title: "Identity Crisis in Confidential Computing: Formal Analysis of Attested TLS"
    date: November 2025,
    target: https://github.com/CCC-Attestation/formal-spec-id-crisis
    author:
      - ins: M. U. Sardar
      - ins: M. Moustafa
      - ins: T. Aura
  refTLS: DOI.10.1109/SP.2017.26
  TLS-RA:
    title: "Separate but together: integrating remote attestation into TLS"
    date: July 2025,
    target: https://www.usenix.org/conference/atc25/presentation/weinhold
    author:
      - ins: Carsten Weinhold
      - ins: M. U. Sardar
      - ins: Ionuț Mihalcea
      - ins: Yogesh Deshpande
      - ins: Hannes Tschofenig
      - ins: Yaron Sheffer
      - ins: Thomas Fossati
      - ins: Michael Roitzsch
  CSA-eBPF:
    title: "MITRE's New Framework: Securing the eBPF Layer Your AI Depends On"
    date: 9 September 2026
    target: https://cloudsecurityalliance.org/blog/2026/09/09/mitre-s-new-framework-securing-the-ebpf-layer-your-ai-depends-on
    author:
      - ins: Cloud Security Alliance
  MITRE-Continuous-Attestation:
    title: "Framework for Continuous Remote Attestation"
    date: 16 July 2026
    target: https://www.mitre.org/news-insights/publication/framework-continuous-remote-attestation
    author:
      - ins: MITRE's Confidential Computing Layered Attestation Working Group
  EarlyAttestationBleed:
    title: "EarlyAttestationBleed: Three Critical-severity Vulnerabilities of CVSS ≥ 9.0 in Confidential Computing"
    date: 21 September 2026,
    target: https://www.researchgate.net/publication/414529199_EarlyAttestationBleed_Three_Critical-severity_Vulnerabilities_of_CVSS_90_in_Confidential_Computing
    author:
      - ins: M. U. Sardar
      - ins: Songbo Bu
  CVE-2026-100835:
     author:
        org: CVE
     title: Contrast before 1.16.0 Remote Attestation Relay Attack
     target: https://www.cve.org/CVERecord?id=CVE-2026-100835
     date: 27 Sept 2026
  EUVD-2026-87851:
     author:
        org: ENISA
     title: EUVD-2026-87851
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-87851
     date: 27 Sept 2026
  CVE-2026-100833:
     author:
        org: CVE
     title: Contrast before 1.23.1 Image Substitution via Policy Generation
     target: https://www.cve.org/CVERecord?id=CVE-2026-100833
     date: 27 Sept 2026
  EUVD-2026-87851:
     author:
        org: ENISA
     title: EUVD-2026-87851
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-87851
     date: 27 Sept 2026
  GHSA-Edgeless-Systems6:
    title: "Contrast (edgelesssys/contrast) versions 1.14.0 before 1.23.1 generate runtime policies that fail to detect all container image substitutions."
    date: 27 Sept 2026
    target: https://github.com/advisories/GHSA-MJJ6-PX65-JQ92
    author:
      - ins: Edgeless Systems
  EUVD-2026-87853:
     author:
        org: ENISA
     title: EUVD-2026-87853
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-87853
     date: 27 Sept 2026
  CVE-2026-108362:
     author:
        org: CVE
     title: CVE-2026-108362
     target: https://www.cve.org/CVERecord?id=CVE-2026-108362
     date: 12 Oct 2026
  CVE-2026-108361:
     author:
        org: CVE
     title: CVE-2026-108361
     target: https://www.cve.org/CVERecord?id=CVE-2026-108361
     date: 12 Oct 2026
  CVE-2026-112377:
     author:
        org: CVE
     title: CVE-2026-112377
     target: https://www.cve.org/CVERecord?id=CVE-2026-112377
     date: 19 Oct 2026
  EUVD-2026-95996:
     author:
        org: ENISA
     title: EUVD-2026-95996
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-95996
     date: 9 Oct 2026
  EUVD-2026-95997:
     author:
        org: ENISA
     title: EUVD-2026-95997
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-95997
     date: 9 Oct 2026
  EUVD-2026-96017:
     author:
        org: ENISA
     title: EUVD-2026-96017
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-96017
     date: 9 Oct 2026
  EUVD-2026-96018:
     author:
        org: ENISA
     title: EUVD-2026-96018
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-96018
     date: 9 Oct 2026
  EUVD-2026-96019:
     author:
        org: ENISA
     title: EUVD-2026-96019
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-96019
     date: 9 Oct 2026
  EUVD-2026-97782:
     author:
        org: ENISA
     title: EUVD-2026-97782
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-97782
     date: 12 Oct 2026
  EUVD-2026-97781:
     author:
        org: ENISA
     title: EUVD-2026-97781
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-97781
     date: 12 Oct 2026
  EUVD-2026-104535:
     author:
        org: ENISA
     title: EUVD-2026-104535
     target: https://euvd.enisa.europa.eu/enisa/EUVD-2026-104535
     date: 19 Oct 2026



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


# Concrete CVEs

## Intra-handshake.fail
{{Intra-handshake.fail}} presents a general approach to analyze the intra-handshake (aka early) attestation proposals, regardless of whether they are within the scope of SEAT charter or not. From a security perspective, one of the key decision factors is the candidate binding mechanism. Some binding mechanisms are within scope of SEAT charter and others are not. The artifacts are available in {{Intra-handshake.fail-repo}} under Apache-2.0 license for reproducibility, extensibility, and further research.

- This work resulted in {{CVE-2026-33697}} of CVSS 7.5.

## ID-Crisis
A *complementary* paper {{ID-Crisis}} presents the identity crisis in pre- and intra-handshake attestation. The formal analysis is available in {{ID-Crisis-repo}} under Apache-2.0 license for reproducibility, extensibility, and further research.

## EarlyAttestationBleed
{{EarlyAttestationBleed}} presents a formal analysis together with regression tests of the broader attestation ecosystem and discovered three critical-severity vulnerabilities in implementations of early attestation:

- Ultraviolet Cocos AI in TDX path resulting in {{CVE-2026-92701}} of CVSS 9.1.
- Ultraviolet Cocos AI in AMD SEV-SNP path resulting in {{CVE-2026-92702}} of CVSS 9.1.
- Edgeless Systems Contrast in policies resulting in {{GHSA-Edgeless-Systems2}} of CVSS 9.0-10.0 and {{CVE-2026-100833}} of CVSS v3.1 of 9.6.

### Architectural Flaws in Early Attestation

Sec. 7 of {{EarlyAttestationBleed}} presents four architectural flaws in early attestation:

- Hardware-level Information of Server
- Only Boot-time Claims
- Re-attestation
- High Handshake Latency, Timeouts, and Failures


## EarlyAttestationTschüss (EAT)

- {{CVE-2026-100835}} of CVSS 9.1 against Edgeless Systems Contrast
- {{CVE-2026-112377}} of CVSS 9.1 against CCC Attestation SIG
- {{CVE-2026-108362}} of CVSS 9.1 against Privasys
- {{CVE-2026-108265}} of CVSS 9.1 against Privasys
- {{CVE-2026-108266}} of CVSS 9.1 against Privasys
- {{CVE-2026-108267}} of CVSS 9.1 against Privasys
- {{CVE-2026-108268}} of CVSS 9.1 against Privasys
- {{CVE-2026-108269}} of CVSS 9.1 against Privasys


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
