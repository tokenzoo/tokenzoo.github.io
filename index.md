---
layout: default
title: Anonymous credentials zoo
banner: bull.jpg
---

Welcome to the anonymous credentials zoo!

## What are anonymous credentials?

Anonymous credentials help anonymously authorizing users.


![text](assets/img/user.png)


_A privacy-aware user wants to authenticate to a paid service, but without logging in.
Anonymous credentials can help authenticating that she's allowed to use a service without revealing any information about their identity, and make application-level tracking impossible._

There are two main types of anonymous credential systems:

- Tokens, which are lightweight, one-show anonymous credentials that encode a single message and can be used only once;
- Credentials, which are more structured, allow for embedding different attributes, and can be used multiple times.

## Website structure

In this website we attempt to organize the vast universe of anonymous credentials:

- We present published anonymous credential [schemes]({{site.baseurl}}/schemes.html) that can be used for various use cases
- We provide brief details on the mathematical [primitives]({{site.baseurl}}/primitives.html) that underlay these constructions
- We categorize the various [properties]({{site.baseurl}}/properties.html) that anonymous credential schemes can support
- We provide a [bibliography]({{site.baseurl}}/bibliography.html) enumerating papers, articles, and other resources around anonymous credentials
- We discuss the [engineering]({{site.baseurl}}/engineering.html) and deployment aspects of anonymous credentials [XXX trust token API, encodings, etc.]

## This is Work In Progress!
## Please [submit a PR](https://github.com/tokenzoo/tokenzoo.github.io) if you want to improve things!
