---
layout: post
title: FizzBuzz Domain
category: fizzbuzz
---

Lets build a Software as a Service ([SaaS](https://en.wikipedia.org/wiki/Software_as_a_service))!
First we need to register a public Domain name.

### Domain Names
We'll use Amazon's [Route 53](https://aws.amazon.com/route53/) for this project.
You'll need to sign-up for an Amazon AWS account.
If you haven't used AWS before, you will be eligible for the [Free Tier](https://aws.amazon.com/free)!
Otherwise, use your existing AWS account.

We'll use the console because it is much more accessible for the uninitiated.
It also gives us a lot of useful information to help prevent making mistakes.

### Add a Domain

Once you're logged into the AWS Console, browse to `Services->Route 53`.
It will be located under the `Networking & Content Delivery` section.

![Services Tab]({{ site.url }}/images/aws-services-route53.png)

Next, browse to `Registered domains` from the Dashboard and click the `Register Domain` Button.

![Register Button]({{ site.url }}/images/aws-register-domain.png)

You will presented with a wizard to register your new domain name. 

- First you can search for available Domain names at various TLDs.

- Next, you will need to provide contact information for Whois

- Lastly, you'll verify payment information

### Finished
Once w've registered a new Domain, lets fire up something to point it at!

[Step 2](/): Fire up an instance on Amazon Web Services

- [Project](/fizzbuzz/2017/09/27/fizzbuzz-project.html) Project Page

