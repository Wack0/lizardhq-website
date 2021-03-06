---
layout: post
title: "Response to Decision Group press release about security vulnerabilities in E-Detective Lawful Interception System"
date: 2015-06-25
categories:
---

*By Mustafa Al-Bassam.*

Two weeks ago we posted a [security advisory](../../../2015/06/14/e-detective.html) detailing severe security flaws in E-Detective, a "lawful" communications interception system. The vendor is a company called Decision Group and they [claim on their website](http://www.edecision4u.com/HTTPS-SSL.html) that their software is used by over 100 law enforcement agencies.

A few days ago they posted a [press release](http://www.edecision4u.com/2015news/20150618_New%20Release.html) to respond to an [IBTimes article](http://www.ibtimes.co.uk/e-detective-spying-tool-used-by-over-100-law-enforcement-agencies-has-major-security-holes-1506447) that covered the security flaws.

The mere fact that they responded to a news article about the security flaws instead of the original security advisory is telling of their attitude to security. An attitude that is unfortunately too common: that security is seen as an externality that affects its customers more than the company itself, so resources should only be devoted to it if it's a public relations issue.

Nevertheless, their response is very much a non-response. It fails to express responsibility for the security holes, and instead deflects the responsibility on their customers.

Excusing their broken English, here's a point-by-point response to their press release.

>Actually we are fully aware of such security concern since 4 years ago when our client asked to enhance the security level of E-Detective system."

The fact that they've been fully aware of these security flaws for 4 years and failed to do something about them until recently is not exactly redeeming. That only makes it much, much worse.

By their own admission they admit that third parties (their clients) have known about these vulnerabilities. Their clients (one of whom they claim to be the National Security Bureau of the Republic of China, which is effectively the Taiwanese NSA) buy their software for the purpose of degrading security. One can only shudder to imagine how many times these flaws have been attempted to be exploited for the purpose of collecting intercepts from other customers.

>The most important guideline of E-Detective deployment is that E-Detective should be deployed in the closed network domain without Internet access to outside world. This network domain should be also isolated from other corporate or government service network segment. By this way, only few authentic staff can access the internal system.

A great example of how a false sense of security can be dangerous. Isolating services in their own network doesn't fix the security flaws nor make them impossible to exploit - it just makes it harder.

There are countless ways that a private network can be compromised. No matter how tight your network is. To get any reasonable work done staff members will move data in and out of the network, even if your network is disconnected from the Internet. There are many entry points into a network, something which shouldn't really need to be explained to a company that sells surveillance software for a living if they are competent.

Software compartmentalisation and network isolation is a good security practice, but it's not a substitute for fixing vulnerabilities or an excuse to run dangerously insecure software.

Even if one was to make the (false) assumption that running E-Detective on an isolated network prevents vulnerabilities affected by it from being exploited: how many of those "100+" customers actually follow these guidelines or have a sane network setup that allows them to do this kind of isolation?

Furthermore, the actual function of E-Detective means that it can never be on a fully isolated network. There will always be an entry point. E-Detective intercepts communications by using a man-in-the-middle proxy. That proxy will need to be connected to the network that the customer wants to intercept communications from. Based on the case studies that they list on their website, that network will also probably be connected to the Internet.

Unless a human being is manually transferring data using external storage from the proxy to the E-Detective system, then the system will probably also be in some way connected to the proxy.

>Since all users of E-Detective are of 4 types: operator, administrator, auditor and datamvr. Operator has the authorized right to input queries and view the scope of intercepted data by his/her own right. Administrator can have authorized right to conduct the operation of system backup, user management, and software system tuning…etc. Auditor has the only right to check and view all log files in the system. The last type of user is only for data transport between different systems, and it cannot be used for system access. None of these users has the superuser right of root. In most cases, root is basically set to hibernation status after system is activated by license under customer SLA request in order to terminate security backdoor.

All of this is made useless by a vulnerability that was discovered after the publication of the original security advisory. It turns out that features that the root user has access to are hidden from the menu of other users, but other users can still access those features by manually navigating to each feature's page.

Even if the root user is deactivated after installation in "most cases", this still doesn't address the fact that the system backup feature uses a static key, which can be exploited to perform remote code execution.

>Besides, E-Detective can be integrated with OTP server for more secured access control, and all logon access record will be reviewed in OTP server for auditing. Biometric access mechanism module with fingerprint can be also available by customer request, but it depends on whether the fingerprint reader is supported on user workstation.

The system is so dangerously insecure beyond easy repair at this point that we feel sorry for anyone that has to trust it with their biometric data.

>After all, E-Detective system is used by our customer for network forensic purpose, such as internal data leakage protection, cyber evidence collection and lawful interception. System security is always the top priority for our customer. All the vulnerabilities mentioned in the news by International Business Times have been fixed several months ago. “Customer IT security is always our top concern,” said Casper Kan Chang, CEO of Decision Group, “and we have already fixed all the vulnerabilities in this current version of E-Detective for more than 11 months.” For those existing customers with old version of system still has concern, Decision Group will update it for free without hesitation."

If IT security is "always" their top concern, why did it take them 3 years to (claim to) fix these vulnerabilities? Have they proactively contacted the customers that are running insecure versions of their software, or are they waiting for their customers to contact them?
