---
layout: default
title: Cryptographic Primitives
banner: cave.jpg
---
In this page you can find cryptographic schemes that can serve as the basis of anonymous credential schemes.


## Algebraic MACs

Algebraic MACs are MACs constructed in cyclic groups of prime-order. Such constructions must satisfy *correctness* -- that honestly generated MACs must verify correctly -- and *existential unforgeability* -- that those without access to the symmetric key cannot generate MACs on new data.

<details>
<summary markdown="span">Click for details</summary>
MACs of this nature can be combined with ZK proofs to construct anonymous credentials, for example see Chase et al. [[CMZ14]].
</details>

## Accumulators

A cryptographic accumulator aggregates many different values into a
fixed-length digest. They also allow to verify whether an element is
accumulated or not using a *membership witness*. In the context of anonymous
credentials, accumulators can be used to implement various shapes of credential
revocation.

Accumulators were first introduced by [Benaloh and De
Mare](https://link.springer.com/content/pdf/10.1007%2F3-540-48285-7_24.pdf) as
a time-stamping protocol.

<details>
<summary markdown="span">Click for details</summary>
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

## OPRF

Oblivious pseudorandom functions are two-party protocols for obliviously evaluating pseudorandom functions: using private client inputs, and a private server key. Such protocols can be augmented with extra verifiability properties to ensure that the client can verify that the PRF is evaluated correctly. The key security properties of such protocols are that the final output is *pseudorandom* against malicious clients, and that malicious servers cannot learn anything about client inputs. If *verifiability* is required, servers must prove to the client that the PRF output is correct.

<details>
<summary markdown="span">Click for details</summary>

OPRF constructions typically considered in anonymous credential schemes:
- [[JKK14]]
- [[NR04]]
</details>

## Signatures

Signatures are cryptographic schemes that allow to verify the authenticity of messages. They must satisfy two main properties: *correctness*, which asks that all honestly-generated signatures must verify, and *unforgeability*, which asks that it is unfeasible for an adversary to forge signatures, even after observing an arbitrary number of them.

A number of variations of the above definitions are available in the literature, in order to accomodate for protocols that need to be able to issue signatures while maintaining parts of the message hidden from the signer or the verifier.


<details>
<summary markdown="span">Click for details</summary>

### Blind Signatures

Blind Signatures are cryptographic signatures in which the message is blinded before being signed.
In this way, it is possible for the signer to sign a message without knowing its content.

#### Blind RSA

A variant of textbook RSA signatures that uses the multiplicative property of this scheme to allow input blinding. This gives rise to a two-party protocol where the client provides a randomised input to the server, the server signs the input with their secret key and returns the signature to the client, and then the client de-randomises the server message and outputs the result as a signature on their original input. Such constructions can naturally be thought of as public verifiable variants of OPRF protocols, since anyone with the verification key can verify this signature.

To illustrate the blinding and signing procedure, consider a standard RSA signature scheme with keypair $(sk, pk) = ((p, q, d), (N = pq, e))$, where $(sk, pk)$ is held by the server, and $pk$ is held by the client. The client samples a valid message $m$, a random value $r$, and blinds $m$ by computing:

$$
m' = m \cdot r^e \pmod N
$$

The client sends $m'$ to the server, who computes and returns to the client:

$$
s' = (m')^dr \pmod N
$$

The client unblinds $s'$ to a valid signature $s$ on the original message $m$ by computing:

$$
s = s' \cdot r^{-1} \pmod N
$$

Correctness holds since:

$$
s = s' \cdot r^{-1} = (m \cdot r^e)^d \cdot r^{-1} = m^d \cdot r \cdot r^{-1} = m^d \pmod N
$$

Verification is the same as RSA signature verification.
#### Blind Schnorr

A Blind Schnorr signature scheme is a two-party protocol for receiving valid Schnorr signatures on hidden inputs. 

Schnorr signatures gave rise to a plethora of variants, some of them with applications to anonymous credentials and e-voting.

Derived from Schnorr blind signatures, [partially blind signatures](https://www.iacr.org/archive/crypto2000/18800272/18800272.pdf) (Abe et al.) are signatures which allow the signature to contain a non-blinded part, that is mutually shared between the server and the client.

#### [BBS+ signatures] (Boneh-Boyen-Shacham signatures)

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

## Zero-Knowledge Proofs


Zero-knowledge proofs is a cryptographic construction by which a prover can convince a verifier that a statement is true. We demand essentially three main properties from them:
*completeness*, which means that honestly-generated proofs should always verify;
*soundness*, which protects the verifier and states that  it is computationally unfeasible for an attacker to generate invalid proofs;
*zero-knowledge*, which means that the proof itself leaks no information besides what can be already inferred by the statement itself.


Zero-knowledge proofs are a fundamental tool in the construction of anonymous credentials, and depending on the application, different notion of soundness might apply.

## References

[CMZ14]: <https://eprint.iacr.org/2013/516.pdf)>
[JKK14]: <https://eprint.iacr.org/2014/650.pdf>
[NR14]: <http://www.wisdom.weizmann.ac.il/~naor/PAPERS/gdh.ps>