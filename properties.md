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

There are two main types of anonymous credential systems:
- tokens
- credentials.

Additionally, there are two possible configurations, allowing either public or private verification.
In both configurations, credentials are issued under a secret server key. In publicly verifiable schemes, there is a public key that allows verifying credentials/tokens. In privately verifiable schemes, only the issuing server can verify.


Besides this, there are two main security properties that an anonymous credential scheme should satisfy: unforgeability an unlinkability. Depending on the feature of the particular scheme that is being chose, there are different additional security properties.
## Unforgeability

Unforgeability refers to the notion that an adversary should not be able to create credentials without the appropriate authorizations.

Studied over [Camenisch et al.](https://eprint.iacr.org/2015/580.pdf), and also studies by studied [by Hoepman et al.](https://eprint.iacr.org/2015/842.pdf), it can take quite a bit of different, specific definitions depending on the actual scheme.

In the case of tokens, we generally ask one-more-unforgeability, i.e. that it is not possible to spend more tokens than have been issued.*
In the case of credentials, we generally ask the adversary cannot authenticate for a credentials that was not issued in the first place, even after observing credentials of other users.


## Unlinkability


Unlinkability, also known as *blindness*, or *context-hiding* in other works, indicated that the redemption of a credential (where the user is anonymous) cannot be linked to its respective issuance (where the user is identified).


Studied [by Camenisch et al.](https://eprint.iacr.org/2015/580.pdf), in earliest [works](https://eprint.iacr.org/2013/179.pdf), and also [by Hoepman et al](https://eprint.iacr.org/2015/842.pdf).
An anonymous credential scheme where linking the token to a user is protected
by information-theoretic means has perfect unlinkability, or *strong unlinkabiliy*.Studied [by Akagi et al.](https://www.researchgate.net/publication/220797020_An_Efficient_Anonymous_Credential_System).
When talking about metadata (public or private) it assures that the tokens that
were issued with the same metadata are indistinguishable to the issuer when
redeemed.



## Additional Features

Most tokens introduce additional features, that help solving specific problems.

<details>
<summary markdown="span">Click for details</summary>

### Revocation

Defined here by [Acar et al.](https://www.iacr.org/archive/pkc2011/65710436/65710436.pdf) and
implemented using an accumulator scheme with delegatable non-membership proofs

Revocation can also be achieved with TODO

### Public Attributes

Anonymous credentials with "Public Attributes" can include metadata (e.g. provider, country of origin). The metadata is generated and signed by the issuer as part of the "credential
issuance" protocol, and are visible by the credential holder.

Certain schemes allow "selective disclosure" of attributes during token
redemption which allows the user to choose which attributes to reveal and which
ones to keep secret, while other schemes require disclosing all attributes.

### Private Attributes

Anonymous credentials with "Private Attributes" include metadata that is created by and visible to the issuer but not by the credential holder. This can allow services
to "shadowban" or rate-limit flagged users.

Private attributes should hold privacy, in the sense that it is very difficult for the issuer to link two credentials with the same set of private attributes.

### Delegatable

In a delegatable anonymous credential system, participants may use their
credentials anonymously as well as anonymously delegate them to other
participants.

Introduced in [CL06]({{site.baseurl}}/schemes.html#cl06).

### Escrow



### Threshold Issuance

A credential scheme where there can be multiple credential issuers which can
also potentially be Byzantine. (see [Coconut](https://arxiv.org/pdf/1802.07344.pdf)).


</details>
