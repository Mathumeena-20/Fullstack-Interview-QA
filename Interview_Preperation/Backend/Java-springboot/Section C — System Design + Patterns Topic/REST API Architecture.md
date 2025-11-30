Here is a **clean, interview-ready explanation** for all your REST API questions with examples.
This covers **core concepts + architecture + best practices + microservices**—exactly what interviewers expect.

---

# ✅ **1. What is REST and RESTful Architecture?**

### ✔ REST (Representational State Transfer)

REST is an architectural style for building APIs that use:

* **HTTP methods** (GET, POST, PUT, DELETE)
* **Resource-based URLs**
* **Stateless communication**
* **JSON/XML formats**

### ✔ RESTful API

An API is *RESTful* if it follows REST principles:

Example:

```
GET /users/10       → Get user  
POST /users         → Create user  
PUT /users/10       → Replace user  
PATCH /users/10     → Update partial user  
DELETE /users/10    → Delete user  
```

---

# ✅ **2. Difference Between REST and SOAP**

| Feature    | REST                | SOAP                          |
| ---------- | ------------------- | ----------------------------- |
| Style      | Architectural style | Protocol                      |
| Format     | JSON, XML           | Only XML                      |
| Transport  | HTTP                | HTTP, SMTP, TCP               |
| Complexity | Lightweight         | Heavy                         |
| Speed      | Faster              | Slower                        |
| Use Case   | Web/Mobile APIs     | Banking, Payments, Enterprise |
| Security   | OAuth, JWT          | Built-in WS-Security          |
| Stateless  | Yes                 | Stateful allowed              |

---

# ✅ **3. Explain Statelessness in REST**

Each request must contain **all information needed** to process it.
Server does NOT store client session.

Example:

Client sends:

```
GET /orders  
Authorization: Bearer <token>
```

Server does not remember:

* Previous requests
* Session ID

This improves: scalability, reliability, horizontal scaling.

---

# ✅ **4. What are REST Constraints?**

REST has **6 constraints**:

1. **Client-Server** → separation of UI & backend
2. **Stateless** → server stores no client session
3. **Cacheable** → HTTP caching
4. **Uniform Interface** → standard resource rules
5. **Layered System** → proxies, load balancers
6. **Code-On-Demand (optional)** → server sends executable code

---

# ✅ **5. What is Idempotency?**

A request is **idempotent** if calling it multiple times produces the **same result**.

| Method | Idempotent? | Meaning                               |
| ------ | ----------- | ------------------------------------- |
| GET    | Yes         | No change                             |
| PUT    | Yes         | Replace resource                      |
| DELETE | Yes         | Delete once only                      |
| POST   | ❌ No        | Creates new resource each time        |
| PATCH  | ❌ No        | May change different values each call |

Example:

```
DELETE /users/10
```

Calling this 10 times → user still ends up deleted once.

---

# ✅ **6. Difference Between PUT vs PATCH**

| Feature      | PUT                     | PATCH                 |
| ------------ | ----------------------- | --------------------- |
| Purpose      | Replace entire resource | Partial update        |
| Idempotent   | Yes                     | No                    |
| Request body | Complete object         | Only fields to update |

### Example:

✔ PUT (full replacement)

```
PUT /users/10
{
  "name": "John",
  "age": 30
}
```

✔ PATCH (partial update)

```
PATCH /users/10
{
  "age": 32
}
```

---

# ✅ **7. How do you design versioning in REST APIs?**

### Methods:

#### ✔ 1. Path Versioning (Most Common)

```
GET /v1/users  
GET /v2/users
```

#### ✔ 2. Header Versioning

```
GET /users  
API-Version: 1
```

#### ✔ 3. Query Params Versioning

```
GET /users?version=1
```

#### ✔ 4. Content Negotiation

```
Accept: application/json; version=2
```

---

# ✅ **8. How do you handle Pagination & Filtering?**

### ✔ URL Example:

```
GET /products?page=2&size=10&sort=price,asc&category=mobile&brand=samsung
```

### Response:

```json
{
  "data": [...],
  "page": 2,
  "size": 10,
  "totalPages": 20,
  "totalItems": 200
}
```

---

# ✅ **9. Best Practices for REST API Error Handling**

### Use Standard HTTP Status Codes

| Code | Meaning      |
| ---- | ------------ |
| 200  | Success      |
| 201  | Created      |
| 400  | Bad Request  |
| 401  | Unauthorized |
| 403  | Forbidden    |
| 404  | Not Found    |
| 409  | Conflict     |
| 500  | Server Error |

### Always send proper JSON error

```json
{
  "timestamp": "2024-01-01",
  "status": 400,
  "error": "Bad Request",
  "message": "Invalid user ID",
  "path": "/users/xyz"
}
```

---

# ✅ **10. How do you design Scalable REST APIs?**

### Key Practices:

1. **Stateless servers → easy horizontal scaling**
2. **Load balancers**
3. **Caching (ETag, Cache-Control)**
4. **Asynchronous operations (message queues)**
5. **Shard/partition data**
6. **Use CDN for static content**
7. **Limit payload size**
8. **Pagination on list endpoints**
9. **Database connection pooling**

---

# ✅ **11. What is HATEOAS?**

**HATEOAS = Hypermedia As The Engine Of Application State**

Server provides **links to next actions**.

Example response:

```json
{
  "id": 10,
  "name": "John",
  "links": [
    { "rel": "self", "href": "/users/10" },
    { "rel": "orders", "href": "/users/10/orders" }
  ]
}
```

Client discovers available actions dynamically.

---

# ✅ **12. How do you secure REST APIs?**

### Common Security Measures:

✔ **API Keys** (basic security)
✔ **OAuth 2.0** (industry standard)
✔ **JWT Tokens**
✔ **HTTPS only**
✔ **Rate limiting**
✔ **Input validation**
✔ **CORS protection**
✔ **CSRF protection (if cookies used)**
✔ **Encrypt sensitive data**

Example Authentication header:

```
Authorization: Bearer <jwt_token>
```

---

# ✅ **13. What is Rate Limiting?**

Rate limiting restricts **number of API calls allowed** from a client in a time window.

Example:

* Max 100 requests/minute
* Return **429 Too Many Requests** when exceeded

Used to prevent:

* Abuse
* DDOS
* Excess load

---

# ✅ **14. How do you handle Backward Compatibility?**

### Techniques:

1. **Versioning**
2. **Never break existing contracts**
3. **Mark old fields as deprecated**
4. **Make new fields optional**
5. **Add, don’t remove**

Example:
Old response:

```json
{ "name": "John" }
```

New compatible response:

```json
{ "name": "John", "age": 30 }  // age is optional
```

---

# ✅ **15. How do you design REST APIs for Microservices?**

### Key Principles:

✔ **Each microservice owns its domain**

* Product Service
* Order Service
* Payment Service

✔ **Communicate via**

* REST
* gRPC
* Message brokers (Kafka, RabbitMQ)

✔ **Use API Gateway**

* Single entry point
* Auth
* Rate limiting
* Routing
* Monitoring

✔ **Service-level versioning**

✔ **Circuit Breakers (Resilience4j)**

✔ **Distributed tracing** (Zipkin, Jaeger)

✔ **Centralized Logging** (ELK stack)

✔ **Use DTOs between services**

---

# ⭐ Final Combined Example of RESTful API (Complete)

### Request:

```
GET /v1/users?page=1&size=5
Authorization: Bearer <jwt_token>
```

### Response:

```json
{
  "users": [
    { "id": 1, "name": "John" },
    { "id": 2, "name": "Alex" }
  ],
  "page": 1,
  "size": 5,
  "links": [
    { "rel": "next", "href": "/v1/users?page=2&size=5" }
  ]
}
```

---

# If you want, I can also give:

✅ Diagram of REST architecture
✅ Spring Boot example REST API
✅ Pagination + filtering code
✅ Error handling using @ControllerAdvice
✅ JWT + OAuth2 example

Just tell me!
