# Python Interview Part5

### **31. Merge two lists `[1,5,7,9]` and `[2,2,6,8]` into a sorted list**

**Core Answer:**

- **`extend()`**: Adds elements from another iterable to the list.
- **`sorted()`**: Sorts the merged list.

**Example Code:**

```python
list1 = [1, 5, 7, 9]
list2 = [2, 2, 6, 8]

list1.extend(list2)  # Merge the lists
sorted_list = sorted(list1)  # Sort the list

print(sorted_list)  # Output: [1, 2, 2, 5, 6, 7, 8, 9]
```

------

### **32. Methods to delete a file in Python and Linux**

**Core Answer:**

- **Python**: Use `os.remove(filename)`.
- **Linux Command**: Use `rm filename`.

**Example Code:**

```python
import os
os.remove("test.txt")  # Deletes the file "test.txt"
```

**Linux Command:**

```sh
rm test.txt  # Deletes the file "test.txt"
```

------

### **33. Log timestamp in Python**

**Core Answer:**

- Use the `datetime` module to get the current timestamp.

**Example Code:**

```python
from datetime import datetime

# Get current timestamp
timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
print(timestamp)  # Example output: "2023-04-01 11:38:54"

# Get the weekday
weekday = datetime.now().strftime("%A")
print(weekday)  # Output: Monday (English) or 星期一 (Chinese)
```

------

### **34. Database query optimization techniques**

**Core Answer:**

- **Foreign keys**: Reduce redundancy and ensure data integrity.
- **Indexes**: Improve search performance.
- **Joins**: Reduce multiple queries and optimize retrieval.
- **Select specific fields**: Avoid `SELECT *` for better efficiency.

**Optimized SQL Query Example:**

```sql
-- Create an index
CREATE INDEX idx_name ON student(name);

-- Select specific fields instead of SELECT *
SELECT name, age FROM student WHERE age > 18;

-- Use joins to optimize queries
SELECT student.name, class.class_name 
FROM student 
JOIN class ON student.class_id = class.id;
```

------

### **35. Open-source libraries for plotting statistical graphs**

**Core Answer:**

- **`matplotlib`**: Most commonly used plotting library for bar charts, line plots, etc.
- **`seaborn`**: Built on `matplotlib`, suitable for statistical visualizations.
- **`plotly`**: Supports interactive plots.

**Example Code (Bar Chart using `matplotlib`):**

```python
import matplotlib.pyplot as plt

data = {"A": 5, "B": 10, "C": 7}
plt.bar(data.keys(), data.values())
plt.show()
```

------

### **36. Custom exception handling in Python**

**Core Answer:**

- Use `raise` to throw a custom exception.

**Example Code:**

```python
class MyCustomError(Exception):
    def __init__(self, message):
        self.message = message

def check_value(x):
    if x < 0:
        raise MyCustomError("Value cannot be negative!")

try:
    check_value(-1)
except MyCustomError as e:
    print("Error:", e)
```

------

### **37. Difference between `.\*` and `.\*?` in regex**

**Core Answer:**

- `.*` → **Greedy match** (matches as much as possible).
- `.*?` → **Non-greedy match** (matches as little as possible).

**Example Code:**

```python
import re

text = "<div>hello world</div><div>test</div>"

# Greedy match
greedy_match = re.findall(r"<div>(.*)</div>", text)
print(greedy_match)  # Output: ['hello world</div><div>test']

# Non-greedy match
non_greedy_match = re.findall(r"<div>(.*?)</div>", text)
print(non_greedy_match)  # Output: ['hello world', 'test']
```

------

### **38. What is Django ORM?**

**Core Answer:**

- **ORM (Object-Relational Mapping)** allows developers to interact with databases using Python objects instead of SQL queries.
- Django ORM abstracts database operations, allowing easy switching between MySQL, PostgreSQL, SQLite, etc.

**Example Code (Django ORM Usage):**

```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()

# Fetch all students
students = Student.objects.all()

# Fetch a single student
student = Student.objects.get(id=1)

# Insert a student
new_student = Student(name="Alice", age=22)
new_student.save()

# Delete a student
student.delete()
```

------

### **39. Flatten `[[1,2],[3,4],[5,6]]` to `[1,2,3,4,5,6]`**

**Core Answer:**

- **List comprehension**: Iterate through nested lists.
- **NumPy method**: Use `numpy.flatten()`.

**Example Code (List Comprehension):**

```python
a = [[1, 2], [3, 4], [5, 6]]
flattened = [j for i in a for j in i]
print(flattened)  # Output: [1, 2, 3, 4, 5, 6]
```

**Example Code (NumPy Method):**

```python
import numpy as np

a = np.array([[1, 2], [3, 4], [5, 6]])
flattened = a.flatten()
print(flattened.tolist())  # Output: [1, 2, 3, 4, 5, 6]
```

------

### **40. Difference between `x.join(y)` and `x.join(z)`**

**Core Answer:**

- `join()` inserts `x` between each element of an iterable.
- The result is always a **string**.

**Example Code:**

```python
x = "abc"
y = "def"
z = ["d", "e", "f"]

print(x.join(y))  # Output: "dabceabcf"
print(x.join(z))  # Output: "dabceabcf"
```

**Explanation:**

- `y = "def"` is a string, so `"abc".join("def")` places `"abc"` between each character, resulting in `"dabceabcf"`.
- `z = ["d", "e", "f"]` is a list, and `join()` works similarly.

**Bonus: `os.path.join()` for path handling**

- Used for joining file paths, different from string `join()`.

**Example Code:**

```python
import os
path = os.path.join("home", "user", "file.txt")
print(path)  # Output: "home/user/file.txt" (Linux) or "home\user\file.txt" (Windows)
```

