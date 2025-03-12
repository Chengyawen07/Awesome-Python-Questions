# Python 高频面试题 Part5

### **31. 合并两个列表 `[1,5,7,9]` 和 `[2,2,6,8]`**

**核心回答：**

- <u>**`extend()`**：将另一个列表的元素逐个添加到当前列表</u>（区别于 `append()` 整体添加）。
- **`sorted()`**：合并后排序。

**示例代码：**

```python
list1 = [1, 5, 7, 9]
list2 = [2, 2, 6, 8]

list1.extend(list2)  # 直接合并列表
sorted_list = sorted(list1)  # 排序

print(sorted_list)  # 输出: [1, 2, 2, 5, 6, 7, 8, 9]
```

------

### PS：

`sorted()` 和 `sort()` 都可以对列表排序，但**它们的区别在于：**

| **函数**           | **是否修改原列表？** | **返回值**                 | **适用场景**                                       |
| ------------------ | -------------------- | -------------------------- | -------------------------------------------------- |
| `sorted(iterable)` | ❌ **不会修改原列表** | **返回一个新排序后的列表** | **适用于任何可迭代对象**（如列表、元组、字符串等） |
| `list.sort()`      | ✅ **会修改原列表**   | **返回 `None`**            | **只能用于列表**，效率更高                         |

### **总结**

| **用法**                 | `sorted()`                             | `sort()`                   |
| ------------------------ | -------------------------------------- | -------------------------- |
| **是否修改原列表？**     | ❌ 不修改                               | ✅ 直接修改                 |
| **返回值**               | 新排序后的列表                         | `None`（无返回值）         |
| **适用于哪些数据类型？** | 任何可迭代对象（列表、元组、字符串等） | 仅限列表                   |
| **适用场景**             | 需要**保留原数据**，返回新列表         | 需要**原地排序**，提高性能 |

如果你不想改变原列表，用 **`sorted()`**；
如果你只需要对列表排序，直接用 **`sort()`**，更快



### **32. 删除文件的方法**

**核心回答：**

- **Python**：使用 `os.remove(文件名)`
- **Linux 命令行**：使用 `rm 文件名`

**示例代码：**

```python
import os
os.remove("test.txt")  # 删除 test.txt 文件
```

**Linux 命令行：**

```sh
rm test.txt  # 删除 test.txt 文件
```

------

### **33. 记录日志的时间戳**

- log日志中，我们需要用时间戳记录error,warning等的发生时间，请用datetime模块打印当前时间戳

**核心回答：**

- 使用 `datetime` 模块格式化当前时间。
- 可以使用 .strftime() 方法，把时间格式化为字符串
- datetime.now() vs datetime.today()：now() 更推荐，因为它可以支持时区

**示例代码：**

```python
from datetime import datetime

# 获取当前时间
timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
print(timestamp)  # 输出示例: 2023-04-01 11:38:54

# 获取星期
weekday = datetime.now().strftime("%A")
print(weekday)  # 输出: Monday (英文) 或 星期一（中文）
```

------

### **34. 数据库优化查询方法**

**核心回答：**

- **外键（Foreign Key）**：减少数据冗余，提升数据完整性。
- **索引（Index）**：加速查询，提高搜索效率。
- **联合查询（Join）**：减少多次查询，提高效率。
- **选择特定字段（SELECT specific columns）**：避免 `SELECT *`，提高查询速度。

**示例 SQL 查询优化：**

```sql
-- 建立索引
CREATE INDEX idx_name ON student(name);

-- 仅查询需要的字段
SELECT name, age FROM student WHERE age > 18;

-- 通过联合查询优化查询
SELECT student.name, class.class_name 
FROM student 
JOIN class ON student.class_id = class.id;
```

------

### **35. Python 中用于绘制统计图的开源库**

**核心回答：**

- **`matplotlib`**：最常用的绘图库，支持折线图、条形图等。
- **`seaborn`**：基于 `matplotlib`，更适合统计数据可视化。
- **`plotly`**：支持交互式图表。

**示例代码（绘制条形图）：**

```python
import matplotlib.pyplot as plt

data = {"A": 5, "B": 10, "C": 7}
plt.bar(data.keys(), data.values())
plt.show()
```

------

### **36. 自定义异常**

- 写一段自定义异常代码

**核心回答：**

- 使用 `raise` 关键字抛出自定义异常。
- 语法：
- 1、直接抛出一个异常
  - raise ValueError("这是一个 ValueError 异常")
  - 2、自定义异常：
- 你可以继承 Exception 类，创建自己的异常：
  - class MyCustomError(Exception)
  -  raise MyCustomError("Value")

**示例代码：**

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

### **37. `.\*` 和 `.\*?` 的区别**

**核心回答：**

- `.*` 是 **贪婪匹配**（尽可能匹配更多字符）。

  - `.*` **会尽可能多地匹配**，它会**一直匹配到最后一个 `</div>`**。

  - **`.\*` 先匹配 `hello world`**，但它发现后面还有 `</div><div>test</div>`，所以继续匹配。

    **最终，匹配到 `</div><div>test`，直到遇到最后一个 `</div>`**。

  - 最终结果：['hello world</div><div>test']

- `.*?` 是 **非贪婪匹配**（尽可能匹配更少字符）。

- 正则：`<div>(.*?)</div>`

- `.*?` **是非贪婪的，会尽可能少地匹配**，遇到 **第一个 `</div>` 就停下**

- 结果：['hello world', 'test']

### **适用场景**

- 如果**希望获取完整的内容**（可能包含多个 `<div>` 之间的内容），用 **贪婪 `.\*`**。
- 如果**希望逐个提取每个 `<div>` 内的内容**，用 **非贪婪 `.\*?`**。

**示例代码：**

```python
import re

text = "<div>hello world</div><div>test</div>"

# 贪婪匹配
greedy_match = re.findall(r"<div>(.*)</div>", text)
print(greedy_match)  # 输出: ['hello world</div><div>test']

# 非贪婪匹配
non_greedy_match = re.findall(r"<div>(.*?)</div>", text)
print(non_greedy_match)  # 输出: ['hello world', 'test']
```

------

### **38. Django ORM**

**核心回答：**

- **ORM（对象关系映射）** 使开发者 **无需写 SQL 语句**，直接使用 Python 操作数据库。
- Django 的 ORM 可轻松切换数据库，如 MySQL、PostgreSQL、SQLite。

**示例代码（Django ORM 操作数据库）：**

```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()

# 查询所有学生
students = Student.objects.all()

# 查询单个学生
student = Student.objects.get(id=1)

# 添加学生
new_student = Student(name="Alice", age=22)
new_student.save()

# 删除学生
student.delete()
```

------

### **39. 将 `[[1,2],[3,4],[5,6]]` 展平为 `[1,2,3,4,5,6]`**

**核心回答：**

- **列表推导式**：遍历嵌套列表并提取元素。
- **<u>NumPy 方法：`numpy.flatten()` 可以高效展平数组。</u>**

**示例代码（列表推导式）：**

```python
a = [[1, 2], [3, 4], [5, 6]]
flattened = [j for i in a for j in i]
print(flattened)  # 输出: [1, 2, 3, 4, 5, 6]
```

**示例代码（NumPy 方法）：**

```python
import numpy as np

a = np.array([[1, 2], [3, 4], [5, 6]])
flattened = a.flatten()
print(flattened.tolist())  # 输出: [1, 2, 3, 4, 5, 6]
```

------

### **40. `x.join(y)` 和 `x.join(z)` 的区别**

- x="abc",y="def",z=["d","e","f"],分别求出x.join(y)和x.join(z)返回的结果

**核心回答：**

- `join()` **在可迭代对象的元素之间插入指定的字符串**。
- <u>结果始终是一个 **字符串**。</u>
- 只要 x 是字符串，<u>x.join(iterable) 的结果一定是字符串，不管 iterable 是字符串、列表、元组等</u>，它都会在元素之间插入 x，最终返回一个新的字符串。

**示例代码：**

```python
x = "abc"
y = "def"
z = ["d", "e", "f"]

print(x.join(y))  # "dabceabcf"
print(x.join(z))  # "dabceabcf"
```

**解释：**

- `y = "def"` 是字符串，因此 `"abc".join("def")` 逐个字符插入，形成 `"dabceabcf"`。
- <u>`z = ["d", "e", "f"]` 是列表，`join()` 也适用于列表，结果一致。</u>

**补充：`os.path.join()`**

- 用<u>于 **拼接路径**，与字符串的 `join()` 逻辑不同。</u>

**示例代码：**

```python
import os
path = os.path.join("home", "user", "file.txt")
print(path)  # 输出: "home/user/file.txt" (Linux) 或 "home\user\file.txt" (Windows)
```

