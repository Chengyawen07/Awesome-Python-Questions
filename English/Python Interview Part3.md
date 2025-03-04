# Python Interview Part3

------

### **11. Difference between `__new__` and `__init__` in OOP**

**Core Answer:**

- `__new__` is responsible for **creating an instance** and must return an instance.
- `__init__` is responsible for **initializing an instance** and does not return anything.

**Key Differences:**

| Method     | Purpose                 | Needs Return Value?               | When Called       | Parameter                   |
| ---------- | ----------------------- | --------------------------------- | ----------------- | --------------------------- |
| `__new__`  | Creates an instance     | **Yes** (must return an instance) | Before `__init__` | `cls` (class reference)     |
| `__init__` | Initializes an instance | **No**                            | After `__new__`   | `self` (instance reference) |

**Example Code:**

```python
class A:
    def __new__(cls, *args, **kwargs):
        print("Creating instance")
        return super(A, cls).__new__(cls)

    def __init__(self, value):
        print("Initializing instance")
        self.value = value

a = A(10)
# Output:
# Creating instance
# Initializing instance
```

------

### **12. What does `with` do when opening files?**

**Core Answer:**

- `with` automatically **manages file resources**, ensuring the file is closed even if an error occurs.
- Traditional file handling requires `try-finally` to ensure the file is closed.

**Example Code:**

```python
# Traditional way
try:
    f = open("file.txt", "r")
    content = f.read()
finally:
    f.close()  # Must manually close the file

# Using `with`
with open("file.txt", "r") as f:
    content = f.read()  # `with` automatically closes the file
```

------

### **13. Use `map()` to compute squares and filter numbers greater than 10**

**Core Answer:**

- `map()` applies a function to each element in a list.
- List comprehension is used for **filtering**.

**Example Code:**

```python
nums = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, nums))
filtered = [x for x in squared if x > 10]

print(squared)  # [1, 4, 9, 16, 25]
print(filtered)  # [16, 25]
```

------

### **14. Generate random integers, random decimals, and values between 0-1**

**Core Answer:**

- `random.randint(a, b)`: Generates an integer in range `[a, b]`.
- `np.random.randn(n)`: Generates `n` random floating numbers.
- `random.random()`: Generates a float between `0-1`.

**Example Code:**

```python
import random
import numpy as np

print(random.randint(1, 10))  # Random integer between 1 and 10
print(np.random.randn(5))  # Generates 5 random float numbers
print(random.random())  # Random float between 0 and 1
```

------

### **15. How to avoid escape sequences in strings?**

**Core Answer:**

- Prefixing a string with `r` makes it a **raw string**, preventing escape sequences.

**Example Code:**

```python
print(r"C:\new\test")  # Output: C:\new\test
print("C:\\new\\test")  # Alternative way: C:\new\test
```

------

### **16. Regex to extract content inside `<div class="xxx">China</div>`**

**Core Answer:**

- Use `re.search()` and `group()` to extract content inside the `<div>` tag.

**Example Code:**

```python
import re

html = '<div class="nam">China</div>'
match = re.search(r'<div class=".*?">(.*?)</div>', html)

if match:
    print(match.group(1))  # Output: China
```

------

### **17. Example of assertion (`assert`)**

**Core Answer:**

- `assert` checks conditions during debugging; if the condition is `False`, an `AssertionError` is raised.

**Example Code:**

```python
x = 5
assert x > 0  # No error
assert x < 0, "x must be less than 0"  # Raises AssertionError
```

------

### **18. SQL Query to remove duplicate names in `student` table**

**Core Answer:**

- Use the `DISTINCT` keyword to eliminate duplicates.

**SQL Query:**

```sql
SELECT DISTINCT name FROM student;
```

------

### **19. 10 Commonly Used Linux Commands**

**Core Answer:**

| Command | Purpose                               |
| ------- | ------------------------------------- |
| `ls`    | List directory contents               |
| `pwd`   | Print working directory               |
| `cd`    | Change directory                      |
| `touch` | Create a file                         |
| `rm`    | Remove files or directories           |
| `mkdir` | Create a new directory                |
| `tree`  | Display directory structure as a tree |
| `cp`    | Copy files and directories            |
| `mv`    | Move or rename files                  |
| `cat`   | Display file contents                 |
| `grep`  | Search inside files                   |
| `echo`  | Print text to the terminal            |

**Example:**

```sh
ls -l  # List files in detailed format
cd /home  # Change to /home directory
touch test.txt  # Create test.txt
grep "python" file.txt  # Search for "python" in file.txt
```

------

### **20. Differences between Python 2 and Python 3 (List 5)**

| **Feature**         | **Python 2**                        | **Python 3**                        |
| ------------------- | ----------------------------------- | ----------------------------------- |
| **Print Statement** | `print "hello"`                     | `print("hello")`                    |
| **`range()`**       | Returns a list (`range(1,10)`)      | Returns an iterator (`range(1,10)`) |
| **Encoding**        | Default `ASCII`                     | Default `UTF-8`                     |
| **String Types**    | `unicode` for text, `str` for bytes | `str` for text, `bytes` for bytes   |
| **Input Function**  | `raw_input()`                       | `input()`                           |

**Example Code:**

```python
# Python 3
print("Hello")  # Must use parentheses
print(list(range(3)))  # [0, 1, 2]
print(type("hello"))  # <class 'str'>
```

