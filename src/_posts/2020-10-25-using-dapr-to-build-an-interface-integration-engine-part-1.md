---
category: healthcare interface
tags:
  - Dapr
date: 2020-10-25
title: Using Dapr to build an Interface/Integration Engine for healthcare solutions - Part 1
vssue: false
---

Using [Dapr](https://dapr.io/) to build an Interface/Integration Engine for healthcare solutions - Part 1

<!-- more -->

## Using Dapr to build an Interface/Integration Engine for healthcare solutions - Part 1

### What's an interface engine, and a bit of background info

Many years ago I worked at a company that provided healthcare solutions, primarily to Accident and Emergency Departments (A+E) in hospitals. Hospitals did not (still don't) have a single provider for all their software solution needs. They engaged different suppliers who provided highly specialised, best-of-breed applications to run in each of its departments e.g. Radiology, Labs, Pharmacy, A+E, In-patient etc.

Consider a patient attending a hospital, it's highly unlikely that they would be seen in just one department. They need to be assessed, have lab tests, maybe xrays, or even admitted. There is a lot of important data on the patient that gets collected, and that needs to be available immediately, from anywhere. When a hospital has different applications in each department, that data needs to be shared. Imagine a scenario where patient data is not shared between the departments. At best, an incredibly frustrating journey for the patient as they have to register and provide the same data to each department they visit. Or the worst case scenario where you get missing or incomplete information, negatively impacting the outcome of the patient's vist.

So all these applications have to share patient data, and most did this via an interface or integration. An interface is basically just a means of exchanging information. An interface has specifications on how to exchange information (text files, web services, TCP/IP etc) and how it was structured, or formatted (XML, HL7, FHIR etc). For the A+E solution, we built an Interface Engine that allowed users to input the specifications for multiple interfaces via configuration screens, and that then took that configuration and run each interface as a separate service.

At the time, our product was built in Visual Basic 6 (VB6), and thats what we used to build the engine. We had to support the different protocols and formats for interfaces. It was not exactly straightforward, there's many things that are not easy to do in VB6, like threading (anyone dealt with marshalling?), or windows services, or does it really need all that memory, or can it scale out to this farm, or please please please can it just try run like forever? Running in older tech also made a lot of other MUNDANE things difficult, like test driven development, interfacing with newer applications, monitoring, logging or just being able to build new stuff. Great testament to VB6 though, it still runs and is still supported!

Anyway, that was a long time ago, or so I thought and then along comes [Dapr](https://dapr.io/)...

### What's Dapr?

I watched a session on MSBUILD introducing something new called [Dapr](https://dapr.io/). What's dapr?...straight from the website, "...An event-driven, portable runtime for building microservices on cloud and edge...". Sounds cool. Then there was a demo, dapr watching for and logging tweets, I dont think it got to [mine](https://twitter.com/MaringaM/status/1262827963755696128), but I thought, ok looks good. It logged everything, and it could monitor stuff, and on reading further it could do more, like encrypt, scale out, was configuration driven and had really MUNDANE stuff. All you had to do was code what you wanted to do with the tweet.

Wait, what, just deal with the tweet? Could I use this runtime as the core of an interface engine, where I dont need to worry about logging, monitoring, encrypting, scaling and maybe just process an interface message? If I had to build an interface engine again, would I use Dapr and would it resolve all the previous pain points? There's only one way to find out...

### Let's build an Interface Engine using Dapr!

So let's build an interface engine using Dapr.

I'm not sure how long this is going to take, so I'll put this into a series of blog posts. Considering what an interface does, each post will deal with the following items I have identified so far, and which will probably be expanded as I go along:

- overall architecture, installation
- interface definition and configuration
- connection protocols, TCP/IP and Web Services for now, invocation
- message processing
- scaling, logging, encryption

### Next
