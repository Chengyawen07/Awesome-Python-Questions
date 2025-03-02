# Python Interview Part2

------

### **1. One-liner to calculate the sum of numbers from 1 to 100**

**Core Answer:** Use the built-in `sum()` function.

**Example Code:**

```python
print(sum(range(1, 101)))  # Output: 5050
```

------

### **2. How to modify a global variable inside a function?**

**Core Answer:** Use the `global` keyword inside the function.

**Example Code:**

```python
x = 10

def modify_global():
    global x  # Declare that we're modifying the global variable
    x = 20

modify_global()
print(x)  # Output: 20
```

------

### **3. List five Python standard libraries**

**Core Answer:**

- `os`: Provides functions for interacting with the operating system.
- `sys`: Used for accessing system-specific parameters and functions.
- `re`: Handles regular expressions.
- `math`: Provides mathematical functions.
- `datetime`: Handles date and time operations.

**Example Code:**

```python
import os
import sys
import re
import math
import datetime

print(os.name)  # Prints the name of the OS
print(sys.argv)  # Gets command-line arguments
print(re.findall(r"\d+", "hello123world456"))  # ['123', '456']
print(math.sqrt(16))  # 4.0
print(datetime.datetime.now())  # Prints current date & time
```

------

### **4. How to remove a key from a dictionary and merge two dictionaries?**

**Core Answer:**

- Remove a key using `del` or `pop()`.
- Merge dictionaries using `update()` or `|` (Python 3.9+).

**Example Code:**

```python
# Removing a key
my_dict = {"a": 1, "b": 2, "c": 3}
del my_dict["b"]
print(my_dict)  # {'a': 1, 'c': 3}

# Merging dictionaries
dict1 = {"x": 10, "y": 20}
dict2 = {"y": 30, "z": 40}

dict1.update(dict2)  # Using update()
print(dict1)  # {'x': 10, 'y': 30, 'z': 40}

# Using Python 3.9+ merge operator
dict3 = dict1 | dict2
print(dict3)  # {'x': 10, 'y': 30, 'z': 40}
```

------

### **5. Explain Python's Global Interpreter Lock (GIL)**

**Core Answer:**

- The **Global Interpreter Lock (GIL)** ensures that only **one** thread executes Python bytecode at a time.
- This makes multi-threading ineffective for CPU-bound tasks.
- For **I/O-bound tasks**, Python threads can still be useful.
- Use **multiprocessing** instead of threading for CPU-intensive tasks.

**Example Code:**

```python
import threading

def worker():
    for _ in range(5):
        print(threading.current_thread().name)

t1 = threading.Thread(target=worker)
t2 = threading.Thread(target=worker)
t1.start()
t2.start()
t1.join()
t2.join()
```

**Note:** Due to GIL, Python threads do not run truly in parallel.

------

### **6. How to remove duplicates from a list in Python?**

**Core Answer:**

- Use **sets** to remove duplicates (unordered).
- Use `dict.fromkeys()` to remove duplicates while preserving order.

**Example Code:**

```python
# Using a set (order is not preserved)
lst = [1, 2, 2, 3, 4, 4, 5]
unique_list = list(set(lst))
print(unique_list)  # [1, 2, 3, 4, 5] (order may vary)

# Using `dict.fromkeys()` to maintain order
unique_list = list(dict.fromkeys(lst))
print(unique_list)  # [1, 2, 3, 4, 5]
```

------

### **7. What do `\*args` and `\**kwargs` mean in Python?**

**Core Answer:**

- `*args` allows passing **multiple positional arguments** to a function (received as a tuple).
- `**kwargs` allows passing **multiple keyword arguments** to a function (received as a dictionary).

**Example Code:**

```python
def demo_function(*args, **kwargs):
    print("args:", args)
    print("kwargs:", kwargs)

demo_function(1, 2, 3, name="Alice", age=25)
# args: (1, 2, 3)
# kwargs: {'name': 'Alice', 'age': 25}
```

------

### **8. Difference between `range(100)` in Python 2 and Python 3**

**Core Answer:**

- In **Python 2**, `range(100)` returns a **list**, consuming more memory.
- In **Python 3**, `range(100)` returns a **generator (iterator)**, making it memory efficient.

**Example Code:**

```python
# Python 2:
# range(100) -> returns [0, 1, 2, ..., 99] (occupies memory)
# xrange(100) -> returns a generator (lazy evaluation)

# Python 3:
r = range(100)
print(type(r))  # <class 'range'> (iterator)
print(list(r)[:5])  # [0, 1, 2, 3, 4]
```

------

### **9. What characteristics must a language have to support decorators?**

**Core Answer:**

- A language must support **higher-order functions**, meaning functions can be passed as arguments.

**Example Code:**

```python
def decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function call
# Hello!
# After function call
```

------

### **10. List the built-in data types in Python**

**Core Answer:**

- **Numeric types**: `int`, `float`, `complex`
- **Boolean type**: `bool`
- **Sequence types**: `str`, `list`, `tuple`, `range`
- **Set types**: `set`, `frozenset`
- **Mapping type**: `dict`

**Example Code:**

```python
num = 10  # int
flag = True  # bool
text = "hello"  # str
lst = [1, 2, 3]  # list
tup = (1, 2, 3)  # tuple
rng = range(5)  # range
st = {1, 2, 3}  # set
dct = {"a": 1, "b": 2}  # dict

print(type(num), type(flag), type(text), type(lst), type(tup), type(rng), type(st), type(dct))
```

