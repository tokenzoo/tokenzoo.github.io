---
layout: default
title: Schemes
banner: bird.jpg
---
In this page you can find anonymous credentials schemes that are not
implemented, are mainly in research stage, or can serve as a basis for more
complete systems.

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
- Related: [[CL01]] An Efficient System for Non-transferable Anonymous Credentials ...
</details>

### [[CL02]]: Dynamic Accumulators and Application to Efficient ...
<details>
<summary markdown="span">Click for details</summary>
- Based on: TODO
- Properties: TODO
</details>

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
