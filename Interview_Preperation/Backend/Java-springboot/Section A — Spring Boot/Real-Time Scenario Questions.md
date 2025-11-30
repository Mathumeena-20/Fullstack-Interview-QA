
# 1 — Architecture & microservices communication (short summary)

* **Synchronous**: HTTP/REST (OpenFeign, Spring `RestTemplate`/`WebClient`) — simple, low-latency but couples services + requires higher availability.
* **Asynchronous**: Message brokers (Kafka, RabbitMQ) — loose coupling, resilience, easier to handle retries/ordering. Use for events, integration, long-running flows.
* **Patterns**:

  * **API gateway** (routing, authentication, rate-limiting).
  * **Circuit Breaker** (Resilience4j) to avoid cascading failures.
  * **Retry** with exponential backoff.
  * **Bulkhead** to isolate resource exhaustion.
  * **Sagas / Outbox** for distributed transactions (compensating actions).
* **When to use**: synchronous for request-response, async for events/long processes.

---

# 2 — Project dependencies (pom.xml excerpt)

```xml
<!-- include these in your pom.xml -->
<dependencies>
  <!-- Spring Boot Starter Web, JPA, Security -->
  <dependency>
    <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-web</artifactId>
  </dependency>
  <dependency>
    <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-data-jpa</artifactId>
  </dependency>
  <dependency>
    <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-security</artifactId>
  </dependency>

  <!-- H2 for quick testing -->
  <dependency>
    <groupId>com.h2database</groupId><artifactId>h2</artifactId><scope>runtime</scope>
  </dependency>

  <!-- OpenFeign -->
  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
  </dependency>

  <!-- Resilience4j for retries/circuit-breaker/fallback (annotations) -->
  <dependency>
    <groupId>io.github.resilience4j</groupId>
    <artifactId>resilience4j-spring-boot2</artifactId>
  </dependency>
  <dependency>
    <groupId>io.github.resilience4j</groupId>
    <artifactId>resilience4j-retry</artifactId>
  </dependency>

  <!-- Logging (SLF4J), MDC usually available via spring-boot-starter -->
  <dependency>
    <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-logging</artifactId>
  </dependency>

  <!-- Lombok (optional) -->
  <dependency>
    <groupId>org.projectlombok</groupId><artifactId>lombok</artifactId><optional>true</optional>
  </dependency>
</dependencies>
```

Also add Spring Cloud BOM and plugin configuration (Spring Boot + Spring Cloud compatibility).

---

# 3 — Employee CRUD: Entity, Repository, Service, Controller

### 3.1 `Employee` entity

```java
// package com.example.employee.entity
import jakarta.persistence.*;
import java.time.Instant;

@Entity
public class Employee {
    @Id @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String firstName;
    private String lastName;
    private String email;
    private String role;
    private Instant createdAt = Instant.now();

    // getters & setters (or use Lombok @Data)
}
```

### 3.2 Repository

```java
// package com.example.employee.repository
import org.springframework.data.jpa.repository.JpaRepository;

public interface EmployeeRepository extends JpaRepository<Employee, Long> {}
```

### 3.3 Service (business logic)

```java
// package com.example.employee.service
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;
import java.util.List;

@Service
public class EmployeeService {
    private final EmployeeRepository repo;
    public EmployeeService(EmployeeRepository repo) { this.repo = repo; }

    public List<Employee> findAll() { return repo.findAll(); }
    public Employee findById(Long id) {
        return repo.findById(id).orElseThrow(() -> new ResourceNotFoundException("Employee", id));
    }

    @Transactional
    public Employee create(Employee e) { return repo.save(e); }

    @Transactional
    public Employee update(Long id, Employee updated) {
        Employee e = findById(id);
        e.setFirstName(updated.getFirstName());
        e.setLastName(updated.getLastName());
        e.setEmail(updated.getEmail());
        e.setRole(updated.getRole());
        return repo.save(e);
    }

    @Transactional
    public void delete(Long id) {
        Employee e = findById(id);
        repo.delete(e);
    }
}
```

(Define `ResourceNotFoundException` class; shown below.)

### 3.4 REST Controller

```java
// package com.example.employee.controller
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import java.net.URI;
import java.util.List;

@RestController
@RequestMapping("/api/employees")
public class EmployeeController {
    private final EmployeeService service;
    public EmployeeController(EmployeeService service) { this.service = service; }

    @GetMapping
    public List<Employee> list() { return service.findAll(); }

    @GetMapping("/{id}")
    public Employee get(@PathVariable Long id) { return service.findById(id); }

    @PostMapping
    public ResponseEntity<Employee> create(@RequestBody Employee employee) {
        Employee saved = service.create(employee);
        return ResponseEntity.created(URI.create("/api/employees/" + saved.getId())).body(saved);
    }

    @PutMapping("/{id}")
    public Employee update(@PathVariable Long id, @RequestBody Employee employee) {
        return service.update(id, employee);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> delete(@PathVariable Long id) {
        service.delete(id);
        return ResponseEntity.noContent().build();
    }
}
```

---

# 4 — Global exception handler using `@ControllerAdvice`

```java
// package com.example.employee.exception
import org.springframework.http.*;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.context.request.WebRequest;
import java.time.Instant;
import java.util.Map;

@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<Object> handleNotFound(ResourceNotFoundException ex, WebRequest req) {
        var body = Map.of(
            "timestamp", Instant.now(),
            "status", HttpStatus.NOT_FOUND.value(),
            "error", "Not Found",
            "message", ex.getMessage(),
            "path", req.getDescription(false)
        );
        return new ResponseEntity<>(body, HttpStatus.NOT_FOUND);
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<Object> handleAll(Exception ex, WebRequest req) {
        var body = Map.of(
            "timestamp", Instant.now(),
            "status", HttpStatus.INTERNAL_SERVER_ERROR.value(),
            "error", "Internal Server Error",
            "message", ex.getMessage(),
            "path", req.getDescription(false)
        );
        return new ResponseEntity<>(body, HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

Example `ResourceNotFoundException`:

```java
public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String resource, Object id) {
        super(resource + " with id " + id + " not found");
    }
}
```

---

# 5 — Scheduled task (runs every hour)

```java
// Enable scheduling on main application
@SpringBootApplication
@EnableScheduling
public class EmployeeApplication { ... }

// Scheduled task bean
@Component
public class HourlyTasks {
    private final EmployeeService service;
    public HourlyTasks(EmployeeService service) { this.service = service; }

    // Run at the top of every hour
    @Scheduled(cron = "0 0 * * * *")
    public void hourlyJob() {
        // e.g., cleanup, metrics, summary report
        var total = service.findAll().size();
        // use logger (SLF4J)
        logger.info("Hourly job: total employees = {}", total);
    }
}
```

---

# 6 — Custom `HandlerInterceptor` to log incoming requests & set correlation id

We will use MDC (Mapped Diagnostic Context) to include a correlation id in logs.

```java
// package com.example.employee.logging
import jakarta.servlet.http.*;
import org.slf4j.MDC;
import org.springframework.stereotype.Component;
import org.springframework.web.servlet.HandlerInterceptor;
import java.util.UUID;

@Component
public class CorrelationIdInterceptor implements HandlerInterceptor {
    public static final String CORR_HEADER = "X-Correlation-ID";
    public static final String MDC_KEY = "correlationId";

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) {
        String id = request.getHeader(CORR_HEADER);
        if (id == null || id.isEmpty()) id = UUID.randomUUID().toString();
        MDC.put(MDC_KEY, id);
        response.setHeader(CORR_HEADER, id);
        // log basic info
        logger.info("Incoming request: {} {}", request.getMethod(), request.getRequestURI());
        return true;
    }

    @Override
    public void afterCompletion(HttpServletRequest req, HttpServletResponse res, Object handler, Exception ex) {
        MDC.remove(MDC_KEY);
    }
}
```

Register interceptor:

```java
@Configuration
public class WebConfig implements WebMvcConfigurer {
    private final CorrelationIdInterceptor interceptor;
    public WebConfig(CorrelationIdInterceptor interceptor) { this.interceptor = interceptor; }

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(interceptor).addPathPatterns("/**");
    }
}
```

In logging config (logback) include `%X{correlationId}` in pattern to print it.

---

# 7 — Exception logging across services (best practices)

* Add **Correlation ID** to each request and propagate in all outgoing calls (headers e.g., `X-Correlation-ID`).
* Use MDC so every log line contains the correlation id.
* Centralized logging: ship logs to ELK/EFK (Elasticsearch + Filebeat/Fluentd + Kibana) or to logging SaaS (Sentry, Datadog).
* Structured logging (JSON) makes searching easier.
* Use distributed tracing (Spring Cloud Sleuth / OpenTelemetry + Zipkin / Jaeger) for request traces.
* On exceptions, log stacktrace + context (user id, request body limited to safe fields), then send structured error to monitoring/alerting system.

---

# 8 — Secure REST APIs (JWT sketch)

Use Spring Security with JWT filter:

1. Authenticate users at `/auth/login` (return JWT).
2. For protected endpoints, validate JWT in a filter.

Simplified filter:

```java
public class JwtAuthenticationFilter extends OncePerRequestFilter {
    private final JwtService jwtService; // verify tokens
    @Override
    protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain chain) {
        String authHeader = request.getHeader("Authorization");
        if (authHeader != null && authHeader.startsWith("Bearer ")) {
            String token = authHeader.substring(7);
            if (jwtService.validate(token)) {
                Authentication auth = jwtService.getAuthentication(token);
                SecurityContextHolder.getContext().setAuthentication(auth);
            }
        }
        chain.doFilter(request, response);
    }
}
```

Spring Security config:

```java
@EnableWebSecurity
public class SecurityConfig {
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http, JwtAuthenticationFilter jwtFilter) throws Exception {
        http.csrf().disable()
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/auth/**", "/actuator/**").permitAll()
                .anyRequest().authenticated()
            )
            .addFilterBefore(jwtFilter, UsernamePasswordAuthenticationFilter.class);
        return http.build();
    }
}
```

**Notes**: store JWT signing secret securely (Vault), rotate keys, apply short expiry + refresh tokens, use HTTPS.

---

# 9 — OpenFeign client with retry + fallback + Resilience4j

### 9.1 Enable Feign

```java
@SpringBootApplication
@EnableFeignClients
public class EmployeeApplication { ... }
```

### 9.2 Feign client interface

```java
@FeignClient(name = "payroll-service", url = "${payroll.service.url}", fallback = PayrollClientFallback.class)
public interface PayrollClient {
    @GetMapping("/api/payroll/employee/{id}/salary")
    SalaryDto getSalary(@PathVariable("id") Long employeeId);
}
```

### 9.3 Fallback implementation (simple)

```java
@Component
public class PayrollClientFallback implements PayrollClient {
    @Override
    public SalaryDto getSalary(Long employeeId) {
        // fallback: return default or null and record a metric
        return new SalaryDto(employeeId, 0.0, "fallback");
    }
}
```

### 9.4 Resilience4j retry & circuit-breaker on service method (recommended)

Add config (application.yml):

```yaml
resilience4j:
  retry:
    instances:
      payrollRetry:
        max-attempts: 3
        wait-duration: 500ms
  circuitbreaker:
    instances:
      payrollCB:
        registerHealthIndicator: true
        slidingWindowSize: 10
        failureRateThreshold: 50
```

Use annotations on service method that calls Feign:

```java
@Service
public class PayrollService {
    private final PayrollClient client;

    @Autowired
    public PayrollService(PayrollClient client) { this.client = client; }

    @Retry(name = "payrollRetry", fallbackMethod = "salaryFallback")
    @CircuitBreaker(name = "payrollCB", fallbackMethod = "salaryFallback")
    public SalaryDto getSalary(Long id) {
        return client.getSalary(id);
    }

    public SalaryDto salaryFallback(Long id, Throwable ex) {
        // record metric, return safe default
        return new SalaryDto(id, 0.0, "fallback");
    }
}
```

### 9.5 Feign retryer alternative

Feign has its own `Retryer` — you can configure a custom `Retryer` bean, but using Resilience4j is preferred for visibility & combined patterns.

---

# 10 — Handling retries and fallbacks (conceptual)

* **Retries**: only for idempotent operations or safe GETs. Use exponential backoff and jitter; cap total attempts.
* **Fallbacks**: return cached/default data or user-friendly error; avoid masking root problems.
* **Circuit breaker**: after repeated failures open the circuit (fail fast) to avoid overwhelming downstream.
* **Retry policy location**: implement at client side (Resilience4j), and also ensure server side is resilient (rate limit, queue).

---

# 11 — Managing distributed transactions

* **2PC (XA)**: strong consistency but complex and blocks resources; rarely used in microservices.
* **Saga pattern** (recommended): composition of local transactions + compensating actions.

  * **Choreography**: services publish events; other services react.
  * **Orchestration**: a coordinator (Saga orchestrator) invokes steps and calls compensating actions on failure.
* **Outbox pattern**: write DB changes + events in same local transaction; a separate process publishes events to broker to ensure eventual consistency.
* **Practical approach**: use Sagas for business-level distributed transactions (bookings, orders), use idempotency keys and retries, maintain compensation logic.

---

# 12 — Example: Service A calls Service B and needs distributed transaction (Saga idea)

1. Service A creates local record `Order` and publishes `OrderCreated`.
2. Payment service listens, takes payment, publishes `PaymentCompleted` or `PaymentFailed`.
3. If `PaymentFailed`, Order service triggers compensating action `CancelOrder`.

Orchestrator pattern: Orchestrator calls sub-services sequentially and calls compensations on failure.

---

# 13 — Exception & error propagation strategy

* Use meaningful HTTP status codes (4xx for client, 5xx for server).
* Include a structured error body `{code, message, details, correlationId, timestamp}`.
* For service-to-service calls, pass correlation id and short structured errors so orchestrators can act.
* Log errors with MDC correlation id and send error metrics to monitoring.

---

# 14 — Full example: Employee API calling external Payroll via Feign (controller-level example)

Controller that exposes an endpoint to get employee and salary:

```java
@RestController
@RequestMapping("/api/employees")
public class EmployeeController {
    private final EmployeeService service;
    private final PayrollService payrollService; // uses Feign + Resilience4j

    public EmployeeController(EmployeeService service, PayrollService payrollService) {
        this.service = service; this.payrollService = payrollService;
    }

    @GetMapping("/{id}/with-salary")
    public ResponseEntity<EmployeeWithSalaryDto> getWithSalary(@PathVariable Long id) {
        Employee e = service.findById(id);
        SalaryDto salary = payrollService.getSalary(id); // resilient call
        var dto = new EmployeeWithSalaryDto(e.getId(), e.getFirstName(), e.getLastName(),
                                            e.getEmail(), salary.getAmount());
        return ResponseEntity.ok(dto);
    }
}
```

---

# 15 — Notes on testing & deployment

* Unit test controllers & services (MockMvc, Mockito).
* Integration tests with `@SpringBootTest` and in-memory DB.
* Contract tests for Feign clients (Pact or Spring Cloud Contract).
* Containerize service (Docker) and use k8s or ECS for deployment.
* Use liveness/readiness probes, rate limiting, resource limits.

---

# 16 — Quick `application.properties` / `application.yml` essentials

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.jpa.hibernate.ddl-auto=update

# Feign and Resilience
payroll.service.url=http://localhost:8081

# Logging pattern (logback config recommended to include %X{correlationId})
```

---

# 17 — Summary: recommended tech choices

* Use **OpenFeign** for simple sync calls + **Resilience4j** for retry/circuit-breaker/fallback.
* Use **Sagas** + **Outbox pattern** for distributed transactions.
* Use **JWT + HTTPS** for REST security; rotate keys & apply minimal privileges.
* Use **Correlation IDs + MDC + centralized logging/tracing** for observability.
* Use **asynchronous messaging** for decoupling and resiliency where possible.

---

