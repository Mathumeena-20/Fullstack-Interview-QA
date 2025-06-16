# ✅ 1. **How Do You Connect a Python App to a Database?**

### 👉 Explanation:

To connect a Python app to a database:

* You need a **database connector** (library).
* You provide **connection details** like host, username, password, port, and database name.
* You use the connector to **execute SQL queries**.

---

### 🔹 Example: Connect to PostgreSQL using `psycopg2`

```python
import psycopg2

# Connect to PostgreSQL
conn = psycopg2.connect(
    host="localhost",
    database="mydb",
    user="postgres",
    password="password"
)

# Create a cursor
cur = conn.cursor()

# Execute a query
cur.execute("SELECT version();")
record = cur.fetchone()
print("Database version:", record)

# Close resources
cur.close()
conn.close()
```

✔️ **Summary:**

* `psycopg2.connect()` establishes a connection.
* `cursor` is used to send SQL commands.
* Always close both the cursor and connection.

---

### ✅ Key Python Database Connectors:

| Database   | Connector              | Example Command                      |
| ---------- | ---------------------- | ------------------------------------ |
| PostgreSQL | psycopg2               | `pip install psycopg2`               |
| MySQL      | mysql-connector-python | `pip install mysql-connector-python` |
| SQLite     | sqlite3 (built-in)     | No installation needed               |

---

# ✅ 2. **What ORMs Have You Used in Python? (e.g., SQLAlchemy, Django ORM)**

### 👉 Explanation:

**ORM** = Object Relational Mapper

* ORMs help you work with databases using **Python objects** instead of writing raw SQL.

### ✔️ Common ORMs:

* **SQLAlchemy:** Most flexible, supports many databases.
* **Django ORM:** Built into Django framework.
* **Peewee:** Lightweight ORM.

---

### 🔹 Example: SQLAlchemy ORM Setup

```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

# Connect to SQLite (can change to other databases)
engine = create_engine('sqlite:///mydb.sqlite', echo=True)

Base = declarative_base()

# Define the table as a Python class
class User(Base):
    __tablename__ = 'users'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    age = Column(Integer)

# Create the table
Base.metadata.create_all(engine)

# Create session
Session = sessionmaker(bind=engine)
session = Session()
```

✔️ **Summary:**

* `create_engine` connects to the database.
* `Base` is the base class for all ORM models.
* SQLAlchemy automatically creates the table structure from the Python class.

---

# ✅ 3. **Explain Basic CRUD Operations Using an ORM in Python**

### 👉 Explanation:

CRUD = **Create, Read, Update, Delete**
These are the four basic operations to manage database records.

---

### 🔹 Full CRUD Example using SQLAlchemy

#### ✅ Create (Insert)

```python
new_user = User(name="Alice", age=25)
session.add(new_user)
session.commit()
```

✔️ Adds a new record to the database.

---

#### ✅ Read (Select)

```python
# Get all users
users = session.query(User).all()

# Get user by condition
user = session.query(User).filter_by(name="Alice").first()
print(user.name, user.age)
```

✔️ Fetches records from the database.

---

#### ✅ Update

```python
user = session.query(User).filter_by(name="Alice").first()
user.age = 30
session.commit()
```

✔️ Updates the selected record.

---

#### ✅ Delete

```python
user = session.query(User).filter_by(name="Alice").first()
session.delete(user)
session.commit()
```

✔️ Deletes the selected record.

---

### 🔹 Quick CRUD Summary Table

| Operation | SQLAlchemy Command                            |
| --------- | --------------------------------------------- |
| Create    | `session.add(object)` → `session.commit()`    |
| Read      | `session.query(Model).all()`                  |
| Update    | Fetch → Modify → `session.commit()`           |
| Delete    | `session.delete(object)` → `session.commit()` |

---

### ✅ Django ORM CRUD Quick Example

```python
# models.py
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()

# Create
User.objects.create(name="Bob", age=20)

# Read
User.objects.all()

# Update
user = User.objects.get(name="Bob")
user.age = 25
user.save()

# Delete
user.delete()
```

✔️ **Django ORM is simpler** than SQLAlchemy because Django automatically handles database sessions.

---

## ✅ Summary:

* **Database connection:** Using connectors like `psycopg2` or `sqlite3`.
* **ORM tools:** SQLAlchemy (manual control), Django ORM (framework integrated).
* **CRUD operations:** Easily performed using ORM’s Python classes instead of raw SQL.

---

👉 If you want, I can:

* Help you build a **mini project** using database + Python.
* Show you **Flask or Django full CRUD web app** step-by-step.

Let me know!
