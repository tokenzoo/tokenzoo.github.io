---
layout: default
title: Properties
banner: crabs.jpg
---
<style>

details > *:not(summary){
  margin-left: 2em;
}

ul,li {
  margin-left: 4em;
}

</style>

Formally, anonymous credentials are two-party cryptographic protocols
where a user interacts with an issuer. Such protocols were first
introduced by Chaum in
[[Chaum]]({{site.baseurl}}/bibliography.html#chaum85), and several
practical instantiations have followed.

There are two core security notions that that an anonymous credential
scheme should satisfy: unforgeability an unlinkability.
Informally, unforgeability protects the issues and makes sure that no
unauthorized credential is spent. On the other hand, unlinkability
protects the user and makes sure that the user cannot be tracked across sessions.

The literature proposes many more additional features that extend the
properties of the scheme, such as embedding (authenticated) public
metadata, revocation, and blacklisting. For readability, we have compressed
them below.

## Unforgeability

Unforgeability refers to the notion that an adversary should not be able to
create credentials without the appropriate authorizations. It should not
be able to do so even after interacting multiple times with an issuer.

Definitions differ across various papers. For example, the works of
[[CDHK15]]({{site.baseurl}}/bibliography.html#cdhk15), and
[[HLR15]]({{site.baseurl}}/bibliography.html#hlr15) give specific
definitions that differ depending on the actual scheme.

In the case of tokens, we generally ask one-more-unforgeability, i.e. that it
is not possible to spend more tokens than have been issued. In the case of
credentials, we generally ask the adversary cannot authenticate for a
credentials that was not issued in the first place, even after observing
credentials of other users.

## Unlinkability

Unlinkability, also known as *blindness*, or *context-hiding* in other works,
indicated that the redemption of a credential (where the user is anonymous)
cannot be linked to its respective issuance (where the user is identified).

Definitions of unlinkability for anaonymous credential schemes appeared
earliest in the work of [[CL01]]({{site.baseurl}}/bibliography.html#cl01)
and subsequently in
[[CKLM13]]({{site.baseurl}}/bibliography.html#cklm13), \[CDHK15\], and
\[HLR15\].

An anonymous credential scheme where linking the token to a user is protected
by information-theoretic security guarantees has *perfect*, or *strong*
unlinkability. This property has been formally studied in
[[AMO08]]({{site.baseurl}}/bibliography.html#amo08), and guarantees that
attacks on classical cryptosystems by unbounded adversaries will not
allow linkage of activity in the future.


## Additional Features

Anonymous tokens and credentials may introduce additional features, for
helping thwi solving specific problems.

<details>
<summary markdown="span">Click for details</summary>

### Concurrent Security

A system is said to have concurrent security if the signer or issuer of
tokens or credentials can engage in multiple, concurrent issuances at
the same time without affecting security. Many schemes only include
proofs that consider sequential security, wherein at most one issuance
flow occurs at a time, yet fail to achieve concurrent security. In
practice, concurrent security is paramount.

### Single-Show and Multi-Show

Tokens or credentials may be either single- or multi-show, depending on the cryptographic
construction. For example, tokens derived from the output of an [OPRF protocol]({{site.baseurl}}/primitives.html#oprf) are
typically single-show because spending the same token twice forces the client to
reveal the same input twice, thereby breaking unlinkability. Credentials
that permit multi-show operations (such as [[CL06]]({{site.baseurl}}/bibliography.html#bcckls08))

### Revocation

Defined here by [Acar et al.](https://www.iacr.org/archive/pkc2011/65710436/65710436.pdf) and
implemented using an accumulator scheme with delegatable non-membership proofs.
Revocation via blocklisting was also implemented by [Tsang et al.](https://www.cs.dartmouth.edu/~sws/pubs/akts07.pdf).

### Associated Data

Credentials may permit attaching associated data during an issuance transaction. Attaching metadata to
credentials can lead to not guarantee the desired level of anonymity.
In scenarios where metadata is permitted, credentials are only
unlinkable from the set of users with the same metadata (regardless of
whether it is public or private).

#### Public Attributes {#public-metadata}

Anonymous credentials with "Public Attributes" can include metadata (e.g. provider, country of origin). The metadata is generated and signed by the issuer as part of the "credential
issuance" protocol, and are visible by the credential holder.

Certain schemes allow "selective disclosure" of attributes during token
redemption which allows the user to choose which attributes to reveal and which
ones to keep secret, while other schemes require disclosing all attributes.

#### Private Attributes {#private-metadata}

Credentials with "Private Attributes" include metadata that is created
by and visible to the issuer but not by the credential holder. This can allow services to "shadowban" or rate-limit flagged users.

Private attributes must hold privacy: it must be infiseable for
the issuer to link two credentials with the same set of private
attributes.

### Delegatable

Introduced in [CL06]({{site.baseurl}}/bibliography.html#bcckls08), delegatable anonymous credential system allow participants to use their
credentials anonymously, as well as anonymously delegate them to other
participants.

### Escrow

TODO

### Threshold Issuance

A credential scheme where there can be multiple credential issuers which can
also potentially be Byzantine. (see [Coconut](https://arxiv.org/pdf/1802.07344.pdf)).

</details>
