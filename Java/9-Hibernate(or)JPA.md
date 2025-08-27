## 1️⃣ What is Hibernate? Difference between Hibernate and JPA?

* **Hibernate**

  * It’s an **ORM (Object Relational Mapping)** framework.
  * Maps Java objects → Database tables.
  * Provides features like caching, lazy loading, HQL, etc.

* **JPA (Java Persistence API)**

  * It’s a **specification** (interface) that defines how ORM should work.
  * Hibernate is one of the implementations of JPA (others: EclipseLink, OpenJPA).

👉 **Interview Tip**:
*"JPA is a standard/specification, Hibernate is an implementation. We code against JPA, Hibernate executes it."*

---

## 2️⃣ Difference between save() and persist()

* **save()** → Hibernate-specific, returns generated identifier (Serializable).
* **persist()** → JPA method, returns `void`.

🔹 Example:

```java
User u = new User();
u.setName("John");

// Hibernate specific
Serializable id = session.save(u); // returns id

// JPA standard
entityManager.persist(u); // returns void
```

👉 **Tip**: Use **persist()** in JPA projects (standard, portable).

---

## 3️⃣ Lazy vs Eager Fetching

* **Lazy Fetching (default)**

  * Associated entities are **loaded only when accessed**.
  * Improves performance.

* **Eager Fetching**

  * Associated entities are **loaded immediately with parent**.
  * Can cause unnecessary joins (N+1 problem).

🔹 Example:

```java
@Entity
class User {
    @OneToMany(mappedBy="user", fetch = FetchType.LAZY)  // Lazy
    private List<Order> orders;
}

@Entity
class Product {
    @OneToOne(fetch = FetchType.EAGER) // Eager
    private Category category;
}
```

👉 **Tip**: Prefer **Lazy**, control loading with `JOIN FETCH` in queries.

---

## 4️⃣ @Entity, @Id, @GeneratedValue

* **@Entity** → Marks class as a JPA entity (maps to table).
* **@Id** → Marks primary key field.
* **@GeneratedValue** → Auto-generate primary key (strategy: AUTO, IDENTITY, SEQUENCE, TABLE).

🔹 Example:

```java
@Entity
class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```

👉 **Tip**: Always use `@Entity` + `@Id` → mandatory.

---

## 5️⃣ get() vs load()

* **get()** → Immediately hits DB, returns `null` if not found.
* **load()** → Returns **proxy** (lazy), throws `ObjectNotFoundException` if entity not found.

🔹 Example:

```java
User u1 = session.get(User.class, 1L);   // returns null if not exists
User u2 = session.load(User.class, 1L);  // proxy, exception if not exists
```

👉 **Tip**: Use `get()` when you’re unsure if entity exists.

---

## 6️⃣ First-level vs Second-level Cache

* **First-level cache**

  * Enabled by default (Session-level).
  * Cached objects exist till session is open.

* **Second-level cache**

  * Optional, needs configuration (EhCache, Hazelcast).
  * Shared across sessions.

🔹 Example:

```java
Session session = sessionFactory.openSession();

// First call → DB
User u1 = session.get(User.class, 1L);

// Second call → cache (same session)
User u2 = session.get(User.class, 1L); 
```

👉 **Tip**: Always mention that Hibernate has **Query Cache** too (for HQL/JPQL).

---

## 7️⃣ Native Query vs JPQL

* **JPQL (Java Persistence Query Language)**

  * Works with **entities** (Java objects).
  * Database-independent.

* **Native Query**

  * Works with **actual SQL** (tables/columns).
  * Database-dependent.

🔹 Example:

```java
// JPQL
List<User> users = em.createQuery("SELECT u FROM User u", User.class).getResultList();

// Native
List<User> users = em.createNativeQuery("SELECT * FROM users", User.class).getResultList();
```

👉 **Tip**: Prefer **JPQL** unless you need DB-specific features.

---

✅ **Quick Recap Table**

| Topic                         | Key Point                                               | Example/Tip                               |
| ----------------------------- | ------------------------------------------------------- | ----------------------------------------- |
| Hibernate vs JPA              | Hibernate = implementation, JPA = spec                  | JPA portable, Hibernate extended features |
| save vs persist               | save → returns ID (Hibernate), persist → void (JPA)     | Use persist in JPA                        |
| Lazy vs Eager                 | Lazy = on-demand, Eager = immediate                     | Prefer Lazy                               |
| @Entity, @Id, @GeneratedValue | Entity mapping annotations                              | Mandatory for ORM                         |
| get vs load                   | get → hits DB, null if missing; load → proxy, exception | Use get if unsure                         |
| Cache                         | 1st = session, 2nd = shared across sessions             | 2nd needs provider                        |
| JPQL vs Native                | JPQL = entity-based, Native = SQL                       | Prefer JPQL                               |
