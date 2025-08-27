## 1️⃣ What is REST? Difference between REST and SOAP?

* **REST (Representational State Transfer)**

  * Architectural style.
  * Uses HTTP (GET, POST, PUT, DELETE, etc.).
  * Lightweight, stateless, JSON/XML.
  * Resource-based (`/users/1/orders`).

* **SOAP (Simple Object Access Protocol)**

  * Protocol with strict rules (XML-based).
  * Heavier, needs WSDL.
  * Built-in error handling and security.

👉 **Interview Tip**:
*"REST is lightweight and widely used in modern apps, while SOAP is heavier and used in legacy/banking apps requiring strict contracts."*

---

## 2️⃣ HTTP Methods

| Method     | Purpose                        |
| ---------- | ------------------------------ |
| **GET**    | Fetch resource (read-only)     |
| **POST**   | Create new resource            |
| **PUT**    | Update/replace entire resource |
| **PATCH**  | Update part of resource        |
| **DELETE** | Remove resource                |

🔹 Example in Spring Boot:

```java
@RestController
@RequestMapping("/users")
public class UserController {

    @GetMapping("/{id}") // GET /users/1
    public User getUser(@PathVariable Long id) { ... }

    @PostMapping        // POST /users
    public User createUser(@RequestBody User user) { ... }

    @PutMapping("/{id}") // PUT /users/1
    public User updateUser(@PathVariable Long id, @RequestBody User user) { ... }

    @PatchMapping("/{id}") // PATCH /users/1
    public User updatePartialUser(@PathVariable Long id, @RequestBody Map<String,Object> updates) { ... }

    @DeleteMapping("/{id}") // DELETE /users/1
    public void deleteUser(@PathVariable Long id) { ... }
}
```

---

## 3️⃣ HTTP Status Codes

* **200 OK** → Request success
* **201 Created** → New resource created (after POST)
* **400 Bad Request** → Invalid input/request format
* **401 Unauthorized** → No/invalid authentication
* **404 Not Found** → Resource doesn’t exist
* **500 Internal Server Error** → Server crashed or unhandled exception

🔹 Example:

```java
@PostMapping
public ResponseEntity<User> createUser(@RequestBody User user) {
    User saved = service.save(user);
    return ResponseEntity.status(HttpStatus.CREATED).body(saved); // returns 201
}
```

---

## 4️⃣ Difference between PUT and PATCH

* **PUT**

  * Replaces the **entire resource**.
  * If fields are missing, they may be set to `null`.

* **PATCH**

  * Partially updates only given fields.
  * More efficient for small updates.

🔹 Example:

```json
PUT /users/1
{
  "name": "John",
  "email": "john@example.com"
}
```

(replaces the full user object)

```json
PATCH /users/1
{
  "email": "john.new@example.com"
}
```

(only updates email field)

👉 **Tip**: Say you’ll prefer PATCH for **partial updates** to avoid overwriting.

---

## 5️⃣ Securing REST APIs (JWT, OAuth2)

* **JWT (JSON Web Token)**

  * Client logs in → Server generates JWT token → Client includes it in `Authorization: Bearer <token>` header for subsequent requests.
  * Stateless (no session storage needed).

* **OAuth2**

  * Used for third-party logins (Google, GitHub, etc.).
  * Client → Authorization Server → Token → API Access.

🔹 JWT Example in Spring Boot:

```java
// Authentication filter (simplified)
@Override
protected void doFilterInternal(HttpServletRequest request,
        HttpServletResponse response, FilterChain chain) throws IOException, ServletException {
    String header = request.getHeader("Authorization");
    if (header != null && header.startsWith("Bearer ")) {
        String token = header.substring(7);
        if (jwtUtil.validateToken(token)) {
            UsernamePasswordAuthenticationToken auth =
                new UsernamePasswordAuthenticationToken(user, null, roles);
            SecurityContextHolder.getContext().setAuthentication(auth);
        }
    }
    chain.doFilter(request, response);
}
```

---

✅ **Quick Recap Table**

| Concept      | REST                                  | Example                         |
| ------------ | ------------------------------------- | ------------------------------- |
| REST vs SOAP | REST = lightweight, JSON, stateless   | `/users/1`                      |
| HTTP Methods | GET, POST, PUT, PATCH, DELETE         | CRUD APIs                       |
| Status Codes | 200, 201, 400, 401, 404, 500          | `ResponseEntity`                |
| PUT vs PATCH | PUT = replace, PATCH = partial update | Update user                     |
| Security     | JWT (stateless), OAuth2 (third-party) | `Authorization: Bearer <token>` |
