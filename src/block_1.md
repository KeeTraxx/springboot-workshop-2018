# Spring Boot

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

1. Block 1: Spring@Puzzle & Getting Started
2. Block 2: In-Depth Spring (JPA, Security)
3. Block 3: Where to go from here?

Note: 

Some notes?

<!-- .slide: class="master02" -->

---

## Spring @round Puzzle - where are we?

* BLS-POC
* HAST-OPR
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

### Spring Framework

Core ideas:

* Aspect Oriented Programming (AspectJ)
* Authentication & Authorization (Spring Security)
* Data Access (Spring Data)
* Inversion of Control: Dependency Injection (Spring DI)
* Model-View-Controller Pattern (Spring MVC)
* Unit & Integration Testing (Support classes)

---

### Spring Boot

Library to create standalone Spring applications.

Also a collection of "starter" packages with convention-over-configuration solution.

----

* spring-boot-starter-actuator
* spring-boot-starter-web
* spring-boot-starter-data-jpa
* spring-boot-starter-test

----

* spring-boot-starter-websocket
* spring-boot-starter-mail
* spring-boot-starter-hateoas
* spring-boot-starter-webflux

---

## Spring vs JEE?

![Spring vs JEE](images/spring_vs_jee.png)

https://www.slideshare.net/BenWilcock1/microservices-java-ee-vs-spring-boot-and-spring-cloud

----

Developers: 
> We just want to build, test and ship our application!

---

## Getting Started with Spring Boot

<!-- .slide: class="master02 intro" -->

---

## Manual Maven or Gradle build

https://spring.io/guides/gs/spring-boot/

## Spring Initialzr

https://start.spring.io/

---

## Manual Maven or Gradle build

Go through the tutorial at

https://spring.io/guides/gs/spring-boot/

![](images/own_build.png) <!-- .element style="max-width: 40%;" -->

---

## Spring Intialzr

https://start.spring.io/

Prepares a Maven or Gradle project with all dependencies.

![](images/initialzr.png) <!-- .element style="max-width: 40%;" -->

---

## Why Spring Intialzr

* You can bootstrap new versions (opposed to copy/paste from an old or a seed project)
* Dependencies are usually handled well (opposed to copying dependency snippets from SO or similar)
* ==> Saves you time!

---

## Our first Spring Boot Application

* Select `DevTools`, `Web`, `Actuator`, `JPA` dependencies
* Generate Project
* `unzip myapp.zip`
* 1st terminal: `./gradlew build --continuous`
* 2nd terminal: `./gradlew bootRun`

---

## Static web resources

Create `src/resources/static/index.html`

Open `http://localhost:8080/`

---

## Spring externalized configuration

External configuration can be injected in Spring `@Bean`s (which encompasses almost everything in the Spring Framework) with `@Value`

Syntax: `@Value(${my.configuration.var:Default Value})`

Order (simplified):

1. Command line arguments (`java -jar myapp.jar --app.message=bonjour`)
2. JSON Configuration in SPRING_APPLICATION_JSON
3. Java System Properties (from `System.getProperties()` and `System.setProperty(...)`)
4. OS Environment variables (`APP_MESSAGE=bonjour`)
5. Profile specific outside jar (`application-{profile}.properties / .yml`)
6. Profile specific inside jar (`application-{profile}.properties / .yml`)
7. Main app configuration file (`application.properties / .yml`)

----

More details:

https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-external-config.html#boot-features-external-config

---

### Example

```
@RestController
@RequestMapping("/api/hello")
public class HelloController {

  @Value("${app.message:No message defined}")
  private String message;

  @GetMapping
  public String sayHello() {
      return message;
  }
}
```

---

## Actuators

https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#production-ready-endpoints

----

* [actuator/health](http://localhost:8080/actuator/health)
* [actuator/auditevents](http://localhost:8080/actuator/auditevents)
* [actuator/beans](http://localhost:8080/actuator/beans)
* [actuator/configprops](http://localhost:8080/actuator/configprops)
* [actuator/env](http://localhost:8080/actuator/env)
* [actuator/httptrace](http://localhost:8080/actuator/httptrace)

----

* [actuator/info](http://localhost:8080/actuator/info)
* [actuator/loggers](http://localhost:8080/actuator/loggers)
* [actuator/metrics](http://localhost:8080/actuator/metrics)
* [actuator/mappings](http://localhost:8080/actuator/mappings)
* [actuator/scheduledtasks](http://localhost:8080/actuator/scheduledtasks)
* [actuator/sessions](http://localhost:8080/actuator/sessions)

---

### Discussion

![mustache](http://www.bluemaize.net/im/baby-girls-clothing-shoes/i-mustache-you-a-question-5.jpg)

<!-- .slide: class="master04" -->
