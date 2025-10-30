# 🧩 **1️⃣ Basics of Spring Boot**

---

### 💡 What is Spring Boot and why is it used?

**Spring Boot** is a framework built on top of **Spring** that simplifies the development of **standalone, production-grade Spring applications** with minimal configuration.

✅ **Why use it?**

* Auto-configuration (no XML)
* Embedded servers (Tomcat, Jetty)
* Starter dependencies
* Easy production-ready setup (Actuator, metrics)

**Example (Main Class):**

```java
@SpringBootApplication
public class HealthApp {
    public static void main(String[] args) {
        SpringApplication.run(HealthApp.class, args);
    }
}
```

---

### ⚙️ Difference between Spring and Spring Boot

| Feature      | Spring                | Spring Boot         |
| ------------ | --------------------- | ------------------- |
| Setup        | Manual XML config     | Auto-configuration  |
| Server       | Needs external server | Embedded Tomcat     |
| Dependencies | Add manually          | Uses Starters       |
| Boilerplate  | High                  | Low                 |
| Actuator     | Not included          | Built-in monitoring |

---

### ⚙️ What is Auto-Configuration?

Spring Boot automatically configures your app based on **classpath dependencies**.

**Example:**
If `spring-boot-starter-data-jpa` is present, it configures:

* `DataSource`
* `EntityManager`
* `JpaRepository`

**Annotation:**
`@EnableAutoConfiguration` (included in `@SpringBootApplication`)

---

### 🌟 What is a Spring Boot Starter?

Starters are **predefined dependency packages** that simplify adding libraries.

**Example:**

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

✅ Includes Spring MVC + Jackson + Tomcat automatically.

---

### 🛠 What is application.properties / application.yml?

Used to define **application-level configuration**.

**Example (application.properties):**

```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/healthdb
spring.datasource.username=root
spring.datasource.password=1234
```

**YAML Format:**

```yaml
server:
  port: 8081
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/healthdb
```

---

### 🧩 What is @SpringBootApplication?

Combines:

* `@Configuration` → defines beans
* `@EnableAutoConfiguration`
* `@ComponentScan`

✅ **Tells Spring Boot:** “This is the starting point of the app.”

---

# 💉 **2️⃣ Dependency Injection & Beans**

---

### 💡 What is Dependency Injection (DI)?

A design pattern where Spring **injects dependencies automatically** instead of creating them manually.

**Example:**

```java
@Component
class Engine {
    void start() { System.out.println("Engine started"); }
}

@Component
class Car {
    private final Engine engine;
    @Autowired
    public Car(Engine engine) { this.engine = engine; }
    void drive() { engine.start(); }
}
```

---

### ⚙️ @Autowired vs @Inject

| Annotation   | Package | Description                        |
| ------------ | ------- | ---------------------------------- |
| `@Autowired` | Spring  | Preferred in Spring apps           |
| `@Inject`    | Javax   | Standard Java annotation (JSR-330) |

---

### 🧱 @Component vs @Service vs @Repository

| Annotation    | Layer          | Purpose                 |
| ------------- | -------------- | ----------------------- |
| `@Component`  | Generic        | Any Spring bean         |
| `@Service`    | Business logic | Indicates service class |
| `@Repository` | Data layer     | Wraps JPA exceptions    |

---

### 🏗 What is @Bean annotation?

Used in **@Configuration classes** to manually define a Spring bean.

**Example:**

```java
@Configuration
public class AppConfig {
    @Bean
    public Engine engine() {
        return new Engine();
    }
}
```

---

### ⚙️ Bean Scopes

| Scope       | Description                                   |
| ----------- | --------------------------------------------- |
| `singleton` | One instance per Spring container *(default)* |
| `prototype` | New instance each time                        |
| `request`   | One per HTTP request (Web apps)               |
| `session`   | One per HTTP session                          |

**Example:**

```java
@Component
@Scope("prototype")
class Engine {}
```

---

### 🔄 Bean Lifecycle (Init & Destroy)

**Example:**

```java
@Component
public class Engine {
    @PostConstruct
    public void init() {
        System.out.println("Engine initialized");
    }
    @PreDestroy
    public void destroy() {
        System.out.println("Engine destroyed");
    }
}
```

---

# 🌐 **3️⃣ REST API Development**

---

### 💡 What is @RestController?

Combines:

* `@Controller` → MVC Controller
* `@ResponseBody` → Converts response to JSON

```java
@RestController
@RequestMapping("/api")
public class HealthController {
    @GetMapping("/pulse")
    public String getPulse() {
        return "Pulse rate: 75 bpm";
    }
}
```

---

### ⚙️ @Controller vs @RestController

| Annotation        | Returns     | Used for  |
| ----------------- | ----------- | --------- |
| `@Controller`     | HTML (View) | Web MVC   |
| `@RestController` | JSON/XML    | REST APIs |

---

### 🛠 @GetMapping, @PostMapping, etc.

```java
@RestController
@RequestMapping("/patients")
public class PatientController {

    @GetMapping("/{id}")
    public Patient getPatient(@PathVariable Long id) { ... }

    @PostMapping
    public Patient addPatient(@RequestBody Patient patient) { ... }
}
```

---

### 🔗 Request Params & Path Variables

```java
@GetMapping("/hello")
public String hello(@RequestParam String name) {
    return "Hello " + name;
}

@GetMapping("/user/{id}")
public String user(@PathVariable int id) {
    return "User ID: " + id;
}
```

---

### 📦 ResponseEntity

Used to customize **HTTP status + body + headers**.

```java
@GetMapping("/patient/{id}")
public ResponseEntity<String> getPatient(@PathVariable int id) {
    return ResponseEntity.ok("Patient ID " + id);
}
```

---

### 🧾 JSON Response

Spring Boot automatically uses **Jackson** to convert Java objects → JSON.

```java
@GetMapping("/patient")
public Patient getPatient() {
    return new Patient(1, "Mathu", 25);
}
```

✅ Output:

```json
{"id":1,"name":"Mathu","age":25}
```

---

### 🚨 Exception Handling

**Global Handler:**

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handle(Exception ex) {
        return ResponseEntity.status(HttpStatus.BAD_REQUEST)
                             .body("Error: " + ex.getMessage());
    }
}
```

---

# 💾 **4️⃣ Spring Data JPA / Database Layer**

---

### 💡 What is Spring Data JPA?

Simplifies database access by auto-implementing JPA repositories.

---

### ⚙️ Database Configuration (application.properties)

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/healthdb
spring.datasource.username=root
spring.datasource.password=1234
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

### 🧩 Entity, Repository, Service Layers

```java
@Entity
public class Patient {
    @Id @GeneratedValue
    private Long id;
    private String name;
}

@Repository
public interface PatientRepository extends JpaRepository<Patient, Long> {}

@Service
public class PatientService {
    @Autowired
    private PatientRepository repo;
    public List<Patient> getAll() { return repo.findAll(); }
}
```

---

### 📋 CrudRepository vs JpaRepository vs PagingAndSortingRepository

| Interface                    | Features                   |
| ---------------------------- | -------------------------- |
| `CrudRepository`             | Basic CRUD                 |
| `PagingAndSortingRepository` | Pagination & sorting       |
| `JpaRepository`              | All + batch + flush + JPQL |

---

### 🧠 Custom Queries

```java
@Query("SELECT p FROM Patient p WHERE p.name = :name")
List<Patient> findByName(@Param("name") String name);
```

---

### 💤 Lazy vs Eager Loading

* **Eager:** Loads related entities immediately.
* **Lazy:** Loads related entities only when accessed.

```java
@OneToMany(fetch = FetchType.LAZY)
private List<Report> reports;
```

---

### 🧱 EntityManager

Used for **custom JPA operations**:

```java
@PersistenceContext
EntityManager em;

public List<Patient> getAllPatients() {
    return em.createQuery("FROM Patient").getResultList();
}
```

---

### 🔄 @Transactional

Ensures all DB operations run in a single **atomic transaction**.

```java
@Transactional
public void saveAll(List<Patient> patients) {
    repo.saveAll(patients);
}
```

---

# 🔐 **5️⃣ Security & Configuration**

---

### 🔒 What is Spring Security?

A powerful authentication & authorization framework.

---

### ⚙️ Basic Authentication Setup

**application.properties:**

```properties
spring.security.user.name=admin
spring.security.user.password=admin123
```

Now `/api/**` endpoints require login.

---

### 🪪 JWT (JSON Web Token)

Used to secure REST APIs with stateless authentication.

**Flow:**

1. Client logs in → JWT token returned
2. Client sends token in headers
3. Server verifies token on every request

---

### ⚙️ Roles and Permissions

```java
@PreAuthorize("hasRole('ADMIN')")
@GetMapping("/admin")
public String admin() { return "Welcome Admin"; }
```

---

### 🔐 Storing Secrets Safely

Use:

* Environment variables
* `.env` files
* Spring Cloud Vault or AWS Secrets Manager

---

# 🏗 **6️⃣ Architecture & Advanced Concepts**

---

### 🔁 Spring Boot Flow

```
Controller → Service → Repository → Database
```

Each layer separates business logic for cleaner architecture.

---

### 🚦 DispatcherServlet

Front controller that routes all HTTP requests to the right controller.

---

### ⚙️ Auto-Configuration Detection

Spring scans dependencies on the **classpath** and applies configurations automatically.

---

### 📊 Actuator

Used for monitoring health, metrics, and info.

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Endpoints like `/actuator/health` or `/actuator/metrics`.

---

### 🌍 Profiles

Define environment-specific settings:

```properties
spring.profiles.active=dev
```

---

### 🔄 Handle CORS

```java
@CrossOrigin(origins = "http://localhost:3000")
@GetMapping("/data")
public String getData() { return "Allowed"; }
```

---

### ⏰ Scheduled Tasks

```java
@Component
public class Scheduler {
    @Scheduled(fixedRate = 5000)
    public void printTime() {
        System.out.println("Running every 5 seconds");
    }
}
```

---

### 🌐 External API Calls

```java
@RestController
public class ApiClient {
    @Autowired
    private RestTemplate restTemplate;

    @GetMapping("/weather")
    public String getWeather() {
        return restTemplate.getForObject("https://api.weather.com/data", String.class);
    }
}

Would you like me to continue with **13️⃣ Microservices (Spring Cloud, Eureka, Feign, API Gateway, Circuit Breaker)** next?
It’s the **natural next step** after this — often asked in 2–4 year interviews.
