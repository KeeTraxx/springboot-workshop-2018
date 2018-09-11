# Spring Framework

## PUZ Techworkshop 2018

<small>13.09.2018 - tran@puzzle.ch</small>

Note: Authentication, Encoding, Date and Timezone

<!-- .slide: class="master01" -->

---

## Infos

Workshop resources:

https://github.com/KeeTraxx/springboot-workshop-2018

---

## Agenda

**Block 1** What's Spring Framework & Getting Started

**Block 2** Spring MVC + Spring Data + JPA

**Block 3** Spring Test, Exchange & where to go from here?

Note:

Some notes?

<!-- .slide: class="master02" -->

---

## What's Spring Framework?

Wikipedia:

> The Spring Framework is an application framework [...] for the Java platform.

---

## What's equivalent to the Spring Framework?

### Java

* JEE (formerly J2EE)
* Dropwizard
* Spark

----

### Scala

* Play Framework

----

### Ruby

* Ruby on Rails

----

### nodejs

* Express
* Loopback

----

### Python

* Django

----

### PHP

* Laravel
* Symfony

---

## Spring @round Puzzle

* BLS-POC
* HAST-OPR
* HAST-REG
* BLS-FMSX
* BLS-BAU
* SBB-ZLD
* SBB-TMS (TMS-L, FLUX)
* SBB-WFT

---

## Spring Ecosystem

![Desu](images/spring_ecosystem.svg)

Note:

Spring Tool Suite: Eclipse based development environment

Spring Roo: RAD - Rapid Appication Development, CLI based scaffolding helper. Comparable with Angular CLI, Ember CLI, ...

Spring Boot: Spring Standaloen Applications, Embedded Tomcat / Jetty / Undertow, Starter Configurations, Autoconfiguration, Actuators, no code generation and no xml configuration

Spring Data Rest: Automatically expose Spring Data Repositories as REST Endpoints

Spring Mobile: Run code conditionally, depending on the device

Spring Webflow: Flow of application (like forms), usually superseeded by JS applications now

Spring MVC: Model-View-Controller pattern for Spring Applications

Spring Security: Arbitary Security Model

Spring XD: Now Spring Cloud Data Flow

Spring Hadoop

---

### Spring Boot

Library to create standalone Spring applications.

Also a collection of "starter" packages with convention-over-configuration solution.

---

## Why Spring Boot? (1)

![Spring vs JEE](images/spring_vs_jee.png)

---

## Why Spring Boot? (2)

### Advantages for developers

* Easy to connect a debugger

----

* Easier to write unit / integration tests

----

* Easier to distribute and run

---

## Why Spring Boot? (3)

### Advantages for operators

* No need to choose, configure, operate application servers.
* Less problems with dependencies

---

Next up:

[Exercise 1](block_1_exercise.md)