## 🧩 **1. Basic Level (Core Concepts)**

1. What is MongoDB, and how is it different from a relational database?
2. Explain the concept of **collections** and **documents** in MongoDB.
3. What is a **BSON** document? How does it differ from JSON?
4. How do you create a database and a collection in MongoDB?
5. What is the difference between `insertOne()` and `insertMany()`?
6. How do you retrieve all documents from a collection?
7. Explain the purpose of the `_id` field.
8. What are **indexes** in MongoDB, and why are they important?
9. How can you update multiple documents at once?
10. How do you delete a document or an entire collection?

---

## ⚙️ **2. Intermediate Level (Queries and Design)**

1. What is the difference between **embedded documents** and **references**?
   → When would you use one over the other?

2. Explain the difference between `$set`, `$push`, `$inc`, and `$addToSet` operators.

3. How do you sort, limit, and skip results in a MongoDB query?

4. What are **aggregation pipelines**?
   → Explain the role of stages like `$match`, `$group`, `$sort`, `$project`, `$lookup`.

5. How do you perform a **join** operation in MongoDB?

6. How can you perform **text search** or **pattern matching** in MongoDB?

7. How can you find all documents where a specific field exists or doesn’t exist?

8. Explain **schema design best practices** in MongoDB.

9. What are **capped collections**?

10. What is the difference between `find()` and `aggregate()`?

---

## 🧠 **3. Advanced / Real-World Scenarios**

1. What is **sharding** in MongoDB? Why is it needed?
2. What is **replication**, and how does MongoDB achieve high availability?
3. What happens when the **primary** node goes down?
4. How does **write concern** and **read concern** work?
5. How do you ensure data consistency in distributed MongoDB setups?
6. What are **transactions** in MongoDB? When would you use them?
7. How can you improve **query performance** in MongoDB?
8. How do you handle **large datasets** or **pagination** efficiently?
9. How can you use **MongoDB Atlas** for deployment and monitoring?
10. Explain a scenario where MongoDB is not a good fit.

---

## 🧑‍💻 **4. Hands-On / Coding Type Questions**

1. Write a query to:

   * Find all employees whose salary > 50,000 and department = “IT”.

     ```js
     db.employees.find({ department: "IT", salary: { $gt: 50000 } })
     ```
2. Increment a product’s stock count by 5.

   ```js
   db.products.updateOne({ _id: 101 }, { $inc: { stock: 5 } })
   ```
3. Get total sales amount grouped by each month.

   ```js
   db.sales.aggregate([
     { $group: { _id: { $month: "$date" }, totalSales: { $sum: "$amount" } } },
     { $sort: { "_id": 1 } }
   ])
   ```
4. Find documents where “skills” array contains both “Python” and “MongoDB”.

   ```js
   db.users.find({ skills: { $all: ["Python", "MongoDB"] } })
   ```
5. Perform a lookup between `orders` and `customers`.

   ```js
   db.orders.aggregate([
     { $lookup: { from: "customers", localField: "customer_id", foreignField: "_id", as: "customer_info" } }
   ])
   ```

---

## 🧾 **5. Frequently Asked in Interviews**

* Difference between **MongoDB and SQL joins**?
* How do you handle **schema migrations** in MongoDB?
* How do you perform **data validation** in MongoDB?
* What are **aggregation framework advantages**?
* Explain **ObjectId structure** (timestamp, machine id, process id, counter).
* Difference between **findOne()** and **find()**?
* How do you **backup and restore** MongoDB databases?
* How does **MongoDB handle concurrency**?
