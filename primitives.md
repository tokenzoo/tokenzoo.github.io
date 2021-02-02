---
layout: default
title: Cryptographic Primitives
banner: cave.jpg
---
In this page you can find cryptographic schemes that can serve as the basis of anonymous credential schemes.

## Signatures
<details>
<summary markdown="span">Click for details</summary>

### Blind Signatures

Blind Signatures are cryptographic signatures in which the message is blinded before being signed.
In this way, it is possible for the signer to sign a message without knowing its content.

### Blind RSA

### Blind Schnorr

Blind Schnorr signatures are derived from

Schnorr signatures gave rise to a plethora of variants, some of them with applications to anonymous credentials and e-voting.

Derived from Schnorr blind signatures, [partially blind signatures](https://www.iacr.org/archive/crypto2000/18800272/18800272.pdf) (Abe et al.) are signatures
 which allow the signature to contain a non-blinded part, that is mutually shared between the server and the client.

### Brand's blind signature [\[PDF\]](http://courses.csail.mit.edu/6.857/2009/handouts/untraceable.pdf)

### [BBS+ signatures] (Boneh-Boyen-Shacham signatures)

First introduced by [by Boneh et al.](http://crypto.stanford.edu/~dabo/papers/groupsigs.pdf)
as BBS signatures, and then later improved
[by Au et al.](http://web.cs.iastate.edu/~wzhang/teach-552/ReadingList/552-14.pdf)
as BBS+ signatures. Also studied [by Camenisch et al.](https://eprint.iacr.org/2016/663.pdf).

They allow the multi-message signing while producing a single output
signature. This fits naturally the use case of attributes in anonymous
credentials.

While pairings are used during the scheme, they are not used for signature
verification.

Also used in the [EPID scheme](https://eprint.iacr.org/2009/095.pdf).

[BBS+ signatures]: http://web.cs.iastate.edu/~wzhang/teach-552/ReadingList/552-14.pdf)


[Implementation](https://github.com/hyperledger/ursa/tree/master/libzmix/bbs)

[Working Group](https://w3c-ccg.github.io/ldp-bbs2020/) for web based credentials. 

### [PS signatures] (Pointcheval-Sanders signatures)

Usually used for threshold issuance.

[Related signature scheme](https://eprint.iacr.org/2020/016.pdf)

[PS signatures]: https://eprint.iacr.org/2015/525.pdf

### [BLS signatures] (Boneh–Lynn–Shacham signatures)

[BLS signatures]: https://www.iacr.org/archive/asiacrypt2001/22480516.pdf


### [Mercurial Signatures]

Notes: Mercurial signatures can [be used](https://eprint.iacr.org/2018/923.pdf) to create delegetable credentials.

[Mercurial Signatures]: https://eprint.iacr.org/2020/979

### Signatures of Knowledge
</details>

## Algebraic MACs


## OPRF
<details>
<summary markdown="span">Click for details</summary>
- Jareki et al. (for Privacy Pass)
- Naor-Reingold
</details>

## Commitments
## Zero-Knowledge Proofs

## Accumulators
<details>
<summary markdown="span">Click for details</summary>

A cryptographic accumulator aggregates many different values into a
fixed-length digest. They also allow to verify whether an element is
accumulated or not using a *membership witness*. In the context of anonymous
credentials, accumulators can be used to implement various shapes of credential
revocation.

Accumulators were first introduced by [Benaloh and De
Mare](https://link.springer.com/content/pdf/10.1007%2F3-540-48285-7_24.pdf) as
a time-stamping protocol.

The main constructions for dynamic accumulators according to [Benarroch et
al](https://eprint.iacr.org/2019/1255.pdf) and [Boneh et
al](https://eprint.iacr.org/2018/1188.pdf) are:

- RSA-Based: Slow to bootstrap, reasonable performance for updates, proof
  generation and verification ([BP97,CL02,  LLX07,  Lip12])
- ECC-based: Smaller and faster proofs than RSA. Setup parameters large and the
  number of elements they support is fixed after creation. Work on curves that
  support bilinear pairings. ([DT08,  CKS09,  Ngu05])
- Merkle hash trees: Short setup parameters and accumulator size depends on
  tree depth ([[Mer88, CHKO08])

[Example ECC-based scheme](https://eprint.iacr.org/2020/777.pdf)
and [example RSA-based implementation](https://github.com/mikelodder7/accumulator-rs).

</details>

