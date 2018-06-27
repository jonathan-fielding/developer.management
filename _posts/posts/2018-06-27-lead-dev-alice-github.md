---
title: The Container Operator's Manual - Lead Dev UK 2018
date: 2018-06-27
author: Jonathan Fielding
layout: post
permalink: /containers-operator-manual-talk-by-alice-goldfuss/
categories:
  - Miscellaneous
---

I have decided to write up some of the talks from Lead Dev UK 2018 that I found really interesting. The first being a talk from Alice Goldfuss, an SRE from Github who started the day with a talk on "The Container Operator's Manual".

Alice introduced the talk talking about Car Ads. How they open with a beautiful mountainside, make you want the car however at the bottom they have the the small text saying "Laboratory settings". Most container talks are the same, they give you a half finished tutorial. She wants less Docker 101 and more Docker WTF. 

Most talks lead you to think containers work like this:

* First you have your host, then your OS
* then your container daemon
* then you have your containers

But this is lies.

When you build a dokerr file you make a tarball. When you deploy it is is unpacked and run as a process. 

### Were going through 4 lessons

1. Containers have stengths

   1. they lie in ephemeral disposable processes. By this Alice explained she mean's stateless applications. 
   2. Catainers are not boxes, boxes are lies. Containers are portable so you can use it everywhere and you dont have to worry about having the library versions to run it. This makes it easy to itterate and upgrade. You want to iterate fast and containers can help you there.
   3. Disaster Recovery, if everything is containarised, everything is deployed the same way to the same place. 
   4. Testing environments, what are testing environments but just different versions of your application.

2. Containers have weaknesses

   1. Stateful applications, in particular Databases. Normally if people say this to Alice she will reply "Are you Google?". Normally the answer is No. 
   2. Reasons to try are faster provisioning, stability, recovery. But you can get all these benefits from a cloud provider, and its cheaper than the cost of building and maintaining your own solution.
   3. Normally you can end up network bound and end up with requring even more hardware.

3. Containers need friends

   1. Its never just containers, you have to glue things together to build platform
   2. You can build the container tarballs locally, you could use docker for that and then deploy it to something out.
   3. Management, how will you manage clusters?
   4. Networking, how will you handle routing, access control, service discovery? Theres lots of different tools that handle the networking.
   5. Deployment, - how will you deploy to the new container platform?
   6. Monitoring - how will you monitoer your container health?
   7. How will you provison new containers
   8. How will you troubleshoot issues

4. Containers need headcount

   1. Normally one person will say "we need containers" and another person will say "Lets give it to ops".  Lets just give them an extra thing to worry about.

   2. You should build a new team to build the container platform. You need people with the correct skills including:

      * Operations (and know the operartions at your company so they know the skeletons),
      * Deployments and know how deployment works at your company
      * Tooling (someone who will write the tooling that ties everything togehter and integrartes into existing infrastructure)
      * Monitoring,
      * Kernel engineer (someone to look at kernel crashing and the low level) 
      * Networking, someone who understands your networking
      * InfoSec, security in containers is really a first class citizen so you need someone who is passionate about this
      * Internal adoption, someone who will manage relationship with early adopters and can help you manage the migration
      * Project manager to keep the project on track, help motivate the team.

      They don't all need to be dedicated people but the team needs to be minimum of 4 people, ideally 6-8. They need to be empowered to succeed, they need budget to try out cloud instances to iterate faster and they need the space to fail. You need to ensure they have the supoport they need to correctly build out this platform.

## Should we use containers in prod?

Yes if:

- Do you have starteless services?
- Do you have a large platform
- Time, money, people and organisation support

No if:

- Do you have a monolith and few services?
- A small team with no org support?

Remember, they can be tricky, you should try to have funa dn you will get them in the end.