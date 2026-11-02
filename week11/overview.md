# Week 11: JSON, SQL & PostgreSQL

## Overview

Welcome to Week 11! Learn to work with JSON data format and connect Python to PostgreSQL databases for powerful data management.

## Watch: JSON & SQL

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week11.html
:width: 100%
:label: week11-animation

**Week 11 animation (1:17).** Turning text into data, and talking to a database safely. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**JSON is text**

- JSON is a text format that looks a lot like a Python dictionary. APIs and files hand it to you as a string.
- text is a str, not a dict, even though it has braces and keys.
- So what happens if we treat it like a dictionary?
- A string can only be indexed by position (`text[0]`, `text[1]`, …), not by a key.

**Parse it**

- `json.loads()` (“load string”) parses the text into a real dictionary.
- Now book is a dict and 42 is an int, so lookups and math work. (`json.dumps()` goes the other way: data to text.)

**Query a database**

- Now a database. library.db already has a books table. A patron searches for a title that contains an apostrophe.
- The f-string pastes the title straight into the SQL. Look at the quotes: 'Ender' ends early, and s Game' is left over.
- The database can't read it. Worse, a crafted title could rewrite the query itself. That's SQL injection.

**Use placeholders**

- Never build SQL with f-strings. Put a ? placeholder in the SQL and pass the values separately.
- The database handles the quotes safely, and we get the row back. With PostgreSQL and psycopg, the placeholder is %s instead of ?.

**Key idea:** JSON is text until you parse it. SQL values go in placeholders, never f-strings. `json.loads()` turns JSON text into dictionaries and lists. Pass values to a query separately (? in sqlite3, %s in psycopg) and the database handles the quoting safely.
:::

## Learning Objectives

- Work with JSON data in Python
- Read and write JSON files
- Convert between Python objects and JSON
- Connect to PostgreSQL databases
- Execute SQL queries from Python
- Insert, update, and retrieve data
- Use parameters safely to prevent SQL injection
- Connect with SQLAlchemy and move query results into pandas

## Topics Covered

1. **JSON in Python**
   - What is JSON?
   - json.loads() and json.dumps()
   - Reading/writing JSON files
   - Working with nested JSON

2. **PostgreSQL Basics**
   - What is PostgreSQL?
   - Installing psycopg (version 3)
   - Connecting to databases
   - Creating tables

3. **SQL Operations**
   - SELECT queries
   - INSERT, UPDATE, DELETE
   - WHERE clauses
   - Parameters and safety

4. **Python + PostgreSQL**
   - Executing queries
   - Fetching results
   - Using cursors
   - Transaction management

5. **SQLAlchemy**
   - Engines and connection URLs
   - `text()` queries with named placeholders
   - pandas `read_sql()` and `to_sql()`

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Assignment 2** - Due this week
- **Weekly Discussion** - Participate in forum


## Readings

**Required:**
### JSON
- [Real Python - Working with JSON data](https://realpython.com/python-json/)
- [The Hitchhiker's Guide to Python > JSON](https://docs.python-guide.org/scenarios/json/)
- [W3C > Python JSON](https://www.w3schools.com/python/python_json.asp)
- [The New Stack > Python for Beginners: How to Use JSON in Python](https://thenewstack.io/python-for-beginners-how-to-use-json-in-python/)

### XML
- [Real Python > A Roadmap to XML Parsers in Python](https://realpython.com/python-xml-parser/)
- [The Hitchhiker's Guide to Python > XML Parsing](https://docs.python-guide.org/scenarios/xml/)

### POSTGRESQL
- [FreeCodeCamp > How to Use Postgres in Python](https://www.freecodecamp.org/news/postgresql-in-python/)
- [Psycopg 3 > Basic Module Usage](https://www.psycopg.org/psycopg3/docs/basic/usage.html)
- [PYnative > Python PostgreSQL Tutorial Using Psycopg2](https://pynative.com/python-postgresql-tutorial/) (uses psycopg2, the older version; nearly identical)
- [SQLAlchemy 2.1 > Unified Tutorial](https://docs.sqlalchemy.org/en/21/tutorial/)

---

## JSON in Python - Quick Guide

### JSON Basics

```python
import json

# Python to JSON (serialize)
data = {
    "name": "Alice",
    "age": 25,
    "courses": ["Python", "SQL", "Data Science"]
}

json_string = json.dumps(data, indent=2)
print(json_string)

# JSON to Python (deserialize)
json_data = '{"name": "Bob", "age": 30}'
python_dict = json.loads(json_data)
print(python_dict)
```

### Reading/Writing JSON Files

```python
import json

# Write to file
data = {"students": [{"name": "Alice", "grade": 95}]}
with open("data.json", "w") as file:
    json.dump(data, file, indent=2)

# Read from file
with open("data.json", "r") as file:
    data = json.load(file)
    print(data)
```

## PostgreSQL with Python

### Installing psycopg and SQLAlchemy

Run this once in the VS Code terminal, with your Anaconda environment active:

```bash
pip install "psycopg[binary]" sqlalchemy pandas
```

We use **psycopg 3**, the current PostgreSQL driver for Python. Its module is named `psycopg`. Many older tutorials use `psycopg2`, the previous version; the code looks almost the same, but new projects should use psycopg 3.

### Connecting to Database

```python
import os
import psycopg

# Connection parameters (the password comes from an environment variable)
conn = psycopg.connect(
    host="localhost",
    dbname="mydb",
    user="postgres",
    password=os.environ["PGPASSWORD"],
)

# Create cursor
cursor = conn.cursor()

# Execute query
cursor.execute("SELECT version();")
version = cursor.fetchone()
print(version)

# Close connections
cursor.close()
conn.close()
```

### Better Way - Context Manager

```python
import os
import psycopg

with psycopg.connect(
    host="localhost",
    dbname="mydb",
    user="postgres",
    password=os.environ["PGPASSWORD"],
) as conn:
    with conn.cursor() as cursor:
        cursor.execute("SELECT * FROM students")
        results = cursor.fetchall()
        for row in results:
            print(row)

# When the with block ends, psycopg commits (or rolls back on an error)
# and closes the connection for you.
```

### Rows as Dictionaries

```python
from psycopg.rows import dict_row

with psycopg.connect(..., row_factory=dict_row) as conn:
    row = conn.execute("SELECT name, grade FROM students WHERE id = %s", (1,)).fetchone()
    print(row["name"], row["grade"])
```

### Creating Tables

```python
import psycopg

with psycopg.connect(...) as conn:
    with conn.cursor() as cursor:
        cursor.execute("""
            CREATE TABLE IF NOT EXISTS students (
                id SERIAL PRIMARY KEY,
                name VARCHAR(100),
                age INTEGER,
                grade FLOAT
            )
        """)
        conn.commit()
```

### Inserting Data (Safe Way)

```python
# Use parameters to prevent SQL injection!
with psycopg.connect(...) as conn:
    with conn.cursor() as cursor:
        # Single insert
        cursor.execute(
            "INSERT INTO students (name, age, grade) VALUES (%s, %s, %s)",
            ("Alice", 20, 95.5)
        )
        
        # Multiple inserts
        students = [
            ("Bob", 21, 87.0),
            ("Charlie", 22, 92.5)
        ]
        cursor.executemany(
            "INSERT INTO students (name, age, grade) VALUES (%s, %s, %s)",
            students
        )
        
        conn.commit()
```

### Querying Data

```python
with psycopg.connect(...) as conn:
    with conn.cursor() as cursor:
        # Fetch all
        cursor.execute("SELECT * FROM students")
        all_students = cursor.fetchall()
        
        # Fetch one
        cursor.execute("SELECT * FROM students WHERE id = %s", (1,))
        student = cursor.fetchone()
        
        # Iterate results
        cursor.execute("SELECT name, grade FROM students WHERE grade > %s", (90,))
        for name, grade in cursor:
            print(f"{name}: {grade}")
```

### Updating and Deleting

```python
with psycopg.connect(...) as conn:
    with conn.cursor() as cursor:
        # Update
        cursor.execute(
            "UPDATE students SET grade = %s WHERE name = %s",
            (96.0, "Alice")
        )
        
        # Delete
        cursor.execute(
            "DELETE FROM students WHERE grade < %s",
            (70,)
        )
        
        conn.commit()
```

### Another Way: SQLAlchemy

**SQLAlchemy** sits on top of psycopg. You describe the database once, as a URL, and the rest of your code looks the same whether that database is PostgreSQL or SQLite. It is also what pandas expects for `read_sql()` and `to_sql()`.

```python
import os
import pandas as pd
from sqlalchemy import create_engine, text, URL

# one URL describes the database (the password comes from an environment variable)
url = URL.create(
    "postgresql+psycopg",
    username="postgres",
    password=os.environ["PGPASSWORD"],
    host="localhost",
    port=5432,
    database="mydb",
)
engine = create_engine(url)

# read: named placeholders (:min_grade) with a dictionary of values
with engine.connect() as conn:
    result = conn.execute(
        text("SELECT name, grade FROM students WHERE grade > :min_grade"),
        {"min_grade": 90},
    )
    for row in result:
        print(row.name, row.grade)

# write: engine.begin() commits when the block ends, or rolls back on an error
with engine.begin() as conn:
    conn.execute(
        text("INSERT INTO students (name, age, grade) VALUES (:name, :age, :grade)"),
        {"name": "Dana", "age": 23, "grade": 88.0},
    )

# straight into pandas
df = pd.read_sql(text("SELECT * FROM students"), engine)
print(df.head())

engine.dispose()
```

| | psycopg | SQLAlchemy |
|---|---|---|
| Placeholders | `%s` with a tuple | `:name` with a dictionary |
| Saving changes | `conn.commit()` | `with engine.begin():` |
| Switching databases | PostgreSQL only | change the URL (e.g. `sqlite:///library.db`) |
| With pandas | works, with a warning | what `read_sql()`/`to_sql()` expect |

For the full, runnable version with a library catalog, see [Connecting Python to PostgreSQL](postgres-python.ipynb).

## Practical Example: Student Database

```python
import psycopg
import json

class StudentDatabase:
    def __init__(self, conn_params):
        self.conn_params = conn_params
    
    def add_student(self, name, age, grade):
        with psycopg.connect(**self.conn_params) as conn:
            with conn.cursor() as cursor:
                cursor.execute(
                    "INSERT INTO students (name, age, grade) VALUES (%s, %s, %s)",
                    (name, age, grade)
                )
                conn.commit()
    
    def get_all_students(self):
        with psycopg.connect(**self.conn_params) as conn:
            with conn.cursor() as cursor:
                cursor.execute("SELECT * FROM students ORDER BY name")
                return cursor.fetchall()
    
    def export_to_json(self, filename):
        students = self.get_all_students()
        data = [
            {"id": s[0], "name": s[1], "age": s[2], "grade": s[3]}
            for s in students
        ]
        with open(filename, "w") as file:
            json.dump(data, file, indent=2)

# Use it
db = StudentDatabase({
    "host": "localhost",
    "dbname": "school",
    "user": "user",
    "password": "pass"
})

db.add_student("Alice", 20, 95.5)
students = db.get_all_students()
db.export_to_json("students.json")
```

## Summary

✅ **JSON** - Lightweight data format  
✅ **json module** - Parse and generate JSON  
✅ **PostgreSQL** - Powerful relational database  
✅ **psycopg** - Python PostgreSQL adapter (version 3)  
✅ **Parameters** - Safe SQL execution  
✅ **CRUD operations** - Create, Read, Update, Delete  
✅ **SQLAlchemy** - One URL, any database; the bridge to pandas  
