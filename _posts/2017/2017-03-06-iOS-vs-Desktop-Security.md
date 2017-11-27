---
layout: page
title: "iOS vs Desktop Security"
subheadline: ""
teaser: "Great explanation from Matthew about the large attack surface presented by a modern desktop machine, and how it compares to mobile devices that were built with security and limited application power in mind. The piece can hopefully explain to the layuser some of the mindfulness that's needed to remain secure. "
author: Morgan
categories:
    - linked
breadcrumb: true
---

From [Matthew Green](https://twitter.com/matthew_d_green) in a piece called _Secure Computing For Journalists_:

> I’m going to devote this post to providing the world’s simplest explanation of why, in the threat model of your typical journalist, your desktop machine isn’t very safe. And specifically, why you’re safer using a modern mobile device — and particularly, an iOS device — than just about any other platform.

Great explanation from Matthew about the large attack surface presented by a modern desktop machine, and how it compares to mobile devices that were built with security and limited application power in mind. The piece can hopefully explain to the layuser some of the mindfulness that's needed to remain secure.

He puts it best here:

> Classical (desktop and laptop) operating systems were designed primarily to support application developers. This means they offer a lot of power to your applications. An application like Microsoft Word can typically read and write all the files available to your account. If Word becomes compromised, this is usually enough to pwn you in practice. And in many cases, these applications have components with root (or Administrator) access, which makes them even more dangerous.
<br>
Modern phone operating systems like Android and iOS were built on a different principle. Rather than trusting apps with much power, each app runs in a “sandbox” that (mainly) limits it to accessing its own files. If the sandbox works, even a malicious application shouldn’t be able to reach out to touch other apps’ files or permanently modify your system. This approach — combined with other protections such as in-memory code signing, hardware secret storage and routine use of anti-exploitation measures — makes your system vastly harder to compromise.

[[via Cryptography Engineering](https://blog.cryptographyengineering.com/2017/03/05/secure-computing-for-journalists/)]

---
<p align="right">Typed on ErgoDox Test Board</p>
