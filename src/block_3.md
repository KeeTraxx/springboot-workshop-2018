# Spring Boot Block 3

## Spring Boot Testing

<small>13.09.2018 - tran@puzzle.ch</small>

<!-- .slide: class="master03" -->

---

## Spring Boot Testing

1. Unit Testing
2. Integration Testing
3. e2e Testing?

---

## Unit Testing with Spring Boot

### What's a unit test?

* Tests a single class
* Everything outside it is mocked.

---

### What's a integration test?

* Tests multiple classes working togehter.

---

### What's an e2e test?

* Tests using a mocked browser engine.

---

## spring-boot-starter-test

* JUnit
* Spring Test
* AssertJ
* Hamcrest
* Mockito
* JSONassert
* JsonPath

---

### Example: Isolated `@RestController` test

```java
import static org.hamcrest.Matchers.is;
import static org.mockito.BDDMockito.given;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.post;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.jsonPath;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import static org.springframework.test.web.servlet.result.MockMvcResultHandlers.*;

@RunWith(SpringRunner.class)
@WebMvcTest(PuzzleMemberController.class)
public class PuzzleMemberControllerTests {

    @Autowired
    private MockMvc mvc;

    @MockBean
    private PuzzleMemberRepository repository;

    private PuzzleMember mockPuzzleMember = new PuzzleMember("Hans", "Muster", 3);

    @Test
    public void incrementCoffeeConsumption() throws Exception {
        given(repository.save(mockPuzzleMember)).willReturn(mockPuzzleMember);
        given(repository.findById(42L)).willReturn(Optional.of(mockPuzzleMember));

        mvc.perform(post("/api/puzzle-members/drink-coffee")
                .contentType(MediaType.TEXT_PLAIN)
                .content("42"))
                .andExpect(status().isOk())
                .andExpect(jsonPath("$.coffeeConsumption", is(4)))
                .andExpect(jsonPath("$.firstName", is("Hans")))
                .andExpect(jsonPath("$.lastName", is("Muster")));
    }

    @Test
    public void noUserFound() throws Exception {
        mvc.perform(post("/api/puzzle-members/drink-coffee")
                .contentType(MediaType.TEXT_PLAIN)
                .content("43"))
                .andDo(print())
                .andExpect(status().is4xxClientError());
    }
}

```

---

### Example: Integration test

---

### Good to know

* Put a `application.properties` in `/src/test/resources`
* Tests will always expect all `@Bean`s to be present or mocked

---

## Free time

* Talk among yourselves
* Explore more Spring Boot stuff:
 - WebFlux
 - WebSockets
 - Spring Cloud
 - Spring Hateoas
 - Spring Security