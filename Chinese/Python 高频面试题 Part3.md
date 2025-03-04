# Python 高频面试题 Part3

------

### **11. `__new__` vs `__init__`**

**核心回答：**

- `__new__`：用于 **创建实例**，返回一个实例对象。
- `__init__`：用于 **初始化实例**，不返回值。

**区别：**

| 方法       | 作用       | 需要返回值 | 何时调用        | 参数           |
| ---------- | ---------- | ---------- | --------------- | -------------- |
| `__new__`  | 创建实例   | **需要**   | `__init__` 之前 | `cls`（类）    |
| `__init__` | 初始化实例 | **不需要** | `__new__` 之后  | `self`（实例） |

**代码示例：**

```python
class A:
    def __new__(cls, *args, **kwargs):
        print("Creating instance")
        return super(A, cls).__new__(cls)

    def __init__(self, value):
        print("Initializing instance")
        self.value = value

a = A(10)
# 输出：
# Creating instance
# Initializing instance
```

------

### **12. `with` 语句处理文件**

**核心回答：**

- <u>`with` 语句 **自动管理资源**，确保文件即使出现异常也会被正确关闭。</u>
- 传统方法需要 `try-finally` 关闭文件，而 `with` 语句自动执行 `close()`。

**代码示例：**

```python
# 传统方式
try:
    f = open("file.txt", "r")
    content = f.read()
finally:
    f.close()  # 必须手动关闭文件

# with 方式
with open("file.txt", "r") as f:
    content = f.read()  # with 语句自动关闭文件
```

------

### **13. 列表[1,2,3,4,5],请使用map()函数输出[1,4,9,16,25]，并使用列表推导式提取出大于10的数，最终输出[16,25]**

**核心回答：**

- `map()` 用于对列表中的每个元素执行某个函数。
- 列表推导式用于 **过滤符合条件的元素**。

**代码示例：**

```python
nums = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, nums))
filtered = [x for x in squared if x > 10]

print(squared)  # [1, 4, 9, 16, 25]
print(filtered)  # [16, 25]
```

------

### **14. 生成随机整数、随机小数、0-1 之间小数**

**核心回答：**

- `random.randint(a, b)`: 生成范围内的随机整数。
- `np.random.randn(n)`: 生成 `n` 个正态分布的随机小数。
- `random.random()`: 生成 `0-1` 之间的随机小数。

**代码示例：**

```python
import random
import numpy as np

print(random.randint(1, 10))  # 生成 1 到 10 之间的随机整数
print(np.random.randn(5))  # 生成 5 个随机小数
print(random.random())  # 生成 0-1 之间的随机小数
```

------

### **15. 如何避免字符串转义？**

**核心回答：**

- 在字符串前加 `r`，表示原始字符串，不转义 `\`。

**代码示例：**

```python
print(r"C:\new\test")  # 输出：C:\new\test
print("C:\\new\\test")  # 另一种写法：C:\new\test
```

------

### **16. 正则匹配 `<div class="xxx">中国</div>`**

**核心回答：**

- 使用 `re.search()` 和 `group()` 提取 `<div>` 标签内容。

**代码示例：**

```python
import re

html = '<div class="nam">中国</div>'
match = re.search(r'<div class=".*?">(.*?)</div>', html)

if match:
    print(match.group(1))  # 输出：中国
```

------

### **17. Python中断言 (`assert`)方法举例**

**核心回答：**

- <u>`assert` 语句用于 **调试检查**，如果条件为 `False`，会抛出 `AssertionError`。</u>

**代码示例：**

```python
x = 5
assert x > 0  # 正常执行
assert x < 0, "x must be less than 0"  # 断言失败，抛出错误
```

------

### **18. SQL 语句：去除 `student` 表中 `name` 字段的重复值**

- 数据表student有id,name,score,city字段，<u>其中name中的名字可有重复，需要消除重复行</u>,请写sql语句

**核心回答：**

- <u>使用 `DISTINCT` 关键字去重。</u>

**SQL 语句：**

```sql
SELECT DISTINCT name FROM student;
```

------

### **19. 10 个常用 Linux 命令**

**核心回答：**

| 命令    | 作用               |
| ------- | ------------------ |
| `ls`    | 列出目录文件       |
| `pwd`   | 显示当前路径       |
| `cd`    | 切换目录           |
| `touch` | 创建文件           |
| `rm`    | 删除文件或目录     |
| `mkdir` | 创建目录           |
| `tree`  | 以树状结构显示目录 |
| `cp`    | 复制文件或目录     |
| `mv`    | 移动或重命名文件   |
| `cat`   | 查看文件内容       |
| `grep`  | 搜索文件中的内容   |
| `echo`  | 输出字符串或变量   |

**示例：**

```sh
ls -l  # 列出当前目录详细信息
cd /home  # 进入 /home 目录
touch test.txt  # 创建 test.txt 文件
grep "python" file.txt  # 在 file.txt 里搜索 "python"
```

------

### **20. Python 2 vs Python 3（列举 5 个区别）**

| **区别点**     | **Python 2**           | **Python 3**             |
| -------------- | ---------------------- | ------------------------ |
| **打印**       | `print "hello"`        | `print("hello")`         |
| **range()**    | 返回列表 `range(1,10)` | 返回迭代器 `range(1,10)` |
| **编码**       | 默认 `ASCII`           | 默认 `UTF-8`             |
| **字符串类型** | `str` 表示字节序列     | `str` 表示字符串序列     |
| **输入函数**   | `raw_input()`          | `input()`                |

**代码示例：**

```python
# Python 3
print("Hello")  # 需要括号
print(list(range(3)))  # [0, 1, 2]
print(type("hello"))  # str
```

