---
layout: post
title: Reactive Architecture != Reactive Programming
---


- Reactive Systems and Reactive Programming are often misunderstood. 
- They are not equivalent
- Reactive Systems apply the **Reactive Principles** at the architectural levels.
- Reactive Programming can be used to build Reactive Systems (or not)

## Reactive Architecture

[https://www.reactivemanifesto.org/](https://www.reactivemanifesto.org/)

- The Reactive Manifesto principles are intrinsic to the design and architecture of Reactive Systems.
- All major architectural components interact in a Reactive way.
- Reactive Systems are separated along asynchronous boundaries.
- Eg. Reactive Microservices.


### Reactive Principles

![](https://i.imgur.com/lKZahOx.png)

- **Responsive**: A Reactive System consistently responds in a timely fashion.
  - _Responsiveness_ is the cornerstone of usability.
  - Systems must respond in a fast an consistent fashion if at al possible.
  - Responsive systems build user confidence.
- **Resilient**: A Reactive System remains responsive, even when failures occur.
  - _Resilience_ provides responsiveness, despite failures.
  - Achieved through replication, isolation, containment, delegation.
  - Failures are isolated to a single Component.
  - Recovery is delegated to an external Component.
- **Elastic**: A Reactive System remains responsive, despite changes to system load.
  - _Elasticity_ provides responsiveness, despite increases (or decreases) in load.
  - Implies zero scaling techniques can be used to support elasticity.
  - predictive auto scaling techniques can be used to support elasticity.
  scaling up provides responsiveness during peak, while scaling down improves cost effectiveness.
- **Message Driven**: A reactive System is built on foundation of async, non-blocking messages.
  - Responsiveness, Resilience, Elasticity are supported by a _Message Driven Architecture_.
  - Messages are asynchronous and non-blocking.
  - Provides Loose coupling, isolation, location transparency.
  - Resources are consumed only while active.


## Reactive Programming

- Reactive Programming can be used to support the construction of Reactive Systems.
- Support breaking problems into small, discrete steps.
- Steps are executed in an **async/non-blocking** fashion, usually via a _callback mechanism_.
- Eg. Futures/Promises, Streams, RxJava/RxScala
- A system that uses Reactive Programming is not necessarily a Reactive System.

#### The Actor Model
  - The _Actor Model_ is a programming paradigm that supports construction of Reactive Systems.
  - It is _Message Driven_.
  - Abstractions provide _Elasticity_ and _Resilience_.
  - It can be used to build _Responsive_ Software.

![](https://i.imgur.com/J2qDGAf.png)

  - All computation occurs inside of _Actors_.
  - Each Actor has an **address**.
  - Actors communicate only through **asynchronous messages**.
  - The _Message Driven_ nature of Actors supports _Location Transparency_.
  - Actors communicate using the same technique, regardless of location.
  - _Local_ vs _Remote_ is mostly configuration.
  - _Location Transparency_ enables actors t be both _Resilient_ and _Elastic_.

