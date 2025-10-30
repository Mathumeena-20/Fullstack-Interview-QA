# 🧪 **1️⃣ What is JUnit and Mockito?**

### ✅ **JUnit**

JUnit is a **Java testing framework** used for writing and running **unit tests**.
Latest version: **JUnit 5 (Jupiter API)**.

* Helps automate code testing.
* Ensures every method works as expected.

### ✅ **Mockito**

Mockito is a **mocking framework** for creating **dummy objects (mocks)** of dependencies.
Used to **isolate and test only one class** without needing real DB, APIs, etc.

---

### 💻 Example:

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;
import static org.mockito.Mockito.*;

class Calculator {
    int add(int a, int b) {
        return a + b;
    }
}

public class CalculatorTest {
    @Test
    void testAddition() {
        Calculator calc = new Calculator();
        assertEquals(5, calc.add(2, 3));
    }
}
```

✅ **Explanation:**
`@Test` marks a method as a **test case**, and `assertEquals()` checks expected vs actual result.

---

# 🧩 **2️⃣ Difference between Unit Test and Integration Test**

| Feature      | Unit Test              | Integration Test                         |
| ------------ | ---------------------- | ---------------------------------------- |
| Scope        | Tests one class/method | Tests how multiple modules work together |
| Dependencies | Mocked                 | Real (DB, Web, etc.)                     |
| Speed        | Very fast              | Slower                                   |
| Example      | `Calculator.add()`     | `PatientService` + `PatientRepository`   |

---

### 💡 Example:

**Unit test:** Test only `Service` layer by mocking repository.
**Integration test:** Start Spring context and test end-to-end with real DB.

---

# 🧱 **3️⃣ JUnit Lifecycle Annotations**

| Annotation    | Description                    |
| ------------- | ------------------------------ |
| `@BeforeEach` | Runs **before each test**      |
| `@AfterEach`  | Runs **after each test**       |
| `@BeforeAll`  | Runs **once before all tests** |
| `@AfterAll`   | Runs **once after all tests**  |
| `@Test`       | Marks method as test case      |

---

### 💻 Example:

```java
import org.junit.jupiter.api.*;

public class SampleTest {

    @BeforeAll
    static void initAll() {
        System.out.println("Run once before all tests");
    }

    @BeforeEach
    void init() {
        System.out.println("Run before each test");
    }

    @Test
    void testA() {
        System.out.println("Running test A");
    }

    @AfterEach
    void tearDown() {
        System.out.println("Run after each test");
    }

    @AfterAll
    static void tearDownAll() {
        System.out.println("Run once after all tests");
    }
}
```

✅ **Output Order:**

```
Run once before all tests
Run before each test
Running test A
Run after each test
Run once after all tests
```

---

# 🤖 **4️⃣ How to Mock Dependencies in a Spring Boot Test**

Use **Mockito** to simulate repository or service behavior.

---

### 💻 Example: Mocking Repository

```java
import org.junit.jupiter.api.Test;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.MockitoAnnotations;
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.*;
import java.util.*;

class Patient {
    Long id; String name;
    public Patient(Long id, String name) { this.id = id; this.name = name; }
}

interface PatientRepository {
    List<Patient> findAll();
}

class PatientService {
    private final PatientRepository repo;
    public PatientService(PatientRepository repo) { this.repo = repo; }
    public List<Patient> getAll() { return repo.findAll(); }
}

public class PatientServiceTest {
    @Mock
    private PatientRepository repo;

    @InjectMocks
    private PatientService service;

    public PatientServiceTest() {
        MockitoAnnotations.openMocks(this);
    }

    @Test
    void testGetAll() {
        List<Patient> mockPatients = Arrays.asList(new Patient(1L, "Mathu"));
        when(repo.findAll()).thenReturn(mockPatients);

        List<Patient> result = service.getAll();
        assertEquals(1, result.size());
        assertEquals("Mathu", result.get(0).name);
    }
}
```

✅ **Explanation:**

* `@Mock` → creates fake repository
* `@InjectMocks` → injects mock repo into service
* `when(...).thenReturn(...)` → defines mock behavior
* No real DB is used

---

# 🌐 **5️⃣ How to Test REST Endpoints using MockMvc**

**MockMvc** simulates HTTP requests to your REST controllers **without starting a real server**.

---

### 💻 Example:

**Controller:**

```java
@RestController
@RequestMapping("/api/patient")
class PatientController {
    @GetMapping("/{id}")
    public ResponseEntity<String> getPatient(@PathVariable Long id) {
        return ResponseEntity.ok("Patient ID: " + id);
    }
}
```

**Test:**

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.test.web.servlet.MockMvc;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.*;

@WebMvcTest(PatientController.class)
class PatientControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    void testGetPatient() throws Exception {
        mockMvc.perform(get("/api/patient/1"))
               .andExpect(status().isOk())
               .andExpect(content().string("Patient ID: 1"));
    }
}
```

✅ **Explanation:**

* `@WebMvcTest` → loads only the controller layer
* `MockMvc` → performs fake HTTP calls
* `andExpect()` → asserts HTTP status and response body

---

# 🧱 **6️⃣ What is Testcontainers?**

**Definition:**
Testcontainers is a **Java library** that runs **real Docker containers** (like MySQL, PostgreSQL, Kafka) for **integration testing**.

👉 It allows you to test your code **against real services** instead of mocks.

---

### 💡 Example:

**Use case:** Run MySQL container for integration tests.

```java
import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;
import org.testcontainers.containers.MySQLContainer;
import static org.junit.jupiter.api.Assertions.*;

@SpringBootTest
public class MySQLContainerTest {

    @Test
    void testMySQLContainer() {
        try (MySQLContainer<?> mysql = new MySQLContainer<>("mysql:8.0")) {
            mysql.start();

            System.out.println("JDBC URL: " + mysql.getJdbcUrl());
            assertTrue(mysql.isRunning());
        }
    }
}
```

✅ **Explanation:**

* Starts a real MySQL container in Docker.
* Automatically stops after the test.
* Can be integrated with Spring Boot using `@DynamicPropertySource`.

---

# 🧠 **Summary Table**

| Concept      | Tool/Annotation         | Description                          |
| ------------ | ----------------------- | ------------------------------------ |
| Unit Test    | JUnit                   | Test one method/class                |
| Mocking      | Mockito                 | Replace real dependencies with fakes |
| REST Testing | MockMvc                 | Simulate HTTP requests               |
| Lifecycle    | @BeforeEach, @AfterEach | Control test setup & teardown        |
| Integration  | Spring Boot Test        | Test full app with context           |
| Real DB Test | Testcontainers          | Run real DB in Docker                |

---

# 🚀 **Bonus: Common Interview Questions**

1. What is the difference between `@Mock` and `@MockBean`?

   * `@Mock`: Pure Mockito, no Spring context.
   * `@MockBean`: Used in Spring Boot test, replaces real bean in context.

2. What does `@SpringBootTest` do?

   * Starts full Spring Boot application context for integration tests.

3. How do you test service methods with dependencies?

   * Use `@ExtendWith(MockitoExtension.class)` with `@Mock` and `@InjectMocks`.

4. How to test repository layer?

   * Use `@DataJpaTest` → loads only JPA layer with in-memory DB (H2).

