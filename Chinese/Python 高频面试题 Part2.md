# Python 高频面试题 Part2

### **1. 一行代码实现 1 到 100 之和**

**核心回答：** 使用 `sum()` 函数可以快速求和。

**代码示例：**

```python
print(sum(range(1, 101)))  # 输出 5050
```

------

### **2. 如何在函数内部修改全局变量**

**核心回答：** 使用 `global` 关键字可以在函数内部修改全局变量。

**代码示例：**

```python
x = 10

def modify_global():
    global x  # 声明修改全局变量
    x = 20

modify_global()
print(x)  # 输出 20
```

------

### **3. 列出 5 个 Python 标准库**

**核心回答：**
 Python 标准库提供了一些常用的模块，例如：

- `os`：与操作系统交互，如文件操作、进程管理。
- `sys`：处理 Python 运行时环境，如获取命令行参数。
- `re`：正则表达式匹配和字符串处理。
- `math`：数学计算函数，如三角函数、对数。
- `datetime`：处理日期和时间。

**代码示例：**

```python
import os
import sys
import re
import math
import datetime

print(os.name)  # 输出当前操作系统类型
print(sys.argv)  # 获取命令行参数
print(re.findall(r"\d+", "hello123world456"))  # ['123', '456']
print(math.sqrt(16))  # 4.0
print(datetime.datetime.now())  # 输出当前时间
```

------

### **4. 字典如何删除键和合并两个字典**

**核心回答：**

- 删除键：使用 `del` 或 `pop()` 方法。
- 合并字典：使用 `update()` 方法或 `|`（Python 3.9+）。

**代码示例：**

```python
# 删除键
my_dict = {"a": 1, "b": 2, "c": 3}
del my_dict["b"]
print(my_dict)  # {'a': 1, 'c': 3}

# 合并字典
dict1 = {"x": 10, "y": 20}
dict2 = {"y": 30, "z": 40}

dict1.update(dict2)  # 使用 update() 合并
print(dict1)  # {'x': 10, 'y': 30, 'z': 40}

# Python 3.9+ 新写法
dict3 = dict1 | dict2
print(dict3)  # {'x': 10, 'y': 30, 'z': 40}
```

------

### **5. 谈谈 Python 的 GIL（全局解释器锁）**

**核心回答：**

- **GIL（Global Interpreter Lock）** 是 Python 解释器中的一个机制，保证同一时间只有一个线程在执行 Python 字节码，即使在多线程环境下。
- **影响：** 在 CPU 密集型任务中，多线程无法真正并行执行，建议使用 **多进程（multiprocessing）** 代替。
- **适用于：** I/O 密集型任务，如网络请求、文件读写。

**代码示例：**

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

**注意**：由于 GIL 的存在，这里的两个线程不会真正并行运行，而是交替执行。

------

### **6. Python 实现列表去重**

**核心回答：**

- 可以使用 **集合（set）** 去重，因为集合不允许重复元素。
- 也可以使用 **`dict.fromkeys()`** 方法。

**代码示例：**

```python
# 使用集合去重（会打乱顺序）
lst = [1, 2, 2, 3, 4, 4, 5]
unique_list = list(set(lst))
print(unique_list)  # 输出 [1, 2, 3, 4, 5]（顺序可能变化）

# 使用 `dict.fromkeys()` 保持顺序
unique_list = list(dict.fromkeys(lst))
print(unique_list)  # 输出 [1, 2, 3, 4, 5]
```

------

### **7. `\*args` 和 `\**kwargs` 的作用**

**核心回答：**

- `*args` 允许传递 **多个位置参数**，在函数内以 **元组** 形式接收。
- `**kwargs` 允许传递 **多个关键字参数**，在函数内以 **字典** 形式接收。

**代码示例：**

```python
def demo_function(*args, **kwargs):
    print("args:", args)
    print("kwargs:", kwargs)

demo_function(1, 2, 3, name="Alice", age=25)
# args: (1, 2, 3)
# kwargs: {'name': 'Alice', 'age': 25}
```

------

### **8. Python 2 和 Python 3 的 `range(100)` 区别**

**核心回答：**

- Python 2：`range(100)` 返回 **列表**，占用大量内存。
- Python 3：`range(100)` 返回 **迭代器**，节省内存。

**代码示例：**

```python
# Python 2:
# range(100) -> 返回 [0, 1, 2, ..., 99]（占用内存）
# xrange(100) -> 返回生成器（不会一次性创建所有元素）

# Python 3:
r = range(100)
print(type(r))  # <class 'range'> （迭代器）
print(list(r)[:5])  # [0, 1, 2, 3, 4]
```

------

### **9. 具备哪些特性，语言才能使用装饰器**

**核心回答：**

- **装饰器本质是一个函数，必须支持函数作为参数传递。**
- **Python 支持高阶函数**（函数可以作为参数传递给另一个函数）。

**代码示例：**

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
# 输出：
# Before function call
# Hello!
# After function call
```

------

### **10. Python 内建数据类型**

**核心回答：**

- **数值类型**：`int`, `float`, `complex`
- **布尔类型**：`bool`
- **序列类型**：`str`, `list`, `tuple`, `range`
- **集合类型**：`set`, `frozenset`
- **映射类型**：`dict`

**代码示例：**

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

------





