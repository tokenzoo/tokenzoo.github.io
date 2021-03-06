---
layout: default
title: Schemes
banner: bird.jpg
---
<style>

.scheme-table {
    width: 100%;
    text-align: center;
}
.scheme-table th {
    background: black;
    word-wrap: break-word;
    text-align: center;
}
.scheme-table td:nth-child(1) {
    background: grey;
    color: black;
}

</style>

In this page we go over various proposed anonymous credential and token schemes.

<br>

We start our investigation with anonymous credentials schemes that have been
specified and implemented. We first present the various schemes and their
security properties in this table, and then we dive more in depth right below.

<br>

<div class="scheme-table">

| Scheme               | Type          | Attributes | Public Verifiability | Other notes                             |
| -------------------- | ------------- | ---------- | -------------------- | --------------------------------------- |
| Privacy Pass         | Single-show   | ?          |      No              | Perfect Unlinkability                   |
| Signal Creds         | Multi-show    | Yes        |      No              |                                         |
| Coconut              | Multi-show    | Yes        |      Yes             | Complex attributes / Threshold Issuance |
| Idemix               | Multi-show    | ?          |      ?               |                                         |
| FB PrivateStats      | Single-show   | Yes        |      No              |                                         |
| U-Prove              | Single-show   | Yes        |      ?               |                                         |
| FB Blind Sigs        | Single-show   | ?          |      Yes             | Perfect Unlinkability                   |
| aeonflux             | Multi-show    | Yes        |      No              |                                         |

</div>

<br>

### [[DGST18]]: Privacy Pass

<details>
<summary markdown="span">Click for details</summary>

- [Website](https://privacypass.github.io/)
- Source code: [Client](https://github.com/privacypass/challenge-bypass-extension) & [Server](https://github.com/privacypass/challenge-bypass-server)
- Properties: Strong-unlinkability, Single-show
- Based on: [(V)OPRF]({{site.baseurl}}/primitives.html#oprfs)
</details>

### [[CPZ19]]: Signal Private Group System

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

### [[SABM19]]: Coconut

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

### [[CH03]]: Idemix

<details>
<summary markdown="span">Click for details</summary>
- [Implementation](prime.inf.tu-dresden.de/idemix/)
- Properties: Constant Credential Size, Multi-show
- Based on: [CL03]({{site.baseurl}}/schemes.html#cl03)
</details>

[Idemix]: https://idemix.wordpress.com/

### [[HIJK21]]: Facebook's PrivateStats

<details>
<summary markdown="span">Click for details</summary>
- Properties: Single-show, Public Attributes
- Based on:
  - [(V)OPRF]({{site.baseurl}}/primitives.html#oprfs)
</details>

### [[PZ13]]: U-Prove

<details>
<summary markdown="span">Click for details</summary>
- [U-Prove implementation](https://github.com/Microsoft/uprove-csharp-sdk)
- Properties: Single-show, Public Attributes
- Based on: [Brand's blind signature]({{site.baseurl}}/primitives.html#brands-blind-signature)
- Notes: The U-Prove token is single-show, but can be shown multiple times to serve as a pseudonym.
</details>

### Facebook's Blind Signatures

<details>
<summary markdown="span">Click for details</summary>
- [Implementation](https://github.com/siyengar/private-fraud-prevention)
- Properties: Public Verifiability
- Based on: [Blind RSA]({{site.baseurl}}/primitives.html#blind-rsa)
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

<br><br>

---

We now continue with credential schemes that have been proposed and can serve
as a basis for more complete systems but have not been implemented yet.

<br><br>



### [[BL13]]: Anonymous Credentials Light
<details> <summary markdown="span">Click for details</summary>
- Based on: Abe-Okamoto
- Properties: Attributes, Single-show
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

### [[AMO08]]: An Efficient Anonymous Credential System
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

### Tor Anonymous Res Tokens

<details>
<summary markdown="span">Click for details</summary>
- [Tor summary](https://blog.torproject.org/stop-the-onion-denial) and [proposed specification](https://lists.torproject.org/pipermail/tor-dev/2021-February/014517.html)
- Properties: Single-show
- Based on: [Blind RSA]({{site.baseurl}}/primitives.html#blindsigs)
</details>

### [[ZKSZ20]]: EL PASSO: Privacy-preserving, Asynchronous Single Sign-On

<details>
<summary markdown="span">Click for details</summary>
- Based on: [PS signatures]({{site.baseurl}}/primitives.html#ps-signatures)
- Properties: Multi-show, Selective Attribute Disclosure
- Performance:
  - Show size: 414 bytes
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
[DGST18]: <https://www.petsymposium.org/2018/files/papers/issue3/popets-2018-0026.pdf>
[CPZ19]: <https://eprint.iacr.org/2019/1416>
[SABM19]: <https://arxiv.org/pdf/1802.07344.pdf>
[CH03]: <https://www.cise.ufl.edu/~nemo/anonymity/papers/idemix.pdf>
[HIJK21]: <https://research.fb.com/wp-content/uploads/2021/01/PrivateStats-De-Identified-Authenticated-Logging-at-Scale_final.pdf>
[PZ13]: <https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/U-Prove20Cryptographic20Specification20V1.1.pdf>
[AMO08]: <https://link.springer.com/chapter/10.1007/978-3-540-85230-8_25>
[ZKSZ20]: <https://arxiv.org/pdf/2002.10289.pdf>
