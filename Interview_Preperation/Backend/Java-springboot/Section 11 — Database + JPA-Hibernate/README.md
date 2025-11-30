## 1. Entity Mapping

1. What is an Entity in JPA?
2. What is the purpose of `@Entity` and `@Table` annotations?
3. Difference between `@Id`, `@GeneratedValue`, and generation strategies.
4. What is `@Column` and when do you customize it?
5. Difference between `@OneToOne`, `@OneToMany`, `@ManyToOne`, and `@ManyToMany`.
6. What is owning side and inverse side in relationships?
7. Difference between `@JoinColumn` and `@JoinColumns`.
8. What is cascade type? Explain different cascade options.
9. What is `orphanRemoval` and how does it work?
10. What is the difference between unidirectional and bidirectional mapping?
11. How do you map composite primary keys?
12. Difference between `@EmbeddedId` and `@IdClass`.
13. How do you map a join table?
14. What is the use of `@MappedSuperclass`?
15. Difference between `@Inheritance` strategies (SINGLE_TABLE, JOINED, TABLE_PER_CLASS).
16. What is entity life cycle?
17. What problems did you face while mapping entities in real projects?

---

## 2. Lazy vs Eager Loading

1. What is Lazy loading in JPA?
2. What is Eager loading?
3. Default fetch strategies of:

   * `@ManyToOne`
   * `@OneToMany`
4. Difference between LazyInitializationException and Eager behavior.
5. What is `FetchType.LAZY` and `FetchType.EAGER`?
6. Real project scenario where Lazy loading caused an issue.
7. How do you fix LazyInitializationException?
8. Difference between join fetch and default fetch.
9. How does Hibernate proxy work in lazy loading?
10. Can you change fetch type at query level without changing annotation?
11. Why is EAGER fetching dangerous in production?
12. When would you intentionally use EAGER fetching?
13. Difference between `@EntityGraph` and fetch join.
14. What is bytecode enhancement in relation to lazy loading?
15. Best practices for Lazy loading in REST APIs.

---

## 3. N+1 Problem

1. What is the N+1 query problem?
2. Give a real-world example of N+1 problem.
3. How does N+1 degrade application performance?
4. How do you identify N+1 issue?
5. How to solve N+1 problem using `JOIN FETCH`?
6. How `@EntityGraph` helps solve N+1?
7. Difference between fetch join and normal join.
8. How to prevent N+1 in Spring Data JPA repositories?
9. What tools have you used to detect N+1 problem?
10. What is subselect fetching in Hibernate?
11. Difference between batch fetching and join fetching.
12. What is Hibernate `@BatchSize`?
13. How pagination behaves with fetch join?
14. Can caching solve N+1 problem?
15. Real-world case where you optimized N+1 problem.

---

## 4. Criteria API

1. What is Criteria API?
2. Difference between Criteria API and JPQL.
3. What are advantages of Criteria API?
4. When do you prefer Criteria API over JPQL?
5. What is `CriteriaBuilder`?
6. What is `CriteriaQuery`?
7. What is `Root` in Criteria API?
8. How do you perform dynamic queries using Criteria API?
9. How do you add predicates dynamically?
10. How do you handle joins in Criteria API?
11. How do you implement pagination using Criteria API?
12. How do you use Criteria API for complex filtering?
13. What is `Specification` in Spring Data JPA?
14. Difference between Criteria API and QueryDSL.
15. How did you use Criteria/Specification in your project?

---

## 🔥 Real Project Scenario Questions

1. How did you optimize performance in large entity relationships?
2. How did you solve Lazy loading issues in REST APIs?
3. How to design entities for microservices?
4. How to avoid infinite recursion while returning entities in JSON?
5. How do you manage bidirectional relationships safely?
6. Map OneToMany: Department → Employees.
7. Write a JPQL query to fetch all employees hired in the last 1 year.
8. Solve N+1 problem using join fetch.
9. Implement pagination & sorting using JPA.
10. Write a custom repository method using Criteria API.
---

�
