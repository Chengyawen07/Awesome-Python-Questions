# Python 高频面试题 Part1 

1. Python基本数据结构有哪四种？区别是什么
2. Pyhton数据类型
3. Break和Continuous区别
4. Python return和yield的区别，以及return的作用
5. Python深拷贝和浅拷贝区别
6. range和xrange的区别
7. .is和==的区别
8. 什么是lambda函数
9. 字符串拆分方法有哪些
10. 单引号、双引号、三引号区别
11. python传参时需要注意什么
12. 装饰器是什么
13. 函数或变量的作用域
14. 解释型和编译型语言的区别
15. inti和new的区别
16. 常用的模块
17. python的list和numpy.array（数组）的区别
18. 类中self的概念及其三种应用
19. python的几种变量，按照作用域划分
20. python的面向对象特征



### **Python 高频面试问题答案：**

------

### **1. Python 基本数据结构有哪四种？区别是什么**

Python 主要有四种数据结构：

- **列表（list）**：可变、支持索引和切片、允许重复元素。
- **元组（tuple）**：不可变、支持索引和切片、允许重复元素，访问速度比列表快。
- **集合（set）**：无序、元素唯一，支持集合运算（交集、并集、差集）。
- **字典（dict）**：键值对存储，键唯一，访问速度快。

```python
my_list = [1, 2, 3, 4]
my_tuple = (1, 2, 3, 4)
my_set = {1, 2, 3, 3}  # {1, 2, 3}（去重）
my_dict = {"name": "Alice", "age": 25}
```

------

### **2. Python 数据类型**

- **数值类型**：`int`, `float`, `complex`
- **序列类型**：`list`, `tuple`, `range`, `str`
- **集合类型**：`set`, `frozenset`
- **映射类型**：`dict`
- **布尔类型**：`bool`
- **None 类型**：`NoneType`

```python
a = 10         # int
b = 3.14       # float
c = 3 + 4j     # complex
d = [1, 2, 3]  # list
e = (1, 2, 3)  # tuple
f = {1, 2, 3}  # set
g = {"key": "value"}  # dict
h = True       # bool
i = None       # NoneType
```

------

### **3. `break` 和 `continue` 的区别**

- `break` 直接退出整个循环。
- `continue` 跳过当前迭代，继续下一次循环。

```python
for i in range(5):
    if i == 3:
        break
    print(i)  # 输出 0 1 2

for i in range(5):
    if i == 3:
        continue
    print(i)  # 输出 0 1 2 4
```

------

### **4. `return` 和 `yield` 的区别**

- `return` 返回值并终止函数执行。
- `yield` 生成一个生成器，不会终止函数。

```python
def func():
    return 10

def generator():
    for i in range(3):
        yield i  # 生成器

print(func())  # 10
gen = generator()
print(next(gen))  # 0
print(next(gen))  # 1
print(next(gen))  # 2
```

------

### **5. 深拷贝和浅拷贝**

- **浅拷贝（copy.copy）**：仅拷贝对象的引用，修改可变对象会影响原对象。
- **深拷贝（copy.deepcopy）**：创建独立副本，修改不会影响原对象。

```python
import copy

list1 = [[1, 2], [3, 4]]
shallow_copy = copy.copy(list1)
deep_copy = copy.deepcopy(list1)

shallow_copy[0][0] = 100
print(list1)  # [[100, 2], [3, 4]]（浅拷贝受影响）
print(deep_copy)  # [[1, 2], [3, 4]]（深拷贝不受影响）
```

------

### **6. `range` 和 `xrange` 的区别**

- **Python 2**：`xrange()` 返回生成器（省内存），`range()` 返回列表。
- **Python 3**：`xrange()` 被移除，`range()` 变为生成器。

```python
for i in range(3):
    print(i)  # 0 1 2
```

------

### **7. `.is` 和 `==` 的区别**

- `is` 比较对象的 **内存地址**。
- `==` 比较对象的 **值**。

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)  # True
print(a == c)  # True
print(a is c)  # False
```

------

### **8. Lambda 函数**

匿名函数，简化代码。

```python
square = lambda x: x * x
print(square(5))  # 25
```

------

### **9. 字符串拆分方法**

- `.split()` 按指定字符拆分
- `.partition()` 返回三元组
- `re.split()` 使用正则拆分

```python
s = "apple,banana,orange"
print(s.split(","))  # ['apple', 'banana', 'orange']
```

------

### **10. 单引号、双引号、三引号的区别**

- **单引号、双引号**：等价，适合短字符串。
- **三引号**：用于多行字符串。

```python
s1 = 'Hello'
s2 = "World"
s3 = '''This is
a multi-line
string.'''
```

------

### **11. Python 传参注意事项**

- Python 采用 **“传对象引用”**（Mutable 可变对象会被修改）。

```python
def modify_list(lst):
    lst.append(4)

my_list = [1, 2, 3]
modify_list(my_list)
print(my_list)  # [1, 2, 3, 4]
```

------

### **12. 装饰器**

装饰器用于 **修改函数行为**，不改变函数代码。

```python
def decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper
```

------

### **13. 变量作用域（LEGB）**

- **Local**（局部作用域）
- **Enclosing**（闭包作用域）
- **Global**（全局作用域）
- **Built-in**（内建作用域）

```python
x = 10  # 全局变量
def outer():
    y = 20  # 闭包变量
    def inner():
        z = 30  # 局部变量
        print(x, y, z)
    inner()

outer()  # 10 20 30
```

------

### **14. 解释型和编译型语言的区别**

- **解释型**：逐行执行（Python、JavaScript）。
- **编译型**：编译后执行（C、C++）。

------

### **15. `__init__` vs `__new__`**

- `__new__` 创建实例，`__init__` 初始化实例。

```python
class A:
    def __new__(cls):
        print("Creating instance")
        return super().__new__(cls)

    def __init__(self):
        print("Initializing instance")

a = A()
```

------

### **16. 常用模块**

- `os`（系统操作）
- `sys`（命令行参数）
- `re`（正则表达式）
- `math`（数学运算）
- `random`（随机数）
- `datetime`（时间处理）

------

### **17. `list` vs `numpy.array`**

- `list` 适用于存储各种数据类型。
- `numpy.array` 适用于数值计算。

------

### **18. `self` 在类中的应用**

- 访问实例变量
- 调用实例方法
- 传递给 `super()`

------

### **19. 按作用域划分的变量**

- 局部变量（Local）
- 闭包变量（Enclosing）
- 全局变量（Global）
- 内建变量（Built-in）

------

### **20. Python 面向对象特性**

- **封装**
- **继承**
- **多态**



