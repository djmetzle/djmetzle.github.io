---
layout: post
title: FizzBuzz As a Service
category: fizzbuzz
---

Lets build a Software as a Service ([SaaS](https://en.wikipedia.org/wiki/Software_as_a_service))!
FizzBuzz is a classic easy programming exercise, used in interviews to filter candidates for basic programming proficiency.

The nature of [FizzBuzz](https://en.wikipedia.org/wiki/Fizz_buzz) can make it a hard problem to solve.
Many a joke has been made about writing an [Enterprise Grade FizzBuzz](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition).
My friend [danielj41](https://github.com/danielj41) wrote an almost incomphrensibly complicated [implementation](https://github.com/danielj41/monad-buzz) using every advanced programming concept he could manage. [Addition](https://github.com/danielj41/monad-buzz/issues/15)? Too much mutation he insists.

### This Project

Lets build a nice web app and API around FizzBuzz. From now on, FizzBuzz can be a solved with a single call to cURL.

Along the way, we should find the skeleton for building a simple web app. We'll use some specific technologies, but the blueprint should stay about the same for any cool new web service you might want to build

- [Step 1](/fizzbuzz/2017/09/28/fizzbuzz-domain.html) Register a Domain name
- [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html) Fire up an instance on Amazon Web Services
- [Step 3](/fizzbuzz/2017/11/01/fizzbuzz-dns.html) Add DNS Records
- [Step 4](/) Configure Security Groups and Networking
- [Step 5](/) Configure Nginx
- [Step 6](/) Let's Encrypt!
- [Step 7](/) Some Hardnening
- [Step 8](/) Hello Flask
- [Step 9](/) Hello FizzBuzz

`...`

[Step 10](/) Profit!
