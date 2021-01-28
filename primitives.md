---
layout: default
title: Cryptographic Primitives
banner: cave.jpg
---
In this page you can find cryptographic schemes that can serve as the basis of anonymous credential schemes.

# Signatures

## Blind Signatures

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

# Algebraic MACs

# OPRF

- Jareki et al. (for Privacy Pass)
- Naor-Reingold

# Commitments
# Zero-Knowledge Proofs



# Accumulators

[Example scheme](https://eprint.iacr.org/2020/777.pdf)
and [example implementation](https://github.com/mikelodder7/accumulator-rs).

Notes: Accumulators can be used to implement revocation and blacklistable credentials

