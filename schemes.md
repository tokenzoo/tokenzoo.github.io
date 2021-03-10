---
layout: default
title: Schemes
banner: bird.jpg
---
In this page we over the various proposed anonymous credential and token schemes.

We start with anonymous credentials schemes that have been specified and
implemented and hence we can get concrete performance figures out of them.

In the second part of the page we continue with anonymous credentials schemes
that are not implemented, are mainly in research stage, or can serve as a basis
for more complete systems.

### Privacy Pass [\[PDF\]](https://www.petsymposium.org/2018/files/papers/issue3/popets-2018-0026.pdf)

<details>
<summary markdown="span">Click for details</summary>

- [Website](https://privacypass.github.io/)
- Source code: [Client](https://github.com/privacypass/challenge-bypass-extension) & [Server](https://github.com/privacypass/challenge-bypass-server)
- Properties: Strong-unlinkability, Single-show
- Based on: [(V)OPRF]({{site.baseurl}}/primitives.html#oprfs)
</details>

### Signal Private Group System [\[PDF\]](https://eprint.iacr.org/2019/1416)

<details>
<summary markdown="span">Click for details</summary>

- [Implementation](https://github.com/signalapp/Signal-Android/tree/master/libsignal/service/src/main/java/org/whispersystems/signalservice/api/groupsv2)
- Properties: Multi-show, Public Attributes
- Based on: [KVAC]({{site.baseurl}}/primitives.html#kvac)
- Performance:
  - Credential Size: [493 bytes](https://youtu.be/4eKwlSqGUi4?list=PLeeS-3Ml-rpoVMNQkUrFDSfaTuUMxVtjy&t=2481)
  - Key size: TODO
  - Show size: TODO
  - Prover time: [2.16ms](https://youtu.be/4eKwlSqGUi4?list=PLeeS-3Ml-rpoVMNQkUrFDSfaTuUMxVtjy&t=2481)
  - Verifier time: [1.17ms](https://youtu.be/4eKwlSqGUi4?list=PLeeS-3Ml-rpoVMNQkUrFDSfaTuUMxVtjy&t=2481)
</details>

### Coconut [\[PDF\]](https://arxiv.org/pdf/1802.07344.pdf)

<details>
<summary markdown="span">Click for details</summary>
- [Implementation](https://github.com/asonnino/coconut) and [another implementation](https://gitlab.com/narodnik/darkwallet/-/tree/master/src/coconut)
- Properties: Public Verifiability, Multi-show, Public/Private Attributes, Threshold Issuance
- Based on: [PS signatures]({{site.baseurl}}/primitives.html#ps-signatures) & BGLS Signatures & Waters Signatures
- Performance:
  - Credential Size: [132 bytes](https://sheharbano.com/assets/talks/talk_coconut.pdf)
  - Key size: TODO
  - Show size: [355 bytes](https://sheharbano.com/assets/talks/talk_coconut.pdf)
  - Prover time: [3.35 ms](https://sheharbano.com/assets/talks/talk_coconut.pdf)
  - Verifier time: [10.49 ms](https://sheharbano.com/assets/talks/talk_coconut.pdf)
</details>

### Idemix [\[PDF\]](https://www.cise.ufl.edu/~nemo/anonymity/papers/idemix.pdf)

<details>
<summary markdown="span">Click for details</summary>
- [Implementation](prime.inf.tu-dresden.de/idemix/)
- Properties: Constant Credential Size, Multi-show
- Based on: [CL03]({{site.baseurl}}/schemes.html#cl03)
</details>

[Idemix]: https://idemix.wordpress.com/

### Facebook's Blind Signatures

<details>
<summary markdown="span">Click for details</summary>
- [Implementation](https://github.com/siyengar/private-fraud-prevention)
- Properties: Public Verifiability
- Based on: [Blind RSA]({{site.baseurl}}/primitives.html#blind-rsa)
</details>

### Facebook's PrivateStats

<details>
<summary markdown="span">Click for details</summary>
- [Implementation](https://research.fb.com/wp-content/uploads/2021/01/PrivateStats-De-Identified-Authenticated-Logging-at-Scale_final.pdf)
- Properties: Single-show, Public Attributes
- Based on:
  - [(V)OPRF]({{site.baseurl}}/primitives.html#oprfs)
</details>

### U-Prove [\[PDF\]](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/U-Prove20Cryptographic20Specification20V1.1.pdf)

<details>
<summary markdown="span">Click for details</summary>
- [U-Prove implementation](https://github.com/Microsoft/uprove-csharp-sdk)
- Properties: Single-show, Public Attributes
- Based on: [Brand's blind signature]({{site.baseurl}}/primitives.html#brands-blind-signature)
- Notes: The U-Prove token is single-show, but can be shown multiple times to serve as a pseudonym.
</details>

### Tor Anonymous Res Tokens

<details>
<summary markdown="span">Click for details</summary>
- [Tor summary](https://blog.torproject.org/stop-the-onion-denial) and [proposed specification](https://lists.torproject.org/pipermail/tor-dev/2021-February/014517.html)
- Properties: Single-show
- Based on: [Blind RSA]({{site.baseurl}}/primitives.html#blindsigs)
</details>

### aeonflux

<details>
<summary markdown="span">Click for details</summary>
- [aeonflux] Implementation
- Properties: Multi-show, Attributes
- Based on: [KVAC]({{site.baseurl}}/primitives.html#kvac)
- Performance: TODO
</details>

[aeonflux]: https://github.com/isislovecruft/aeonflux

<!-- TODO(caw): add e-cash and e-voting -->

---


### [[BL13]]: Anonymous Credentials Light
<details>
<summary markdown="span">Click for details</summary>
- Based on: Abe-Okamoto
- Properties: Attributes
- Notes: Small anonymous credentials that allow a user with a list of attributes (L_1, \dots, L_n)
</details>

### [[KVAC]]: Keyed-Verification Anonymous Credentials
<details>
<summary markdown="span">Click for details</summary>
- Based on: [Algebraic MACs]({{site.baseurl}}/primitives.html#algebraic-macs)
- Properties: Multi-show, Public Attributes, Selective Disclosure
</details>

### [[TAKS10]]: BLAC: Revoking Repeatedly Misbehaving Anonymous Users ...
<details>
<summary markdown="span">Click for details</summary>
- Based on: [ZKPs]({{site.baseurl}}/primitives.html#zkps) & BBS+ Signatures
- Related: [[BLACR]] *"BLACR: TTP-free blacklistable anonymous credentials with reputation ..."*
- Related: [[AKTS07]] *"Blacklistable Anonymous Credentials: Blocking Misbehaving .."*
- Properties: Blacklisting
</details>

### [\[PDF\]](https://link.springer.com/chapter/10.1007/978-3-540-85230-8_25): An Efficient Anonymous Credential System
<details>
<summary markdown="span">Click for details</summary>
- Based on: Bilinear Pairings, TODO
- Properties: Strong-unlinkability, Attributes
</details>

### [[CL06]]: Randomizable Proofs and Delegatable Anon Credentials
<details>
<summary markdown="span">Click for details</summary>
- Based on: [ZKPs]({{site.baseurl}}/primitives.html#zkps)
- Related: [[CSF14]] *"Malleable Signatures: New Definitions and Delegatable Anonymous Credentials"*
- Properties: Multi-show, Delegetable
</details>

### [[CL04]]: Signature Schemes and Anonymous Credentials from ...
<details>
<summary markdown="span">Click for details</summary>
- Based on: [Group Signatures]({{site.baseurl}}/primitives.html#group-signatures)
- Properties: TODO
</details>

### [[CL03]]: A Signature Scheme with Efficient Protocols
<details>
<summary markdown="span">Click for details</summary>
- Based on: [ZKPs]({{site.baseurl}}/primitives.html#zkps)
- Properties: Multi-show, Attributes
- Notes: The distinguishing feature of a CL signature is that it allows a user
  to prove possession of a signature without revealing the underlying messages
  or even the signature itself using efficient zero-knowledge proofs of
  knowledge. As the proof is “zero-knowledge”, the user can repeat such a proof
  as many times as she wants and still it is not possible to link the
  individual proofs.
- Related: [[CL01]] An Efficient System for Non-transferable Anonymous Credentials
</details>

### [[CL02]]: Dynamic Accumulators and Application to Efficient, Revocable Credentials
<details>
<summary markdown="span">Click for details</summary>
- Based on: [Accumulators]({{site.baseurl}}/primitives.html#acc)
- Properties: Revocation
</details>

### [[EPID]]: Enhanced Privacy ID
<details>
<summary markdown="span">Click for details</summary>
- Based on: [BBS+ signatures]({{site.baseurl}}/primitives.html#blindsig-bbs)
- Properties: Revocation
</details>

[EPID]: <https://eprint.iacr.org/2009/095.pdf>
[CL01]: <https://www.iacr.org/archive/eurocrypt2001/20450093.pdf>
[CL02]: <https://cs.brown.edu/people/alysyans/papers/camlys02.pdf>
[CL03]: <https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.186.5994&rep=rep1&type=pdf>
[CL04]: <https://www.iacr.org/archive/crypto2004/31520055/cl04.pdf>
[CL06]: <https://eprint.iacr.org/2008/428.pdf>
[BL13]: <https://core.ac.uk/download/pdf/193377167.pdf>
[DGS+18]: <https://www.petsymposium.org/2018/files/papers/issue3/popets-2018-0026.pdf>
[KVAC]: <https://eprint.iacr.org/2013/516.pdf>
[CSF14]: <http://www0.cs.ucl.ac.uk/staff/S.Meiklejohn/files/csf14.pdf>
[TAKS10]: <https://www.cs.dartmouth.edu/~sws/pubs/taks10.pdf>
[BLACR]: <https://ro.uow.edu.au/cgi/viewcontent.cgi?article=9238&context=infopapers>
[AKTS07]: <https://www.cs.dartmouth.edu/~sws/pubs/akts07.pdf>
