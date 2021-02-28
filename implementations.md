---
layout: default
title: Implementations
banner: surprised.jpg
---
In this page you can find anonymous credentials schemes that have been
specified and implemented and hence we can get concrete performance figures out of them.

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

### Tor Anonymous Resumption Tokens

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