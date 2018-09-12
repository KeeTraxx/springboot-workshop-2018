# Block 2: Exercise

## PUZ Techworkshop 2018

<small>13.09.2018 - tran@puzzle.ch</small>

<!-- .slide: class="master02" -->

---

## Goals

1. Implement a JPA Entity
2. Implement a Spring Data `CrudRepository<T, ID>`
3. Implement a `@RestController` that leverages the `CrudRepository`
4. Integrate Swagger UI
5. Bonus: Fill the database with data at start using `@PostConstruct`
6. Bonus: Write some additional queries
7. Bonus: Implement a pageable api using `PagingAndSortingRepository`

---

## Step 1: Implement a JPA Entity

Example:

```java
@Entity
public class PuzzleMember {
    @Id
    @GeneratedValue
    long id;

    private String firstName;
    private String lastName;

    private int coffeeConsumption;

    // [Constructors, Getters, Setters...]
}
```

Optional: Use Lombok to lessen boilerplate code.

---

## Step 2: Implement a Spring Data `CrudRepository<T, ID>`

Look at [Block 2 slides](block_2.md#/4)

---

## Step 3: Implement a `@RestController`

Look at [Block 2 slides](block_2.md#/5)

---

## Step 4: Integrate Swagger UI (1)
Add to `build.gradle`

```groovy
compile('io.springfox:springfox-swagger2:2.9.2')
compile('io.springfox:springfox-swagger-ui:2.9.2')
```

----

## Step 4: Integrate Swagger UI (2)
Create `/src/main/java/.../configuration/SwaggerConfig.java`

```java
@Configuration
@EnableSwagger2
public class SwaggerConfig extends WebMvcConfigurationSupport {
    @Bean
    public Docket apis() {
        return new Docket(DocumentationType.SWAGGER_2)
                .select().apis(RequestHandlerSelectors.any())
                .paths(PathSelectors.ant("/api/**"))
                .build();
    }

    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addRedirectViewController("/", "swagger-ui.html");
    }


    @Override
    protected void addResourceHandlers(ResourceHandlerRegistry registry) {
        registry.addResourceHandler("swagger-ui.html")
                .addResourceLocations("classpath:/META-INF/resources/");

        registry.addResourceHandler("/webjars/**")
                .addResourceLocations("classpath:/META-INF/resources/webjars/");
    }
}
```

----

## Step 4: Integrate Swagger UI (3)

Check Swagger UI

Open http://localhost:8080/

---

## Bonus - Step 5: Fill the database with data at start using `@PostConstruct`

---

## Bonus - Step 6: Write some custom queries

Look at [Block 2 slides](block_2.md#/4/2)
