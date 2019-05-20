---
layout: post
title: Federated authentication with Sitecore 9.0
---

This post is intended to help someone who is struggling with making federated authentication (in my case, OpenID) work seamlessly with Sitecore 9.0 (for me, 9.0.2), and realizes there is little to no good documentation on this integration. The official Sitecore documentation, as you by now have probably discovered, is good at walking through step-by-step configuration changes (just like the "patch" upgrades...), but provides almost no code examples.

My intent is to document my own personal journey with this integration, and at at the same time hopefully help you, lost developer, find your way.

### The Beginning
