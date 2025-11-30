Below is a **complete, interview-ready guide** covering **large entity optimization**, **lazy loading**, **REST API design**, **microservice-safe entity modeling**, **N+1 solutions**, **pagination**, **sorting**, **Criteria queries**, and more.

Everything includes **clear explanations + examples**.

---

# ✅ **1. How did you optimize performance in large entity relationships?**

Common real-world optimizations:

---

### **✔ 1. Use LAZY loading on all collections**

Large lists (e.g., orders, tasks, comments) must always be LAZY:

```java
@OneToMany(mappedBy = "department", fetch = FetchType.LAZY)
private List<Employee> employees;
```

---

### **✔ 2. Use FETCH JOIN only when needed**

Example:

```java
@Query("SELECT d FROM Department d JOIN FETCH d.employees WHERE d.id = :id")
Department getDepartmentWithEmployees(Long id);
```

---

### **✔ 3. Use @BatchSize or FetchMode.SUBSELECT for massive collections**

```java
@BatchSize(size = 20)
@OneToMany(mappedBy = "department")
private List<Employee> employees;
```

This reduces N+1 queries dramatically.

---

### **✔ 4. Avoid EAGER (VERY IMPORTANT)**

EAGER creates unexpected large joins → slow queries.

---

### **✔ 5. Use DTO projections instead of loading full entities**

```java
@Query("SELECT new com.dto.EmployeeDto(e.id, e.name) FROM Employee e")
List<EmployeeDto> findAllEmployees();
```

---

### **✔ 6. Use indexes on foreign key columns**

```sql
CREATE INDEX idx_employee_department ON employee(department_id);
```

---

# 🟢 Answer you can say in interview:

> “I optimized performance by avoiding EAGER fetching, using DTO projections, fixing N+1 issues with fetch join and @BatchSize, and adding DB indexes. For large collections, I used pagination + criteria filters instead of loading full entities.”

---

# ✅ **2. How did you solve Lazy loading issues in REST APIs?**

LazyInitializationException happens when REST controller tries to serialize a lazy field **outside transaction**.

### Solutions:

---

### **✔ Solution 1 — Use DTOs (Best Practice)**

```java
public class DepartmentDto {
    private Long id;
    private String name;
    private List<EmployeeDto> employees;
}
```

---

### **✔ Solution 2 — Use Fetch Join only in query**

```java
@Query("SELECT d FROM Department d JOIN FETCH d.employees WHERE d.id = :id")
Department getDepartmentWithEmployees(Long id);
```

---

### **✔ Solution 3 — Use EntityGraph**

```java
@EntityGraph(attributePaths = {"employees"})
Department findById(Long id);
```

---

### **✔ Solution 4 — Avoid returning Entities directly**

Never do this:

```java
return employee;
```

Always:

```java
return mapper.toDto(employee);
```

---

# 🟢 Interview answer:

> “We avoided returning JPA entities directly. Instead, we used DTOs, fetch joins for required relationships, and EntityGraph to load lazy fields safely within the transaction.”

---

# ✅ **3. How to design entities for microservices?**

Design principles for microservices:

---

### **✔ 1. Entities must be small & bounded context**

One microservice = one domain
Example:

* Employee-Service → Employee, Address
* Payroll-Service → Salary, Payslip
* No shared entity classes across services

---

### **✔ 2. Avoid deep entity graphs (no circular graphs)**

Use flat structures.

---

### **✔ 3. Use ID references instead of direct relationships**

Instead of:

```java
@ManyToOne
private Department department;
```

Use:

```java
private Long departmentId;
```

This avoids cross-service coupling.

---

### **✔ 4. Use DTO-based communication between microservices**

Never expose JPA entities across services.

---

### **✔ 5. No bidirectional relationships**

Microservices should use **unidirectional mappings**.

---

# 🟢 Interview answer:

> “For microservices, I avoid deep entity graphs and bidirectional relationships. I use ID references instead of entity joins to maintain loose coupling between services.”

---

# ✅ **4. How to avoid infinite recursion in JSON (bidirectional mapping)?**

Example of infinite loop:

Employee → Department → Employee → …

---

### Ways to solve:

---

### **✔ 1. Use @JsonManagedReference & @JsonBackReference**

```java
public class Department {
    @JsonManagedReference
    @OneToMany(mappedBy="department")
    private List<Employee> employees;
}

public class Employee {
    @JsonBackReference
    @ManyToOne
    private Department department;
}
```

---

### **✔ 2. Use @JsonIgnore**

```java
@ManyToOne
@JsonIgnore
private Department department;
```

---

### **✔ 3. Use DTOs (best)**

---

# 🟢 Interview answer:

> “We avoided recursion by using @JsonBackReference and DTO mapping to prevent returning entity graphs.”

---

# ✅ **5. How do you manage bidirectional relationships safely?**

### ✔ Maintain both sides consistently

For Example: Department ↔ Employees

```java
public void addEmployee(Employee e) {
    employees.add(e);
    e.setDepartment(this);
}
```

---

### ✔ NEVER use EAGER fetching on collections

Use LAZY.

---

### ✔ Use mappedBy on inverse side

```java
@OneToMany(mappedBy = "department")
private List<Employee> employees;
```

---

### ✔ Use DTO mapping when returning data

Don’t return entity directly.

---

# 🟢 In interview:

> “To manage bidirectional relationships, I always update both sides and ensure the owning side contains the foreign key. Also, I never return entities directly to avoid recursion.”

---

# ✅ **6. Map OneToMany: Department → Employees**

Department:

```java
@Entity
public class Department {
    @Id
    private Long id;

    @OneToMany(mappedBy="department", fetch = FetchType.LAZY)
    private List<Employee> employees;
}
```

Employee:

```java
@Entity
public class Employee {
    @Id
    private Long id;

    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name="department_id")
    private Department department;
}
```

---

# ✅ **7. JPQL query to fetch employees hired in the last 1 year**

```java
@Query("SELECT e FROM Employee e WHERE e.hireDate >= :oneYearAgo")
List<Employee> findRecentEmployees(LocalDate oneYearAgo);
```

Usage:

```java
LocalDate oneYearAgo = LocalDate.now().minusYears(1);
repo.findRecentEmployees(oneYearAgo);
```

---

# ✅ **8. Solve N+1 problem using JOIN FETCH**

```java
@Query("SELECT d FROM Department d JOIN FETCH d.employees WHERE d.id = :id")
Department fetchDepartmentWithEmployees(Long id);
```

Loads everything in **one query**.

---

# ✅ **9. Implement pagination & sorting using JPA**

```java
PageRequest pageRequest = PageRequest.of(0, 10, Sort.by("name").ascending());
Page<Employee> page = employeeRepo.findAll(pageRequest);
```

Repository:

```java
public interface EmployeeRepository extends JpaRepository<Employee, Long> {}
```

---

# ⭐ Pagination + Filters + Sort

```java
Page<Employee> findByDepartmentId(Long id, Pageable pageable);
```

---

# ✅ **10. Custom repository using Criteria API**

### Step 1: Define Custom Interface

```java
public interface EmployeeCustomRepo {
    List<Employee> search(String name, Double minSalary);
}
```

---

### Step 2: Implementation

```java
public class EmployeeCustomRepoImpl implements EmployeeCustomRepo {

    @PersistenceContext
    private EntityManager em;

    @Override
    public List<Employee> search(String name, Double minSalary) {

        CriteriaBuilder cb = em.getCriteriaBuilder();
        CriteriaQuery<Employee> cq = cb.createQuery(Employee.class);
        Root<Employee> root = cq.from(Employee.class);

        List<Predicate> predicates = new ArrayList<>();

        if (name != null) {
            predicates.add(cb.like(root.get("name"), "%" + name + "%"));
        }
        if (minSalary != null) {
            predicates.add(cb.greaterThan(root.get("salary"), minSalary));
        }

        cq.where(predicates.toArray(new Predicate[0]));
        cq.orderBy(cb.asc(root.get("name")));

        return em.createQuery(cq).getResultList();
    }
}
```

---

# 🎯 **Final Summary (Interview Ready)**

| Topic                      | Perfect Answer                        |
| -------------------------- | ------------------------------------- |
| Performance optimization   | Use LAZY, DTOs, join fetch, BatchSize |
| Solving Lazy loading       | DTOs, EntityGraph, fetch join         |
| Microservice entity design | Unidirectional, flat, IDs not joins   |
| Avoid recursion            | @JsonIgnore, @JsonBackReference, DTOs |
| Bidirectional safety       | Maintain both sides, mappedBy, LAZY   |
| OneToMany mapping          | Department ↔ Employees                |
| JPQL (last 1 year)         | `WHERE hireDate >= :date`             |
| Solve N+1                  | fetch join, EntityGraph, BatchSize    |
| Pagination                 | Pageable + PageRequest                |
| Criteria API custom method | dynamic predicates                    |

---

