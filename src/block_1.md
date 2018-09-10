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

**Block 2** In-Depth Spring (JPA, Security)

**Block 3** Where to go from here?


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

## Demystifying Spring: Vocabulary

* Spring Framework
* Spring Boot

<!-- .slide: class="master01 intro" -->

---

### Spring Framework: Spring DI

Inversion of Control: Dependency Injection

----

### Spring Framework: Spring MVC

Model-View-Controller Pattern

----

### Spring Framework: Spring Security

Authentication & Authorization:

* Basic Auth
* Oauth2 / OpenID Connect
* ...

----

### Spring Framework: Spring Data

Simplified Data Access to:

* JPA / Hibernate
* MyBatis
* ORMLite

----

### Spring Framework: Spring Test

Unit & Integration Testing (Support classes)

----

### Spring Framework: Integration of AspectJ

Aspect Oriented Programming

---

### Spring Boot

Library to create standalone Spring applications.

Also a collection of "starter" packages with convention-over-configuration solution.

---

## Spring vs JEE?

![Spring vs JEE](images/spring_vs_jee.png)

----

## Advantages for developers

* Easy to connect a debugger
* Easier to write unit / integration tests
* Easier to distribute and run

----

## Advantages for operators

* No need to choose, configure, operate application servers.
* Less problems with dependencies
