# Spring Boot Block 2
## PUZ Techworkshop 2018

<small>13.09.2018 - tran@puzzle.ch</small>

<!-- .slide: class="master01" -->

---

## Our first REST Controller

Create

`src/main/java/.../controller/MembersController.java`

```
@RestController
@RequestMapping("/api/heroes")
public class HeroController {
    @GetMapping
    public List<String> getHeroes() {
        return Arrays.asList("Superman", "Batman");
    }
}
```

Try it out:
http://localhost:8080/api/members

---

## Swagger UI (1)
Add to `build.gradle`

```
compile('io.springfox:springfox-swagger2:2.9.2')
compile('io.springfox:springfox-swagger-ui:2.9.2')
```

---

## Swagger UI (2)
Create `/src/main/java/.../configuration/SwaggerConfig.java`

```
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
    protected void addResourceHandlers(ResourceHandlerRegistry registry) {
        registry.addResourceHandler("swagger-ui.html")
                .addResourceLocations("classpath:/META-INF/resources/");

        registry.addResourceHandler("/webjars/**")
                .addResourceLocations("classpath:/META-INF/resources/webjars/");
    }
}
```

---

## JPA

<!-- .slide: class="master02 intro" -->

Spring JPA Repositories are Java interfaces.

* `Repository<PojoClass, IDClass>`
* `CrudRepository<PojoClass, IDClass> extends Repository`
* `PagingAndSortingRepository<PojoClass, IDClass> extends CrudRepository`

---

## Step 1: Add a JPA Entity class

```
@Entity
public class PuzzleMember {
  @Id
  @GeneratedValue
  private Long id;
  private String firstName;
  private String lastName;
  private int coffeeConsumption;

  [... Getters and Setters]
}
```

## Step 2: Add a repository

```
public interface PuzzleMemberRepository extends CrudRepository<PuzzleMember, Long> {

}
```

## Step 3: Inject the Service to your Controller

```
@RestController
@RequestMapping("/api/members")
public class PuzzleMember {
  @Autowired
  private PuzzleMemberRepository repo;

  @GetMapping
  public Iterable<PuzzleMembers> getAllMembers() {
    return repo.findAll();
  }
}
```

---

## CrudRepository methods

* findAll()
* findById()
* save(S entity)
* saveAll(Iterable<S> entities)
* count()
* delete(S entity)
* deleteAll() / deleteAll(Iteratble<S> entities)
* deleteById()

---

## Add your own methods

By interface name:

```
Iterable<PuzzleMember> findByFirstName(@Param("firstName") String firstName);
```

----

By interface name (advanced):
```
Iterable<PuzzleMember> findTop3ByOrderByCoffeeConsumptionDesc();
```

Black magic explained: https://docs.spring.io/spring-data/jpa/docs/current/reference/html/

----

By custom query:

```
@Query("SELECT m FROM PuzzleMember m WHERE m.coffeeConsumption >= ?1")
Iterable<PuzzleMember> findByCoffeeConsumption(@Param("minimumConsumption") int minimumConsumption);
```