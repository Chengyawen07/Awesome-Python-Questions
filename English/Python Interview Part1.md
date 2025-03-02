### Python Interview Part1



#### **1. Four Basic Data Structures in Python**

- **List (`list`)**: Mutable, ordered, allows duplicates, supports indexing
- **Tuple (`tuple`)**: Immutable, ordered, allows duplicates
- **Set (`set`)**: Unordered, unique elements, supports set operations
- **Dictionary (`dict`)**: Key-value pairs, keys are unique

#### **2. Python Data Types**

- **Numeric**: `int`, `float`, `complex`
- **Sequence**: `list`, `tuple`, `range`, `str`
- **Set**: `set`, `frozenset`
- **Mapping**: `dict`
- **Boolean**: `bool`
- **NoneType**: `None`

#### **3. Difference Between `break` and `continue`**

- `break`: Exits the loop entirely
- `continue`: Skips the current iteration and continues

#### **4. Difference Between `return` and `yield`**

- `return`: Exits function and returns a value
- `yield`: Returns a value but pauses execution (used in generators)

#### **5. Deep Copy vs. Shallow Copy**

- **Shallow Copy (`copy.copy`)**: Copies references, changes in mutable objects affect both copies
- **Deep Copy (`copy.deepcopy`)**: Creates a separate copy, changes do not affect the original

#### **6. `range` vs `xrange`**

- In **Python 2**: `xrange` returns a generator (memory efficient), `range` returns a list
- In **Python 3**: `xrange` is removed, `range` behaves like `xrange`

#### **7. Difference Between `.is` and `==`**

- `is`: Checks **object identity** (same memory address)
- `==`: Checks **value equality**

#### **8. Lambda Functions**

- Anonymous function: 

  ```
  lambda x: x + 1
  ```

   is equivalent to:

  ```python
  def func(x):
      return x + 1
  ```

#### **9. String Splitting Methods**

- `.split()` - Splits string into a list
- `.partition()` - Returns a tuple of (before, delimiter, after)
- `re.split()` - Uses regex for splitting

#### **10. Single Quotes, Double Quotes, Triple Quotes**

- **Single & Double Quotes**: Equivalent for short strings
- **Triple Quotes**: Used for multi-line strings

#### **11. Python Function Argument Passing**

- **Pass-by-object-reference**: Mutable objects (`list`, `dict`) can be modified inside a function

#### **12. Decorators**

- Modify function behavior without changing its code

- Example:

  ```python
  def decorator(func):
      def wrapper():
          print("Before")
          func()
          print("After")
      return wrapper
  ```

#### **13. Variable Scope (LEGB Rule)**

- **Local** → **Enclosing** → **Global** → **Built-in**

#### **14. Interpreted vs. Compiled Languages**

- **Interpreted**: Executes line-by-line (Python, JavaScript)
- **Compiled**: Translates to machine code before execution (C, C++)

#### **15. `__init__` vs `__new__`**

- `__new__`: Creates a new instance
- `__init__`: Initializes the instance

#### **16. Commonly Used Modules**

- `os` (System operations)
- `sys` (Command-line args)
- `re` (Regex)
- `math` (Math functions)
- `random` (Random numbers)
- `datetime` (Date/time handling)
- `collections` (Advanced data structures)
- `json` (JSON parsing)

#### **17. `list` vs `numpy.array`**

- `list`: General-purpose, stores any data type
- `numpy.array`: Optimized for numerical operations, supports vectorized calculations

#### **18. `self` in Class Methods**

- Represents instance of a class
- Used to:
  - Access instance attributes: `self.var`
  - Call instance methods: `self.method()`
  - Pass to `super()` for parent class methods

#### **19. Variable Scope in Python**

- **Local**: Defined inside a function
- **Nonlocal**: Defined in an enclosing function
- **Global**: Defined at module level
- **Built-in**: Predefined in Python

#### **20. Object-Oriented Programming (OOP) in Python**

- **Encapsulation**: Hiding data, exposing necessary interfaces
- **Inheritance**: Child class inherits parent class methods and attributes
- **Polymorphism**: Same method name, different implementations

