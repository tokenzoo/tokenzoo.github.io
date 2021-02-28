---
layout: default
title: Cryptographic Primitives
banner: cave.jpg
---
{% comment %}

For each primitive we start with a quick summary and an overview of how/why
that primitive is used in the context of anonymous credentials.

After that, in the <details> block we can go into more details. For example:
- Literature overview
- Security properties
- Links to implementations
- Miscelaneous notes, drawbacks, etc.

{% endcomment %}


<style>

h2 {
    font-size: 1.5em;
}

h3 {
    font-size: 1.2em;
}

</style>


In this page you can find cryptographic schemes that can serve as the basis of anonymous credential schemes.

## Algebraic MACs

Algebraic MACs are MACs constructed in cyclic groups of prime order. Algebraic
MACs are used in the context of anonymous credentials because it's easy and
fast to create zero knowledge proofs about algebraic statements.

<details>
<summary markdown="span">Click for details</summary>

Algebraic MACs must satisfy *correctness* -- that honestly generated MACs must
verify correctly -- and *existential unforgeability* -- that those without
access to the symmetric key cannot generate MACs on new data.

MACs of this nature are combined with ZK proofs to construct anonymous
credentials, for example see Chase et al. [[CMZ14]].

</details>

## Accumulators {#acc}

A cryptographic accumulator aggregates many different values into a
fixed-length digest. They also allow to verify whether an element is
accumulated or not using a *membership witness*. In the context of anonymous
credentials, accumulators can be used to implement various shapes of credential
revocation.

<details>
<summary markdown="span">Click for details</summary>
Accumulators were first introduced by [Benaloh and De
Mare](https://link.springer.com/content/pdf/10.1007%2F3-540-48285-7_24.pdf) as
a time-stamping protocol.

The main constructions for dynamic accumulators according to [Benarroch et
al](https://eprint.iacr.org/2019/1255.pdf) and [Boneh et
al](https://eprint.iacr.org/2018/1188.pdf) are:

- RSA-Based: Slow to bootstrap, reasonable performance for updates, proof
  generation and verification ([BP97, CL02, LLX07, Lip12])
- ECC-based: Smaller and faster proofs than RSA. Setup parameters large and the
  number of elements they support is fixed after creation. Work on curves that
  support bilinear pairings. ([DT08, CKS09, Ngu05])
- Merkle hash trees: Short setup parameters and accumulator size depends on
  tree depth ([[Mer88, CHKO08])

[Example ECC-based scheme](https://eprint.iacr.org/2020/777.pdf)
and [example RSA-based implementation](https://github.com/mikelodder7/accumulator-rs).

</details>

## Oblivious Pseudorandom Functions {#oprfs}

Oblivious Pseudorandom Functions (OPRFs) are two-party protocols for obliviously
evaluating pseudorandom functions: using private client inputs, and a private
server key. Such protocols can be augmented with extra verifiability properties
(VOPRFs) to ensure that the client can verify that the PRF is evaluated
correctly.

OPRFs are used in the context of anonymous credentials in a similar way that
blind signatures are used. The client sends a blinded nonce to the server, and
the server produces a pseudorandom value from that nonce in a way that the
client can *verify* that it was created in a unique way and hence the server
could not tag the message.

<details>
<summary markdown="span">Click for details</summary>

The key security properties of such protocols are that the final output is
*pseudorandom* against malicious clients, and that malicious servers cannot
learn anything about client inputs. If *verifiability* is required, servers
must prove to the client that the PRF output is correct.

OPRF constructions typically considered in anonymous credential schemes include
[[JKK14]] and [[NR04]].
</details>

## Blind Signatures {#blindsigs}

Signatures are cryptographic schemes for verifying the authenticity of digital
messages. Signatures must satisfy two main security properties: *correctness*,
which asks that all honestly-generated signatures must verify, and *unforgeability*,
which asks that it is unfeasible for an adversary to forge signatures, even after
observing an arbitrary number of them.

Blind Signatures are multi-party protocols for computing cryptographic signatures
in which the message is blinded before being signed. In this way, it is possible
for the signer to sign a message without knowing its content.

<details>
<summary markdown="span">Click for details</summary>

### Blind RSA signature

Chaum's Blind RSA signature scheme, [analyzed by Bellare et al.](https://link.springer.com/article/10.1007/s00145-002-0120-1)
is perhaps the most widely known blind signature scheme. Variations of this protocol,
using different message encoding schemes such as FDH and PSS, have been proposed
and implemented. Blind RSA can also be made partially oblivious to support a
fixed amount of public attributes [[AF96]], albeit at significant performance costs.

### Blind Schnorr signatures

Schnorr signatures gave rise to a plethora of variants, some of them with
applications to anonymous credentials and e-voting. A Blind Schnorr signature
scheme is a two-party protocol for receiving valid Schnorr signatures on hidden
inputs.

Derived from Schnorr blind signatures, [partially blind signatures](https://www.iacr.org/archive/crypto2000/18800272/18800272.pdf) (Abe et al.) are signatures which allow the signature to contain a non-blinded part,
that is mutually shared between the server and the client.

Security of most Schnorr signature variants reduces to the ROS problem [[Sch01]].
[[BLL+20]] demonstrated a polynomial-time attack against this problem, improving
on Wagner's subexponential-time attack. This impacted most known Schnorr variants.
[[FPS20]] introduced a variant of Schnorr's protocol that is not known to be
vulnerable to this attack.

### BBS+ signatures (Boneh-Boyen-Shacham signatures) {#blindsig-bbs}

First introduced by [by Boneh et al.](http://crypto.stanford.edu/~dabo/papers/groupsigs.pdf)
as BBS signatures, and then later improved
[by Au et al.](http://web.cs.iastate.edu/~wzhang/teach-552/ReadingList/552-14.pdf)
as BBS+ signatures. Also studied [by Camenisch et al.](https://eprint.iacr.org/2016/663.pdf).

They allow the multi-message signing while producing a single output
signature. This fits naturally the use case of attributes in anonymous
credentials.

While pairings are used during the scheme, they are not used for signature
verification.

### PS signatures (Pointcheval-Sanders signatures)

[PS signatures] are usually used for threshold issuance.

[Related signature scheme](https://eprint.iacr.org/2020/016.pdf)

### Waters+ signatures

[Meiklejohn et al.](https://www.cs.utexas.edu/~hovav/dist/blindsigs.pdf) built on
a generalized version of Waters signatures, in combination with Groth-Sahai proofs,
to construct a round-optimal, partially oblivious blind signature scheme.

### BLS signatures (Boneh–Lynn–Shacham signatures)

[BLS signatures] are used to create credential schemes with selective attribute disclosure.

### Mercurial Signatures

[Mercurial signatures] can [be used](https://eprint.iacr.org/2018/923.pdf) to create delegetable credentials.

### Signatures of Knowledge

[Signatures of Knowledge] allow one to issue signatures on behalf of any NP
statement, that can be interpreted as follows: “A person inpossession of a
witness to the statement that x∈L has signed message m.”

</details>

## Zero-Knowledge Proofs

Zero-knowledge proofs are cryptographic constructions by which a prover can
convince a verifier that a statement is true.

Zero-knowledge proofs are a fundamental tool in the construction of anonymous
credentials. They are used in various different ways depending on the scheme:
For example, they can protect linkabilty by allowing clients to prove the
existence of trusted signatures without revealing the signatures themselves
(e.g. [[CL06]]({{site.baseurl}}/schemes.html#cl06)). They can also protect
linkability by allowing issuers to prove to clients that token issuance was
conducted properly (e.g. [[PP]](({{site.baseurl}}/schemes.html#pricacy-pass))

<details>
<summary markdown="span">Click for details</summary>

We demand essentially three main properties from zero knowledge proofs:
*completeness*, which means that honestly-generated proofs should always
verify; *soundness*, which protects the verifier and states that it is
computationally unfeasible for an attacker to generate invalid proofs;
*zero-knowledge*, which means that the proof itself leaks no information
besides what can be already inferred by the statement itself.

Depending on the anonymous credential application, different notion of
soundness might apply.

</details>

[CMZ14]: <https://eprint.iacr.org/2013/516.pdf)>
[JKK14]: <https://eprint.iacr.org/2014/650.pdf>
[NR14]: <http://www.wisdom.weizmann.ac.il/~naor/PAPERS/gdh.ps>
[Mercurial Signatures]: <https://eprint.iacr.org/2020/979>
[Signatures of Knowledge]: <https://eprint.iacr.org/2006/184.pdf>
[BLS signatures]: <https://www.iacr.org/archive/asiacrypt2001/22480516.pdf>
[PS signatures]: <https://eprint.iacr.org/2015/525.pdf>
[BBS+ signatures]: <http://web.cs.iastate.edu/~wzhang/teach-552/ReadingList/552-14.pdf>
[AF96]: <https://link.springer.com/chapter/10.1007/BFb0034851>
[MSF10]: <https://www.cs.utexas.edu/~hovav/dist/blindsigs.pdf>
[Wat04]: <https://eprint.iacr.org/2004/180.pdf>
[Sch01]: <https://link.springer.com/chapter/10.1007%2F3-540-45600-7_1>
[BLL+20]: <https://eprint.iacr.org/2020/945.pdf>
[FPS20]: <https://doi.org/10.1007/978-3-030-45724-2_3>