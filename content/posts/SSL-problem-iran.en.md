---
title: "What happened to the SSL certificates of Iranian websites?"
date: 2026-08-18T20:10:30+03:30
draft: false
categories:
- Iran
tags:
- Security
---
Technically, **anyone can stand up a certificate authority (CA) on their own machine with a few commands** and issue an SSL certificate for any domain on the internet. The real issue is not generating a certificate file. It is the **chain of trust** that browsers actually rely on.

**How an SSL certificate is issued and trusted**

* **Trusted Root Store:** Browsers (Chrome, for example) and operating systems ship with a default list of globally trusted authorities (Let’s Encrypt, DigiCert, Google Trust Services, and others). Those organizations get into that list only after strict security audits by the CA/Browser Forum.
* **Validation chain:** When you open a site, the browser checks whether the site’s certificate ultimately chains up to one of the Root CAs already trusted on the user’s system. If even one link in that chain is unknown, the browser shows a red warning.

---

**Why this happened to Bank Mellat**

The second image shows why:

* **A domestic issuer:** The site’s certificate was issued by `Islamic Republic of Iran Root CA-G3` (Iran’s state root CA), not by an international authority.
* **No global trust:** For structural, sanctions-related, and audit reasons, none of the major vendors (Google, Apple, Microsoft, Mozilla) have put this Iranian root into their operating-system or browser trust stores.
* **Why the bank uses it:** Because of frozen accounts and the repeated revocation of international certificates for Iranian government and banking sites under sanctions, these organizations have moved to domestic CAs.

---

**The security consequence of this error**

Traffic to such a site may still be encrypted with standard algorithms, but the browser has not verified the identity of the other party. If a user, at the site’s request, manually installs that Root CA on their operating system and marks it as trusted, the browser warning goes away. Doing that, however, gives the holder of that root key the ability, if they choose, to decrypt or inspect the user’s encrypted traffic in the middle of the path (a man-in-the-middle attack) without triggering a warning.

Russia and China have taken similar approaches, with different outcomes, in dealing with the global certificate system. And the answer to that last question is exactly the dangerous part: **yes, trusting a Root CA lets that authority mint a certificate for any site on the internet and intercept your traffic.**

---

**Russia: a national CA after sanctions**

* **What happened:** After the war in Ukraine began in 2022 and Russian financial institutions were sanctioned, international CAs (DigiCert among them) stopped issuing and renewing certificates for large Russian banks such as Sberbank and VTB. The Russian government launched its own national CA (**Russian Trusted Root CA**) through the state services portal (Gosuslugi).
* **Did Google and the major vendors trust it?** **No.** Google, Apple, Microsoft, and Mozilla never added that root to their browsers or operating systems.
* **Russia’s current workaround:** The government asks users either to install the root certificate by hand on Windows, macOS, or Linux, or to use Russian browsers such as **Yandex Browser** and **Atom**, which ship with that certificate built in.

---

**China: a case of eviction and distrust**

* **What happened:** For years China had a national CA called **CNNIC**. Unlike Iran and Russia, it was initially trusted by Google, Microsoft, and Mozilla and was present on systems worldwide.
* **Did the major vendors trust it?** In 2015 it emerged that a subordinate CA of CNNIC in Egypt had issued unauthorized certificates for Google’s own domains (which would have enabled a man-in-the-middle attack). Google and Mozilla immediately **distrusted** CNNIC and removed its root from Chrome and Firefox.
* **China’s current workaround:** Chinese companies use standard, commercially trusted global CAs for international traffic, and for their more closed domestic ecosystem they rely on Chinese browsers such as QQ Browser and 360 Secure Browser.

---

**What happens if you trust this certificate?**

Installing a CA into the operating system’s **Trusted Root Store** gives that authority the highest level of cryptographic privilege:

* **Certificates for every domain:** The X.509 protocol lets a Root CA issue a certificate for **any domain on the web** (`google.com`, `instagram.com`, corporate and government domains included), unless name constraints were explicitly applied when the CA was created — which they usually are not.
* **Man-in-the-middle attacks:** If the holder of that Root CA’s private key sits on your network path (an ISP, or at a national level) with an SSL inspection proxy, it can intercept your request to any foreign site, hand your browser a “valid” certificate signed by its own root, decrypt and read the encrypted traffic in the middle (passwords, chats, sensitive data), then re-encrypt it toward the destination server.
* **The browser warning disappears:** Because the browser now treats that root as trusted, it shows the ordinary lock icon, and you will not know the traffic is being intercepted.
