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

### [PS signatures] (Pointcheval-Sanders signatures)

[PS signatures]: https://eprint.iacr.org/2015/525.pdf

### [BLS signatures] (Boneh–Lynn–Shacham signatures)

[BLS signatures]: https://www.iacr.org/archive/asiacrypt2001/22480516.pdf


## [Mercurial Signatures]

Notes: Mercurial signatures can [be used](https://eprint.iacr.org/2018/923.pdf) to create delegetable credentials.

[Mercurial Signatures]: https://eprint.iacr.org/2020/979

## Signatures of Knowledge

## Algebraic MACs

# OPRF

- Jareki et al. (for Privacy Pass)
- Naor-Reingold

# Commitments
# Zero-Knowledge Proofs



# Accumulators

Notes: Accumulators can be used to implement revocation and blacklistable credentials

