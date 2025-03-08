# Python 高频面试题 Part4

### **21. Python 中的可变数据类型和不可变数据类型**

**核心回答：**

- 不可变类型int， float, str, tuple
  - 不允许变量值发生变化，修改变量会生成新的对象，内存地址改变。
- 可变类型 list, dict, set
  - 变量值可以修改，修改后内存地址保持不变。

**示例代码：**

```python
# 不可变类型
a = "hello"
print(id(a))  # 查看内存地址
a += " world"
print(id(a))  # 地址发生变化

# 可变类型
b = [1, 2, 3]
print(id(b))  # 初始地址
b.append(4)
print(id(b))  # 地址不变，列表被修改
```

------

### **22. 去重并对字符串排序**

- s = "ajldjlajfdljfddd"，去重并从小到大排序输出"adfjl"

**核心回答：**

- set(s) 去重字符串 s 中的字符。
- sorted(set(s)) 对去重后的字符按字母顺序排序，得到一个列表。
- "".join(sorted(set(s))) 将排序后的字符列表拼接成一个字符串。

**示例代码：**

```python
chars = ['a', 'd', 'f', 'j', 'l']
result = "".join(chars)
print(result)  # 输出: "adfjl"

# 答案代码：
s = "ajldjlajfdljfddd"
unique_sorted = "".join(sorted(set(s)))
print(unique_sorted)  # 输出: "adfjl"
```

------

### **23. 使用 `lambda` 函数实现两个数相乘**

**核心回答：**

- `lambda` 函数用于创建匿名函数，适用于简单运算。

**示例代码：**

```python
multiply = lambda x, y: x * y
print(multiply(3, 4))  # 输出: 12
```

------

### **24. 按key从小到大排序字典**

**核心回答：**

- 使用 `sorted()` 对 `dict.items()` 进行排序。

**示例代码：**

```python
dic = {"name": "zs", "age": 18, "city": "深圳", "tel": "1362626627"}
sorted_dict = dict(sorted(dic.items()))
print(sorted_dict)
# 输出: {'age': 18, 'city': '深圳', 'name': 'zs', 'tel': '1362626627'}
```

------

### **25. 使用 `collections.Counter` 统计字符串中字母出现次数**

- 利用collections库的Counter方法统计字符串每个单词出现的次数"kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h"

**核心回答：**

- **`Counter()` 可以统计字符串中每个字符出现的次数。**

**示例代码：**

```python
from collections import Counter

s = "kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h"
word_count = Counter(s)
print(word_count)
```

------

### **26. 过滤掉字符串中的英文和数字**

- 字符串a = "not 404 found 张三 99 深圳"，每个词中间是空格，用正则过滤掉英文和数字，最终输出"张三  深圳"

**核心回答：**

- 使用 `re.sub()` 替换匹配到的英文和数字。
- 这个代码的作用是去掉字符串中的英文和数字，只保留非英文和非数字的字符。
- re.sub(pattern, replacement, string) 用于替换字符串中符合 pattern 的部分。
- **r'[a-zA-Z0-9]' 是正则表达式**，匹配所有英文字母（大写、小写）和数字
- **Strip() 用于去掉字符串前后的空格，**避免因为删除内容后出现多余的空格。

**示例代码：**

```python
import re

a = "not 404 found 张三 99 深圳"
filtered_text = re.sub(r'[a-zA-Z0-9]', '', a).strip()
print(filtered_text)  # 输出: "张三  深圳"
```

------

### **27. 使用 `filter()` 筛选列表中的奇数**

**核心回答：**

- `filter()` 用于筛选符合条件的元素。
  - filter(function, iterable)
  - filter() 只保留 function(x) 结果为 True 的元素。

- **`list(filter(...))`**
  - `filter()` 结果是**一个过滤后的迭代器**，需要用 `list()` 转换成列表

**示例代码：**

```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
odd_numbers = list(filter(lambda x: x % 2 != 0, a))
print(odd_numbers)  # 输出: [1, 3, 5, 7, 9]
```

------

### **28. 使用列表推导式筛选列表中的奇数**

- 列表推导式求列表所有奇数并构造新列表，a =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

**核心回答：**

- 使用 **列表推导式** 语法快速生成新列表。
- 列表推导式是一种**简洁的方式**来创建新列表，结构如下：
  - new_list = [表达式 for 变量 in 可迭代对象 if 条件]


**示例代码：**

```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
odd_numbers = [x for x in a if x % 2 != 0]
print(odd_numbers)  # 输出: [1, 3, 5, 7, 9]
```

------

### **29. 正则 `re.compile()` 的作用**

**核心回答：**

- **<u>`re.compile()` 将正则表达式编译为 模式对象，提高匹配效率。</u>**

- 正则表达式（Regular Expression，简称正则或Regex）是一种用于匹配字符串的模式，它可以用来查找、替换、分割、提取特定内容

- 简单示例：

  ```Python 
  # 目标：找到字符串中的所有数字
  
  import re
  
  text = "今天是2025年1月30日，气温是5度"
  result = re.findall(r'\d+', text)
  
  print(result)  # 输出: ['2025', '1', '30', '5']
  
  ```

  

**`re.compile()` 结合正则表达式 示例代码：**

- 为什么要 compile()？ 如果同一个正则要多次使用，re.compile() 只解析一次，后面直接调用，比 re.findall() 直接写字符串更快。

```python
import re

# 编译正则表达式，匹配所有数字
pattern = re.compile(r'\d+')

# 在不同的字符串中查找数字
print(pattern.findall("我有 3 个苹果和 12 个橙子"))  # 输出: ['3', '12']
print(pattern.findall("2024年1月30日"))  # 输出: ['2024', '1', '30']

```

### **总结**

- **正则表达式** 是用来**查找、匹配、替换、验证字符串**的工具。
- <u>**常见符号** 例如 `\d` (数字)、`\w` (字母+数字+下划线)、`^` (开头匹配)、`$` (结尾匹配)。</u>
- **`re.compile()`** 预编译正则，提高执行效率，适合**多次匹配**的情况。

### **PS: 正则表达式的常见符号**

| 符号 | 作用                           | 示例                                       |
| ---- | ------------------------------ | ------------------------------------------ |
| `.`  | 匹配任意字符（除换行符）       | `"a.c"` 可匹配 `"abc"`，`"a1c"`            |
| `\d` | 匹配**数字**（0-9）            | `"\d+"` 可匹配 `"123"`                     |
| `\w` | 匹配**字母、数字、下划线**     | `"\w+"` 可匹配 `"hello_123"`               |
| `\s` | 匹配**空格、换行符、制表符**   | `"\s+"` 可匹配 `" "`                       |
| `+`  | 匹配**前面的字符 1 次或多次**  | `"\d+"` 匹配 `"12345"`                     |
| `*`  | 匹配**前面的字符 0 次或多次**  | `"a*"` 可匹配 `""`、`"a"`、`"aaa"`         |
| `?`  | 匹配**前面的字符 0 次或 1 次** | `"colou?r"` 可匹配 `"color"` 和 `"colour"` |
| `^`  | **匹配字符串开头**             | `"^hello"` 只匹配以 `"hello"` 开头的字符串 |
| `$`  | **匹配字符串结尾**             | `"world$"` 只匹配以 `"world"` 结尾的字符串 |



### **30. `a = (1,)`, `b = (1)`, `c = ("1")` 分别是什么类型？**

**核心回答：**

- `a = (1,)` → **元组（tuple）**（逗号使其成为元组）。
- `b = (1)` → **整数（int）**（括号不会自动创建元组）。
- `c = ("1")` → **字符串（str）**（只有一个元素时，仍是字符串）。

**示例代码：**

```python
a = (1,)
b = (1)
c = ("1")

print(type(a))  # 输出: <class 'tuple'>
print(type(b))  # 输出: <class 'int'>
print(type(c))  # 输出: <class 'str'>
```

