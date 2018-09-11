# Spring Boot Block 2

## PUZ Techworkshop 2018

<small>13.09.2018 - tran@puzzle.ch</small>

<!-- .slide: class="master01" -->

---

## Spring Data JPA

### Introduction

Spring Data JPA facilitates the access to `javax.persistence.*` and still allows you to work with JPA.

---

### How to integrate Spring Data JPA

1. Add `spring-boot-starter-data-jpa` dependency to your Spring Boot Project
2. Implement `@Entity` classes
3. Add Repository interfaces
4. Add custom queries
5. Wire Repository interfaces with your `@Service` or `@RestController`

---

### Implement `@Entity` classes

```java
@Entity
public class Joke {
  @Id
  @GeneratedValue
  long id;

  private String joke;

  // [...] SNIP getters and setters
}
```

---

### Add Repository interfaces

Spring Data abstracts the data access layer for you with `Repository<T, ID>`, `CrudRepository<T, ID>` and `PagingAndSortingRepository<T, ID>`

----

### Example `CrudRepository<T, ID>`

```java
public interface JokeRepository extends CrudRepository<Joke, Long> {}
```

```java
Iterable<T> findAll()
T findById()
T save(T entity)
Iterable<T> saveAll(Iterable<T> entities)
long count()
void delete(S entity)
void deleteAll() / deleteAll(Iteratble<S> entities)
void deleteById()
```

----

### Add custom queries by interface
```java
public interface JokeRepository extends CrudRepository<Joke, Long> {
  Iterable<Joke> findTop3ByOrderByWordsDesc();
  Iterable<Joke> findAllByWords(int words);
}
```

[Documentation](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#repositories.query-methods.query-creation)

----

### Add custom queries with `@Query`

```java
public interface JokeRepository extends CrudRepository<Joke, Long> {
    @Query("SELECT j FROM Joke j WHERE j.joke LIKE %?1%")
    Iterable<Joke> containsWord(String search);
}
```

---

### Wire `Repository` with `@RestController`

```java
@RestController
@RequestMapping("/api/joke")
public class JokeController {

    @Autowired
    private JokeRepository jokeRepository;

    @GetMapping
    public Iterable<Joke> getJokes() {
        return jokeRepository.findAll();
    }

    @GetMapping("top3")
    public Iterable<Joke> top3ByWords() {
        return jokeRepository.findTop3ByOrderByWordsDesc();
    }
}
```