---
layout: default
title: Properties
banner: crabs.jpg
---

## Unforgeability

Also studied [by Hoepman et al.](https://eprint.iacr.org/2015/842.pdf) for the
case of multi-show credential schemes.

Studied over [Camenisch et al.](https://eprint.iacr.org/2015/580.pdf), it is
referred to the notion that an adversary should not be able to produce an exact
same valid token (TODO: I guess we should be referring to them as that) that has
been produced in the past.

It is related to what is referred
on [Privacy Pass](https://www.petsymposium.org/2018/files/papers/issue3/popets-2018-0026.pdf)
as 'one-more-token' security: the requirement that a party should be unable to
forge validly signed tokens using information it learns (TODO: learns during what phase?).

## Unlinkability, Blindness

Defined here [by Camenisch et al.](https://eprint.iacr.org/2015/580.pdf) as a
property of a signature scheme, in the sense that the issuance of a token
(TODO: or signature, might be the same..) and its later use in a protocol
cannot be linked.

It is also referred as 'context-hiding', in earliest [works](https://eprint.iacr.org/2013/179.pdf)
Also studied [by Hoepman et al.](https://eprint.iacr.org/2015/842.pdf) for the case of multi-show credential schemes.

## Strong-unlinkability

An anonymous credential scheme where linking the token to a user is protected
by information-theoretic means, and not just computational security.

Studied [by Akagi et al.](https://www.researchgate.net/publication/220797020_An_Efficient_Anonymous_Credential_System).

## Revocation

Defined here by [Acar et al.](https://www.iacr.org/archive/pkc2011/65710436/65710436.pdf) and
implemented using an accumulator scheme with delegatable non-membership proofs

Revocation can also be achieved with TODO

## Public Attributes

Anonymous credentials with "Public Attributes" can include metadata (e.g. name,
age). The metadata are signed by the issuer as part of the "credential
issuance" protocol and are visible by the credential holder.

Certain schemes allow "selective disclosure" of attributes during token
redemption which allows the user to choose which attributes to reveal and which
ones to keep secret, while other schemes require disclosing all attributes.

## Private Attributes

Anonymous credentials with "Private Attributes" can include metadata that are
visible by the issuer but not by the credential holder. This can allow services
to "shadowban" or rate-limit flagged users.

## Single/Multi-show

Related terms: "self-blindable"

## Public Verifiability

An attribute-based credential (ABC) scheme allows a user, given a set of
attributes, toprove ownership of these attributes to a verifer and selectively
disclose some of them whilekeeping the others secret

## Delegatable

In a delegatable anonymous credential system, participants may use their
credentials anonymously as well as anonymously delegate them to other
participants.

Introduced in [CL06]({{site.baseurl}}/schemes.html#cl06).

## Escrow



## Threshold Issuance

A credential scheme where there can be multiple credential issuers which can
also potentially be Byzantine. (see [Coconut](https://arxiv.org/pdf/1802.07344.pdf)).


