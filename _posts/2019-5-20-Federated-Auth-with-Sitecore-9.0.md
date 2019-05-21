---
layout: post
title: Federated authentication with Sitecore 9.0
---

This post is intended to help someone who is struggling with making federated authentication (in my case, OpenID) work seamlessly with Sitecore 9.0 (for me, 9.0.2), and realizes there is little to no good documentation on this integration. The official Sitecore documentation, as you by now have probably discovered, is good at walking through step-by-step configuration changes (just like the "patch" upgrades...), but provides almost no code examples.

My intent is to document my own personal journey with this integration, and at the same time hopefully help you, lost developer, find your way.

### The Beginning
My team started working on this project at the end of 2017 (a year and half ago, at the time of this writing). This project is a conversion of a traditional ASP.NET MVC website to Sitecore, with an API that acts as a middleman between Sitecore and a POS system. One of the first features developed was the federated auth layer using [IdentityServer3](https://github.com/IdentityServer/IdentityServer3). I did not have much experience with federated auth before this project, and initially had no involvement in developing this feature. Eventually some changes needed made and I was able to dig in, but the core login functionality has been in place as originally written for the entire life of the project. 

The specifics of our implementation worth noting at this point are as follows:
 - we are using Microsoft's OpenID middleware
 - we have some custom data being passed back as a claim in the form of a JSON string
 - we are using `[Authorized]` decorators to force authorization
 - we are calling `AuthenticationManager.GetActiveUser()` to log in users after authentication

### The Scaling Problem
The only reason I'm writing this post is because once the login feature when live, we had a problem: As soon as ~500 users were simultaneously logged in, a Sitecore table was locking up, slowing everything down to the point that we had to roll back. Apparently, a core table contained a single record to capture user data for _every_ logged in user, associated with a common `sc_local` key. To me, this immediately raised some red flags about our custom login implementation. 

### The Frantic Search


### The Enlightenment

