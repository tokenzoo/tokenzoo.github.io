---
layout: page
title: Implementations
---
In this page you can find anonymous credentials schemes that have been
specified and implemented and hence we can get concrete performance figures out of them.

## [Privacy Pass]

- [PrivacyPass paper](https://www.petsymposium.org/2018/files/papers/issue3/popets-2018-0026.pdf)
- Source code: [Client](https://github.com/privacypass/challenge-bypass-extension) & [Server](https://github.com/privacypass/challenge-bypass-server)
- Properties: TODO
- Based on: [OPRF]({{site.baseurl}}/primitives.html#oprfs)
- Performance
  - Credential Size: TODO
  - Key size: TODO
  - Show size: TODO
  - Prover time: TODO
  - Verifier time: TODO

[Privacy Pass]: https://privacypass.github.io/

## [Signal Private Group System]

- [Signal Private Group System Paper](https://eprint.iacr.org/2019/1416)
- [Implementation](https://github.com/signalapp/Signal-Android/tree/master/libsignal/service/src/main/java/org/whispersystems/signalservice/api/groupsv2)
- Properties: TODO
- Based on: [KVAC]({{site.baseurl}}/schemes.html#kvac)
- Performance
  - Credential Size: [493 bytes](https://youtu.be/4eKwlSqGUi4?list=PLeeS-3Ml-rpoVMNQkUrFDSfaTuUMxVtjy&t=2481)
  - Key size: TODO
  - Show size: TODO
  - Prover time: [2.16ms](https://youtu.be/4eKwlSqGUi4?list=PLeeS-3Ml-rpoVMNQkUrFDSfaTuUMxVtjy&t=2481)
  - Verifier time: [1.17ms](https://youtu.be/4eKwlSqGUi4?list=PLeeS-3Ml-rpoVMNQkUrFDSfaTuUMxVtjy&t=2481)

[Signal Private Group System]: https://signal.org/blog/signal-private-group-system/

## [Coconut]

- [Coconut] paper
- [Implementation](https://github.com/asonnino/coconut) and [another implementation](https://gitlab.com/narodnik/darkwallet/-/tree/master/src/coconut)
- Properties: TODO
- Based on: [PS signatures]({{site.baseurl}}/primitives.html#ps-signatures)
- Performance
  - Credential Size: TODO
  - Key size: TODO
  - Show size: TODO
  - Prover time: TODO
  - Verifier time: TODO

[Coconut]: https://arxiv.org/pdf/1802.07344.pdf

## [U-Prove]

- [U-Prove] specification
- [U-Prove implementation](https://github.com/Microsoft/uprove-csharp-sdk)
- Properties: TODO
- Based on: TODO
- Performance
  - Credential Size: TODO
  - Key size: TODO
  - Show size: TODO
  - Prover time: TODO
  - Verifier time: TODO

[U-Prove]: https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/U-Prove20Cryptographic20Specification20V1.1.pdf

## [Idemix]

- [Idemix Paper](https://www.cise.ufl.edu/~nemo/anonymity/papers/idemix.pdf)
- [Implementation](prime.inf.tu-dresden.de/idemix/)
- Properties: Constant Credential Size, Multi-show
- Based on: [Blind RSA]({{site.baseurl}}/primitives.html#blind-rsa)
- Performance
  - Credential Size: TODO
  - Key size: TODO
  - Show size: TODO
  - Prover time: TODO
  - Verifier time: TODO

[Idemix]: https://idemix.wordpress.com/

## [aeonflux]

- [aeonflux] Implementation
- Properties: Multi-show, TODO
- Based on: [Algebraic MACs]({{site.baseurl}}/primitives.html#algebraic-macs)
- Performance
  - Credential Size: TODO
  - Key size: TODO
  - Show size: TODO
  - Prover time: TODO
  - Verifier time: TODO

[aeonflux]: https://github.com/isislovecruft/aeonflux

## Facebook

https://engineering.fb.com/2019/10/16/security/partially-blind-signatures/
