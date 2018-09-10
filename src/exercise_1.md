# Block 1: Exercise

<!-- .slide: class="master02 intro" -->

---

Goals:

1. Use [Spring Initialzr](https://start.spring.io/) to generate a project
2. Static web resources
3. Spring externalized configuration
4. First basic REST Endpoint
5. Deploy to Openshift
6. Get to know Spring Actuators

---

## Step 1: Spring Intialzr (1)

https://start.spring.io/

Prepares a Maven or Gradle project with all dependencies.

![](images/initialzr.png) <!-- .element style="max-width: 40%;" -->

---

## Step 1: Spring Intialzr (2)

* Select `DevTools`, `Web`, `Actuator`, `JPA` dependencies
* Generate Project
* `unzip myapp.zip`
* Run the project using your IDE or `./gradlew bootRun`

---

## Step 2: Static web resources

`echo "hello world" > src/resources/static/index.html`

Open `http://localhost:8080/` in your browser.

---

## Step 3: Spring externalized configuration

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

### Step 4: Rest Controller Example

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

## Step 5: Deploy to Openshift

* Create a project `oc new-project pitc-techworkshop-kt`
* Create a new app `oc new-app --name=web keetraxx/s2i-gradle-springboot~.`
* Create a route `oc expose svc/web`
* Start a build `oc start-build web --from-dir=.`

---

## Step 6: Actuators

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
