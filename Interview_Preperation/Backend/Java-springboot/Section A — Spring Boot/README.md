## 1. REST Controllers

1. Difference between `@Controller` and `@RestController`.
2. What does `@RequestBody` do?
3. Difference between `@GetMapping`, `@PostMapping`, `@PutMapping`, and `@DeleteMapping`.
4. How do you handle path variables and request parameters?
5. Difference between `@PathVariable` and `@RequestParam`.
6. How does Spring Boot convert JSON to Java objects?
7. How do you return different HTTP status codes?
8. What is `ResponseEntity` and why is it used?
9. Difference between REST and SOAP.
10. How do you version REST APIs?

---

## 2. Dependency Injection

1. What is Dependency Injection?
2. Difference between field injection, constructor injection and setter injection.
3. Why is constructor injection recommended?
4. What is `@Autowired` and how does it work?
5. Difference between `@Component`, `@Service`, `@Repository`, `@Bean`.
6. What are Spring beans?
7. Bean lifecycle in Spring.
8. What is `@Lazy`?
9. What is circular dependency and how to resolve it?
10. How does Spring manage singleton beans?

---

## 3. Spring Data JPA

1. What is Spring Data JPA?
2. Difference between JPA and Hibernate.
3. What is an Entity?
4. What is a Repository?
5. Difference between `CrudRepository` and `JpaRepository`.
6. What is `@Transactional`?
7. What is LAZY and EAGER loading?
8. What is JPQL?
9. What is paging and sorting?
10. What are projections?
11. What is N+1 problem?
12. How do you solve N+1 issues?
13. Difference between native query and JPQL.
14. What is dirty checking?
15. How do you define composite primary key?

---

## 4. Validation

1. What is Bean Validation (JSR 380)?
2. Difference between `@Valid` and `@Validated`.
3. Common validation annotations (`@NotNull`, `@Email`, `@Size`).
4. How do you create custom validators?
5. What is validation groups?
6. Where does the validation happen in Spring?
7. How to validate path variables and request parameters?
8. How do you return custom validation messages?
9. Difference between server-side and client-side validation.
10. What happens if validation fails?

---

## 5. Filters & Interceptors

### Filters

1. What is a Servlet Filter?
2. How do you create a custom filter in Spring Boot?
3. Difference between Filter and Interceptor.
4. Use case of filters in real projects.
5. When does a filter get executed?

### Interceptors

6. What is a Spring Interceptor?
7. How do you implement `HandlerInterceptor`?
8. Difference between `preHandle()`, `postHandle()`, `afterCompletion()`.
9. Real-time scenario where you used interceptor.
10. How do you register multiple interceptors?

---

## 6. Global Exception Handling

1. What is `@ControllerAdvice`?
2. Difference between `@ExceptionHandler` and global handler.
3. How do you return custom error response?
4. How do you handle validation errors globally?
5. Difference between checked and unchecked exception handling in Spring.
6. How do you return HTTP status codes using exceptions?
7. How do you log exceptions globally?
8. Can you have multiple ControllerAdvice?
9. Best practices for exception handling in REST APIs.
10. Example of production-level exception handling.

---

## 7. Scheduling

1. What is Spring Scheduler?
2. What is `@EnableScheduling`?
3. What is `@Scheduled`?
4. Difference between fixedRate and fixedDelay.
5. What is cron expression?
6. Can we run scheduled jobs in cluster environment?
7. How do you avoid overlapping jobs?
8. How do you stop scheduled jobs?
9. What happens if a scheduled method throws exception?
10. Real-world example of scheduling tasks.

---

## 8. OpenFeign / RestTemplate

### RestTemplate

1. What is RestTemplate?
2. Difference between RestTemplate and WebClient.
3. How do you configure timeout in RestTemplate?
4. How to handle errors in RestTemplate?

### OpenFeign

5. What is OpenFeign?
6. How does Feign work internally?
7. How do you enable Feign client in Spring Boot?
8. How do you add headers to Feign request?
9. How do you configure Feign timeout?
10. Feign vs RestTemplate vs WebClient.

---

## 🔥 Real-Time Scenario Questions

1. How do you design microservices communication?
2. How do you handle retries and fallbacks in Feign?
3. How do you secure REST APIs?
4. How do you manage distributed transactions?
5. How do you handle exception logging across services?
6. Build a CRUD API for Employee using Spring Boot + JPA.
7. Create a global exception handler using @ControllerAdvice.
8. Implement a scheduled task that runs every hour.
9. Write a custom interceptor to log incoming requests.
10. Build an API that calls another API using OpenFeign.
---

Just tell me 👍
