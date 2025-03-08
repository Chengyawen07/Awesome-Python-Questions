# Python Interview Part4

### **21. Mutable and Immutable Data Types in Python**

**Core Answer:**

- Immutable types  float, str, tuple
  - Cannot be modified after creation.
  - If reassigned, a new memory address is created.
- Mutable types  list, dict, set
  - Can be modified in place.
  - Memory address remains the same after modification.

**Example Code:**

```python
# Immutable types
a = "hello"
print(id(a))  # Address of the object
a += " world"
print(id(a))  # Different address

# Mutable types
b = [1, 2, 3]
print(id(b))  # Initial address
b.append(4)
print(id(b))  # Same address, modified in place
```

------

### **22. Remove duplicates from a string and sort the characters**

**Core Answer:**

- Use `set()` to remove duplicates.
- Convert to `list` and sort using `sorted()`.

**Example Code:**

```python
s = "ajldjlajfdljfddd"
unique_sorted = "".join(sorted(set(s)))
print(unique_sorted)  # Output: "adfjl"
```

------

### **23. Lambda function to multiply two numbers**

**Core Answer:**

- Lambda functions are anonymous functions used for short operations.

**Example Code:**

```python
multiply = lambda x, y: x * y
print(multiply(3, 4))  # Output: 12
```

------

### **24. Sort dictionary by keys**

**Core Answer:**

- Use `sorted()` with `dict.items()`.

**Example Code:**

```python
dic = {"name": "zs", "age": 18, "city": "深圳", "tel": "1362626627"}
sorted_dict = dict(sorted(dic.items()))
print(sorted_dict)
# Output: {'age': 18, 'city': '深圳', 'name': 'zs', 'tel': '1362626627'}
```

------

### **25. Count word occurrences using `collections.Counter`**

**Core Answer:**

- `Counter()` creates a dictionary with character counts.

**Example Code:**

```python
from collections import Counter

s = "kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h"
word_count = Counter(s)
print(word_count)
```

------

### **26. Remove English words and numbers from a string using regex**

**Core Answer:**

- Use `re.sub()` to replace unwanted characters.

**Example Code:**

```python
import re

a = "not 404 found 张三 99 深圳"
filtered_text = re.sub(r'[a-zA-Z0-9]', '', a).strip()
print(filtered_text)  # Output: "张三  深圳"
```

------

### **27. Use `filter()` to get all odd numbers from a list**

**Core Answer:**

- `filter()` applies a function to each element and keeps those returning `True`.

**Example Code:**

```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
odd_numbers = list(filter(lambda x: x % 2 != 0, a))
print(odd_numbers)  # Output: [1, 3, 5, 7, 9]
```

------

### **28. List comprehension to get all odd numbers**

**Core Answer:**

- Use `[x for x in list if condition]`.

**Example Code:**

```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
odd_numbers = [x for x in a if x % 2 != 0]
print(odd_numbers)  # Output: [1, 3, 5, 7, 9]
```

------

### **29. Purpose of `re.compile()`**

**Core Answer:**

- `re.compile()` compiles a regular expression for reuse, improving performance.

**Example Code:**

```python
import re

pattern = re.compile(r'\d+')  # Matches digits
result = pattern.findall("abc123def456")
print(result)  # Output: ['123', '456']
```

------

### **30. Data types of `a = (1,)`, `b = (1)`, `c = ("1")`**

**Core Answer:**

- `a = (1,)` → **Tuple** (comma makes it a tuple).
- `b = (1)` → **Integer** (parentheses do not define a tuple).
- `c = ("1")` → **String** (single element without a comma remains a string).

**Example Code:**

```python
a = (1,)
b = (1)
c = ("1")

print(type(a))  # Output: <class 'tuple'>
print(type(b))  # Output: <class 'int'>
print(type(c))  # Output: <class 'str'>
```

