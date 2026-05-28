# 🐍 PYTHON COMPLETE INTERVIEW MASTER GUIDE
### From BASIC → ADVANCED → EXPERT | TCS + Senior + Product-Based Companies

> **How to use this guide:** Read top to bottom for beginners. Jump to any section for revision. Every topic has: Definition → Why → Example → Interview Q&A → Memory Trick.

---

# ═══════════════════════════════════════════════
# PART 1 — PYTHON BASICS
# ═══════════════════════════════════════════════

---

## 1.1 What is Python?

**Simple Definition:**
Python is a programming language. Like English is a language to talk to humans, Python is a language to talk to computers. You write instructions in Python, and the computer follows them.

**Why Python?**
- Easy to read (like plain English)
- Less code needed (10 lines of Java = 3 lines of Python)
- Huge community, free libraries for everything

**Real-World Use:**
- Google uses Python for search backend
- Instagram backend is Django (Python)
- Netflix uses Python for recommendations
- NASA uses Python for data analysis

**Memory Trick:** Python = "Powerful Yet Simple Language Helping Ordinary Needy developers"

---

## 1.2 Features of Python

| Feature | Explanation | Example |
|---|---|---|
| Interpreted | Runs line by line, no need to compile fully first | Like reading a recipe step by step |
| Dynamically Typed | No need to declare variable type | `x = 5` then `x = "hello"` — both valid |
| Object-Oriented | Everything is an object | Even numbers are objects |
| Open Source | Free to use | Download and use freely |
| Portable | Runs on Windows, Mac, Linux | Write once, run anywhere |
| Extensive Libraries | Numpy, Pandas, Django, Flask | Like a huge toolbox |
| Indentation-based | Uses spaces, not `{}` | Forces clean code |

---

## 1.3 Compiled vs Interpreted

**Think of it like this:**
- **Compiled language (C, C++):** Like translating an entire book from Hindi to English FIRST, then reading it. Fast to read after translation.
- **Interpreted language (Python):** Like having a translator read the Hindi book LINE BY LINE to you in real time. Slower but more flexible.

**Python is Interpreted** — runs code line by line.

**But wait — Python actually does BOTH internally:**
1. Python first **compiles** your `.py` file to **bytecode** (`.pyc` file)
2. Then the **Python Virtual Machine (PVM)** interprets that bytecode

```
Your Code (.py)
     ↓
  Compiler
     ↓
Bytecode (.pyc)
     ↓
   PVM (Python Virtual Machine)
     ↓
  Output
```

**Interview Q:** Is Python compiled or interpreted?
**Best Answer:** "Python is primarily interpreted, but it goes through a compilation step first — source code is compiled to bytecode (.pyc), which is then interpreted by the PVM. So technically both!"

---

## 1.4 Variables

**Simple Definition:** A variable is like a box with a name. You put a value in the box. Whenever you need that value, you use the box name.

```python
name = "Alice"      # box called 'name' holds "Alice"
age = 25            # box called 'age' holds 25
salary = 50000.50   # box called 'salary' holds 50000.50
```

**Python Variable Rules:**
- Can start with letter or underscore `_`
- Cannot start with number
- Case sensitive: `Name` ≠ `name`
- Cannot use keywords: `if`, `for`, `class`, etc.

**Dynamic Typing:**
```python
x = 10        # x is int
x = "hello"   # x is now string — Python allows this!
x = [1,2,3]   # x is now list — still valid!
```

**Interview Q:** What is dynamic typing?
**Answer:** Python automatically decides the variable type based on the value. You don't need to write `int x = 5` like Java. Just write `x = 5`.

---

## 1.5 Data Types Overview

```python
# Numbers
x = 10          # int
y = 3.14        # float
z = 3 + 4j      # complex

# Text
name = "Alice"  # str

# Collections
my_list = [1, 2, 3]           # list
my_tuple = (1, 2, 3)          # tuple
my_dict = {"key": "value"}    # dict
my_set = {1, 2, 3}            # set

# Boolean
flag = True    # bool

# None
data = None    # NoneType
```

---

## 1.6 Operators

| Operator Type | Symbols | Example |
|---|---|---|
| Arithmetic | `+ - * / // % **` | `10 // 3 = 3`, `2**3 = 8` |
| Comparison | `== != > < >= <=` | `5 > 3 → True` |
| Logical | `and or not` | `True and False → False` |
| Assignment | `= += -= *= /=` | `x += 5` |
| Identity | `is is not` | `a is b` |
| Membership | `in not in` | `3 in [1,2,3]` |
| Bitwise | `& | ^ ~ << >>` | `5 & 3 = 1` |

**Important `//` vs `/`:**
```python
10 / 3   # = 3.333... (float division)
10 // 3  # = 3 (integer/floor division)
```

**`is` vs `==`:**
```python
a = [1, 2, 3]
b = [1, 2, 3]
a == b   # True  — same VALUE
a is b   # False — different OBJECTS in memory

c = a
a is c   # True  — same object!
```

**Memory Trick:** `is` = identity (same object), `==` = equality (same value)

---

## 1.7 Input / Output

```python
# Output
print("Hello, World!")
print(f"Name: {name}, Age: {age}")    # f-string (modern, fast)
print("Name: %s, Age: %d" % (name, age))  # old style

# Input
name = input("Enter your name: ")     # always returns STRING
age = int(input("Enter age: "))       # convert to int manually
```

---

## 1.8 Type Casting

```python
int("42")       # → 42
float("3.14")   # → 3.14
str(100)        # → "100"
list((1,2,3))   # → [1, 2, 3]
tuple([1,2,3])  # → (1, 2, 3)
bool(0)         # → False
bool(1)         # → True
bool("")        # → False
bool("hello")   # → True
```

**Falsy values in Python:** `0`, `0.0`, `""`, `[]`, `{}`, `()`, `None`, `False`
**Everything else is Truthy.**

---

## 1.9 Keywords & Identifiers

**Keywords:** Reserved words Python uses. You cannot use them as variable names.
```
False  True  None  and  or  not  if  elif  else
for  while  break  continue  return  def  class
import  from  try  except  finally  raise  with
lambda  yield  global  nonlocal  pass  del  is  in
```

**Identifiers:** Names you give to variables, functions, classes.
```python
# Valid identifiers
my_variable = 10
_private = 20
MyClass = object

# Invalid identifiers
2name = 10      # starts with number — ERROR
my-var = 10     # hyphen not allowed — ERROR
class = "hi"    # keyword — ERROR
```

---

## 1.10 Comments & Indentation

```python
# This is a single-line comment

"""
This is a
multi-line comment (actually a docstring)
"""

def my_function():
    if True:            # 4 spaces indent
        print("hello")  # 8 spaces indent
```

**Why Indentation matters:** Python uses indentation INSTEAD of `{}`. Wrong indentation = error.

```python
# WRONG:
def greet():
print("hello")  # IndentationError!

# RIGHT:
def greet():
    print("hello")  # 4 spaces
```

---

# ═══════════════════════════════════════════════
# PART 2 — PYTHON DATA TYPES (DEEP DIVE)
# ═══════════════════════════════════════════════

---

## 2.1 LIST

**Simple Definition:** A list is like a shopping bag. You can put anything inside — numbers, strings, other lists. You can add, remove, and change items.

**Key Properties:**
- Ordered (items keep their position)
- Mutable (can change after creation)
- Allows duplicates
- Syntax: `[  ]`

```python
fruits = ["apple", "banana", "cherry"]
fruits[0]         # "apple" — indexing
fruits[-1]        # "cherry" — negative index
fruits[0:2]       # ["apple", "banana"] — slicing

fruits.append("mango")       # add to end
fruits.insert(1, "grape")    # insert at position 1
fruits.remove("banana")      # remove by value
fruits.pop()                 # remove last
fruits.pop(0)                # remove at index 0
len(fruits)                  # length
fruits.sort()                # sort in place
fruits.reverse()             # reverse in place
sorted(fruits)               # returns new sorted list
fruits.count("apple")        # count occurrences
fruits.index("cherry")       # find index
fruits.extend([1, 2, 3])     # add multiple items
```

**Time Complexity:**
| Operation | Time |
|---|---|
| Access by index | O(1) |
| Append | O(1) amortized |
| Insert at beginning | O(n) |
| Search (in) | O(n) |
| Delete by value | O(n) |

**Real-World:** Shopping cart items, list of employees, query results from database.

---

## 2.2 TUPLE

**Simple Definition:** A tuple is like a list but LOCKED. Once you create it, you cannot change it. Like a birth certificate — your birth date is fixed forever.

**Key Properties:**
- Ordered
- Immutable (cannot change after creation)
- Allows duplicates
- Syntax: `(  )`
- Faster than list

```python
coordinates = (10, 20)
point = (3, 4, 5)

point[0]         # 3 — can read
# point[0] = 5  # ERROR — cannot modify!

# Unpacking
x, y, z = point
print(x, y, z)   # 3 4 5

# Single element tuple needs comma!
single = (5,)    # tuple
not_tuple = (5)  # just int!
```

**Why is Tuple faster than List?**
- Tuples are stored in a single memory block
- Lists need extra memory for potential growth
- Python can optimize tuple operations at interpreter level

**Real-World:** GPS coordinates, RGB color values `(255, 0, 0)`, database rows returned from query, function returning multiple values.

---

## 2.3 DICTIONARY

**Simple Definition:** A dictionary is like a real dictionary. Every word (key) has a meaning (value). You look up by the word, not by page number.

**Key Properties:**
- Key-Value pairs
- Keys must be unique and immutable (string, int, tuple)
- Values can be anything
- Ordered (Python 3.7+)
- Mutable
- Syntax: `{key: value}`

```python
person = {"name": "Alice", "age": 25, "city": "Mumbai"}

person["name"]            # "Alice"
person.get("salary", 0)   # 0 — safe access with default
person["age"] = 30        # update
person["salary"] = 50000  # add new key
del person["city"]        # delete key
"name" in person          # True — check key exists

person.keys()    # dict_keys(['name', 'age', 'salary'])
person.values()  # dict_values(['Alice', 30, 50000])
person.items()   # dict_items([('name','Alice'), ...])

# Iterating
for key, value in person.items():
    print(f"{key}: {value}")
```

**How Dictionary Works Internally (Hashing):**
1. You give a key: `"name"`
2. Python runs a hash function: `hash("name")` → some number like `12345`
3. That number maps to a memory location
4. Value stored at that location
5. To retrieve: hash the key again → go to same location → get value
6. This is why lookup is O(1)!

**Memory Trick:** Dictionary = Hash Map = O(1) lookup magic!

---

## 2.4 SET

**Simple Definition:** A set is like a bag where DUPLICATES are NOT allowed. Every item is unique. Like a guest list — same person can't be listed twice.

**Key Properties:**
- Unordered (no index)
- No duplicates
- Mutable
- Fast membership testing O(1)
- Syntax: `{  }` — but empty set = `set()`, not `{}`!

```python
nums = {1, 2, 3, 3, 2, 1}
print(nums)    # {1, 2, 3} — duplicates removed!

nums.add(4)
nums.remove(2)
nums.discard(99)  # no error if not found (remove() would error)

# Set operations
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}
a | b     # union: {1,2,3,4,5,6}
a & b     # intersection: {3,4}
a - b     # difference: {1,2}
a ^ b     # symmetric difference: {1,2,5,6}

# Fast lookup
3 in a    # O(1) — much faster than list!
```

**Why Set is Fast:** Sets use hashing internally (like dict). No need to scan every element.

**Real-World:** Removing duplicates from data, finding common users between two groups, spam email filtering.

---

## 2.5 FROZENSET

**Simple Definition:** A frozenset is a SET that is LOCKED (immutable). Like a set engraved in stone.

```python
fs = frozenset([1, 2, 3, 3, 2])
print(fs)       # frozenset({1, 2, 3})
# fs.add(4)     # ERROR — immutable!

# Can be used as dictionary KEY (regular set cannot)
d = {frozenset({1,2}): "pair"}
```

**Real-World:** Use as dictionary keys when you need a set as key.

---

## 2.6 STRING

**Simple Definition:** A string is a sequence of characters. Text. Like a chain of letters.

**Key Properties:**
- Immutable
- Ordered
- Supports indexing and slicing

```python
s = "Hello, World!"
s[0]          # "H"
s[-1]         # "!"
s[0:5]        # "Hello"
s[::-1]       # "!dlroW ,olleH" — reverse

# String methods
s.upper()         # "HELLO, WORLD!"
s.lower()         # "hello, world!"
s.strip()         # remove whitespace from ends
s.split(",")      # ["Hello", " World!"]
s.replace("Hello","Hi")  # "Hi, World!"
s.find("World")   # 7 — index of substring
s.startswith("Hello")    # True
s.endswith("!")          # True
",".join(["a","b","c"])  # "a,b,c"
f"Name: {'Alice'}"       # f-string formatting
```

**String is Immutable:**
```python
s = "hello"
# s[0] = "H"  # ERROR!
s = "H" + s[1:]   # Must create new string
```

---

## 2.7 BIG COMPARISON TABLES

### List vs Tuple
| Feature | List | Tuple |
|---|---|---|
| Syntax | `[1, 2, 3]` | `(1, 2, 3)` |
| Mutable | YES | NO |
| Speed | Slower | Faster |
| Memory | More | Less |
| Use as dict key | NO | YES |
| Use case | Data that changes | Fixed data |

### Set vs Frozenset
| Feature | Set | Frozenset |
|---|---|---|
| Mutable | YES | NO |
| Dict key | NO | YES |
| Hashable | NO | YES |

### List vs Set
| Feature | List | Set |
|---|---|---|
| Duplicates | Allowed | NOT allowed |
| Ordered | YES | NO |
| Lookup speed | O(n) | O(1) |
| Use case | Sequence data | Unique items |

### Mutable vs Immutable
| Mutable | Immutable |
|---|---|
| list | tuple |
| dict | str |
| set | int, float, bool |
| bytearray | frozenset, bytes |

---

## 2.8 Important Interview Questions — Data Types

**Q1: What is the difference between `list` and `tuple`?**
> List is mutable (can change), tuple is immutable (cannot change). Tuple is faster and uses less memory. Use tuple for fixed data like coordinates. Use list for data that changes.

**Q2: Can a list be used as a dictionary key?**
> No. Dictionary keys must be hashable. Lists are mutable and not hashable. Use tuple instead.

**Q3: How does a set remove duplicates?**
> Set uses hashing. When you add an element, Python computes its hash. If hash already exists, element is not added. That's how duplicates are removed.

**Q4: What is the difference between `remove()` and `discard()` in set?**
> Both remove an element. But `remove()` throws `KeyError` if element not found. `discard()` does nothing — no error.

**Q5: How is `{}` different from `set()`?**
> `{}` creates an empty DICTIONARY. `set()` creates an empty SET. This is a common trap!

**Q6: Why is dictionary lookup O(1)?**
> Dictionary uses a hash table internally. Key is hashed to get a memory address directly. No need to search through all keys.

---

# ═══════════════════════════════════════════════
# PART 3 — OOPS IN PYTHON
# ═══════════════════════════════════════════════

---

## 3.1 Why OOPs?

**Problem without OOPs:**
Imagine building a bank system. Without OOPs, all code is scattered — functions everywhere, data everywhere, no structure.

**With OOPs:**
You create a `BankAccount` class. It has data (balance) and actions (deposit, withdraw). Everything organized in one place.

**4 Pillars of OOPs:**
1. **Encapsulation** — Data hiding (keep internals private)
2. **Inheritance** — Reuse code from parent class
3. **Polymorphism** — Same method name, different behavior
4. **Abstraction** — Show only what is necessary, hide complexity

---

## 3.2 Class & Object

**Class = Blueprint.** Like a house blueprint.
**Object = Actual house** built from that blueprint.

```python
class Dog:
    # Class variable — shared by ALL dogs
    species = "Canine"

    def __init__(self, name, age):    # Constructor
        # Instance variables — unique to EACH dog
        self.name = name
        self.age = age

    def bark(self):
        print(f"{self.name} says Woof!")

# Creating objects
dog1 = Dog("Tommy", 3)
dog2 = Dog("Bruno", 5)

dog1.bark()         # Tommy says Woof!
dog2.bark()         # Bruno says Woof!
print(Dog.species)  # Canine
```

---

## 3.3 `self` — What is it?

**`self` = reference to the current object.**
When you call `dog1.bark()`, Python secretly passes `dog1` as the first argument. `self` is that argument.

```python
dog1.bark()
# Python actually does:
Dog.bark(dog1)
# self = dog1
```

**Interview Q:** Can we use a name other than `self`?
**Answer:** Yes! `self` is just a convention. You can write `def bark(this):` and it works. But ALWAYS use `self` — it's the standard.

---

## 3.4 Constructor (`__init__`)

**`__init__` is called automatically when you create an object.**

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
        print(f"Car created: {brand} {model}")

c = Car("Toyota", "Camry")  # prints: Car created: Toyota Camry
```

---

## 3.5 Inheritance

**Simple Definition:** Child class gets all features of Parent class for FREE. Like how you inherit traits from your parents.

```python
class Animal:       # Parent class
    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f"{self.name} is eating")

class Dog(Animal):  # Child class inherits from Animal
    def bark(self):
        print(f"{self.name} says Woof!")

dog = Dog("Tommy")
dog.eat()    # Inherited from Animal — Tommy is eating
dog.bark()   # Dog's own method — Tommy says Woof!
```

**Types of Inheritance:**
```python
# 1. Single
class B(A): pass

# 2. Multiple
class C(A, B): pass

# 3. Multilevel
class B(A): pass
class C(B): pass     # C inherits from B, which inherits from A

# 4. Hierarchical
class B(A): pass
class C(A): pass     # Both B and C inherit from A

# 5. Hybrid
# Combination of above
```

---

## 3.6 MRO — Method Resolution Order

**Problem:** If multiple parent classes have the same method, which one does Python use?

**MRO = The order Python searches for a method.**

Python uses **C3 Linearization Algorithm.**

```python
class A:
    def hello(self): print("A")

class B(A):
    def hello(self): print("B")

class C(A):
    def hello(self): print("C")

class D(B, C): pass

d = D()
d.hello()       # Prints "B"
print(D.__mro__)  # (D, B, C, A, object)
# Search order: D → B → C → A → object
```

**Memory Trick:** MRO = "Most Right Order" → Left to Right, Depth first, then breadth.

---

## 3.7 `super()`

**`super()` calls the parent class method.**

```python
class Animal:
    def __init__(self, name):
        self.name = name

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)    # Call Animal's __init__
        self.breed = breed        # Dog's own init

dog = Dog("Tommy", "Labrador")
print(dog.name, dog.breed)   # Tommy Labrador
```

---

## 3.8 Encapsulation

**Simple Definition:** Wrap data inside a class and control who can access it. Like your ATM PIN — hidden, protected.

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance    # Private — double underscore

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

acc = BankAccount(1000)
acc.deposit(500)
print(acc.get_balance())   # 1500
# print(acc.__balance)     # ERROR! AttributeError
```

**Access Modifiers in Python:**
| Type | Syntax | Access |
|---|---|---|
| Public | `name` | Anywhere |
| Protected | `_name` | Class + Subclasses (convention only) |
| Private | `__name` | Class only (name mangling applied) |

**Note:** Python doesn't truly enforce private. `__balance` becomes `_BankAccount__balance` internally (name mangling). So `acc._BankAccount__balance` still works. Python trusts the developer.

---

## 3.9 Polymorphism

**Simple Definition:** Same method name, different behavior depending on the object. Like the word "run" — a human runs, a computer runs a program, a river runs — same word, different meaning.

```python
class Cat:
    def speak(self): print("Meow")

class Dog:
    def speak(self): print("Woof")

class Cow:
    def speak(self): print("Moo")

animals = [Cat(), Dog(), Cow()]
for animal in animals:
    animal.speak()   # Each behaves differently!
# Output: Meow, Woof, Moo
```

---

## 3.10 Method Overriding

**Child class redefines a method from the parent class.**

```python
class Shape:
    def area(self): return 0

class Circle(Shape):
    def __init__(self, r): self.r = r
    def area(self): return 3.14 * self.r * self.r   # Override!

class Square(Shape):
    def __init__(self, s): self.s = s
    def area(self): return self.s * self.s           # Override!
```

---

## 3.11 Method Overloading

**Python does NOT support true method overloading (same name, different params).**
Workaround using default arguments:

```python
class Calculator:
    def add(self, a, b=0, c=0):   # Default params = overloading workaround
        return a + b + c

calc = Calculator()
calc.add(5)        # 5
calc.add(5, 3)     # 8
calc.add(5, 3, 2)  # 10
```

---

## 3.12 Abstraction

**Simple Definition:** Show only WHAT something does, hide HOW it does it. Like a TV remote — you press a button, TV changes channel. You don't need to know the electronics inside.

```python
from abc import ABC, abstractmethod

class PaymentGateway(ABC):        # Abstract class
    @abstractmethod
    def pay(self, amount):        # Abstract method — no implementation
        pass

class PayPal(PaymentGateway):
    def pay(self, amount):
        print(f"Paying ${amount} via PayPal")

class Stripe(PaymentGateway):
    def pay(self, amount):
        print(f"Paying ${amount} via Stripe")

# gateway = PaymentGateway()     # ERROR! Cannot instantiate abstract class
p = PayPal()
p.pay(100)   # Paying $100 via PayPal
```

---

## 3.13 Instance, Class, and Static Methods

```python
class MyClass:
    class_var = "I am shared"

    def instance_method(self):        # Gets self (object)
        print(f"Instance: {self.class_var}")

    @classmethod
    def class_method(cls):            # Gets cls (class)
        print(f"Class: {cls.class_var}")

    @staticmethod
    def static_method():              # Gets nothing
        print("Static: no access to class or instance")

obj = MyClass()
obj.instance_method()    # needs object
MyClass.class_method()   # called on class
MyClass.static_method()  # called on class, no self/cls
```

| Method Type | Decorator | First Param | Access |
|---|---|---|---|
| Instance | None | `self` | instance + class |
| Class | `@classmethod` | `cls` | class only |
| Static | `@staticmethod` | None | neither |

**Use Case:**
- Instance method: `user.save()` — saves this specific user
- Class method: `User.get_user_count()` — counts all users (factory methods)
- Static method: `Utils.format_date()` — utility function, no state needed

---

## 3.14 Composition vs Aggregation

**Composition:** "Has-a" relationship where child CANNOT exist without parent.
```python
class Engine:           # Engine cannot exist without Car in composition
    def start(self): print("Engine started")

class Car:
    def __init__(self):
        self.engine = Engine()   # Car OWNS the engine — created inside
    def drive(self):
        self.engine.start()
```

**Aggregation:** "Has-a" but child CAN exist independently.
```python
class Teacher:
    def teach(self): print("Teaching")

class School:
    def __init__(self, teacher):
        self.teacher = teacher    # Teacher passed from OUTSIDE — can exist without school

teacher = Teacher()
school = School(teacher)   # Teacher exists independently
```

---

## 3.15 OOPs Interview Questions

**Q1: What are the 4 pillars of OOPs?**
> Encapsulation, Inheritance, Polymorphism, Abstraction.

**Q2: What is MRO and why is it important?**
> MRO (Method Resolution Order) defines the order Python searches for a method in multiple inheritance. Uses C3 linearization. Check with `ClassName.__mro__`.

**Q3: What is the difference between `@classmethod` and `@staticmethod`?**
> `@classmethod` receives `cls` (the class) as first argument — can access/modify class state. `@staticmethod` receives nothing — purely utility function, no access to class or instance.

**Q4: Can we instantiate an abstract class?**
> No. If a class has `@abstractmethod`, it cannot be instantiated. You must create a subclass that implements all abstract methods.

**Q5: What is name mangling?**
> Double underscore `__attr` causes Python to rename it to `_ClassName__attr`. This prevents accidental override in subclasses. It's not true private — you can still access it if you know the mangled name.

---

# ═══════════════════════════════════════════════
# PART 4 — ADVANCED PYTHON
# ═══════════════════════════════════════════════

---

## 4.1 Decorators

**Simple Definition:** A decorator is a function that WRAPS another function to add extra behavior WITHOUT changing the original function. Like putting a gift wrapper around a gift — the gift is the same, but now it looks better.

**Real World:** Logging, authentication check, timing, caching.

```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function runs")     # Extra behavior
        result = func(*args, **kwargs)    # Original function
        print("After function runs")      # Extra behavior
        return result
    return wrapper

@my_decorator         # Same as: greet = my_decorator(greet)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
# Output:
# Before function runs
# Hello, Alice!
# After function runs
```

**Real Example — Login Check:**
```python
def require_login(func):
    def wrapper(user, *args, **kwargs):
        if not user.is_logged_in:
            return "Please login first"
        return func(user, *args, **kwargs)
    return wrapper

@require_login
def view_dashboard(user):
    return "Welcome to dashboard!"
```

**Stacking Decorators:**
```python
@decorator1
@decorator2
def my_func(): pass
# Equivalent to: my_func = decorator1(decorator2(my_func))
# decorator2 is applied FIRST, then decorator1
```

---

## 4.2 Generators

**Simple Definition:** A generator is a function that produces values ONE AT A TIME, on demand. Like a water tap — water comes when you turn it on, not all at once in a flood.

**Why useful:** Saves memory for large data. You don't load everything into RAM.

```python
# Normal function — returns ALL values at once
def normal_squares(n):
    return [x**2 for x in range(n)]   # Entire list in memory

# Generator — returns ONE value at a time
def gen_squares(n):
    for x in range(n):
        yield x**2   # 'yield' makes it a generator

# Usage
for sq in gen_squares(1000000):   # Only ONE value in memory at a time!
    print(sq)

# Generator expression (like list comprehension)
gen = (x**2 for x in range(10))   # Note: () not []
next(gen)   # 0
next(gen)   # 1
next(gen)   # 4
```

**Generator vs List:**
| | List | Generator |
|---|---|---|
| Memory | All at once | One at a time |
| Speed to create | Slower | Faster |
| Can iterate again | YES | NO (one-time use) |
| Use when | Small data, reuse | Large data, one-time |

**Real-World:** Reading a 10GB log file line by line, streaming API responses, infinite sequences.

---

## 4.3 Iterators vs Iterables

**Iterable:** Any object you can loop over. Has `__iter__()` method.
Examples: list, tuple, string, dict, set

**Iterator:** Object that knows the CURRENT position and gets NEXT item. Has both `__iter__()` AND `__next__()`.

```python
my_list = [1, 2, 3]     # Iterable
it = iter(my_list)       # Iterator (created from iterable)

next(it)   # 1
next(it)   # 2
next(it)   # 3
next(it)   # StopIteration error!

# Custom Iterator
class CountUp:
    def __init__(self, limit):
        self.current = 0
        self.limit = limit

    def __iter__(self):
        return self

    def __next__(self):
        if self.current >= self.limit:
            raise StopIteration
        val = self.current
        self.current += 1
        return val

for num in CountUp(5):
    print(num)   # 0 1 2 3 4
```

**Memory Trick:**
- Iterable = "I can be iterated" (has `__iter__`)
- Iterator = "I am iterating right now" (has `__iter__` + `__next__`)
- Every Iterator is an Iterable, but NOT every Iterable is an Iterator!

---

## 4.4 Lambda, map, filter, reduce

**Lambda — Anonymous (nameless) function:**
```python
# Normal function
def square(x): return x**2

# Lambda equivalent
square = lambda x: x**2
print(square(5))   # 25

# Multi-argument lambda
add = lambda x, y: x + y
print(add(3, 4))   # 7
```

**map() — Apply function to every element:**
```python
nums = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x**2, nums))
print(squares)   # [1, 4, 9, 16, 25]

# With regular function
def double(x): return x * 2
doubled = list(map(double, nums))   # [2, 4, 6, 8, 10]
```

**filter() — Keep elements where function returns True:**
```python
nums = [1, 2, 3, 4, 5, 6, 7, 8]
evens = list(filter(lambda x: x % 2 == 0, nums))
print(evens)   # [2, 4, 6, 8]
```

**reduce() — Combine all elements into one value:**
```python
from functools import reduce
nums = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x + y, nums)
print(total)   # 15 (1+2+3+4+5)
```

**Memory Trick:**
- map = TRANSFORM every element
- filter = KEEP some elements
- reduce = COMBINE all elements into one

---

## 4.5 *args and **kwargs

**`*args` = Variable number of positional arguments (stored as tuple)**
**`**kwargs` = Variable number of keyword arguments (stored as dict)**

```python
def add_all(*args):
    print(type(args))   # <class 'tuple'>
    return sum(args)

add_all(1, 2, 3)       # 6
add_all(1, 2, 3, 4, 5) # 15

def print_info(**kwargs):
    print(type(kwargs))  # <class 'dict'>
    for k, v in kwargs.items():
        print(f"{k}: {v}")

print_info(name="Alice", age=25, city="Mumbai")

# Both together
def everything(normal, *args, **kwargs):
    print(normal)   # positional
    print(args)     # extra positionals
    print(kwargs)   # keyword args

everything("hello", 1, 2, 3, name="Bob", age=30)
```

**Unpacking with * and **:**
```python
def add(a, b, c): return a + b + c

nums = [1, 2, 3]
add(*nums)           # Unpacks list → add(1, 2, 3)

info = {"a": 1, "b": 2, "c": 3}
add(**info)          # Unpacks dict → add(a=1, b=2, c=3)
```

---

## 4.6 Closures

**Simple Definition:** A closure is when an inner function REMEMBERS variables from its outer function, even after the outer function has finished running. Like remembering your mom's recipe even after she's gone.

```python
def outer(message):
    def inner():           # Inner function
        print(message)     # Remembers 'message' from outer scope!
    return inner           # Return the function, not call it

greet = outer("Hello!")   # outer() finishes, but 'message' is remembered
greet()                    # Prints: Hello!

# Practical example — Counter
def make_counter():
    count = 0                   # This variable is "closed over"
    def increment():
        nonlocal count          # Access outer variable
        count += 1
        return count
    return increment

counter = make_counter()
counter()   # 1
counter()   # 2
counter()   # 3
```

**Real-World:** Decorators are closures, partial functions, callbacks.

---

## 4.7 Comprehensions

```python
# List Comprehension
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]

# Nested
matrix = [[i*j for j in range(3)] for i in range(3)]

# Dict Comprehension
word_len = {word: len(word) for word in ["hello", "world", "python"]}
# {'hello': 5, 'world': 5, 'python': 6}

# Set Comprehension
unique_len = {len(word) for word in ["hello", "world", "python"]}
# {5, 6}

# Generator Expression
gen = (x**2 for x in range(10))   # Memory efficient
```

---

## 4.8 Context Manager (`with` statement)

**Simple Definition:** A context manager automatically handles setup and cleanup. Like a hotel room — hotel manages check-in and check-out for you.

**Why needed:** Ensures resources (files, DB connections) are always properly closed, even if error occurs.

```python
# Without context manager — RISKY
f = open("file.txt", "r")
data = f.read()
f.close()           # Might not run if error occurs above!

# With context manager — SAFE
with open("file.txt", "r") as f:
    data = f.read()
# File automatically closed after with block, even if error!
```

**Custom Context Manager:**
```python
class DBConnection:
    def __enter__(self):
        print("Connecting to database...")
        return self             # Returned as 'as' variable

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Closing connection...")
        return False            # Don't suppress exceptions

with DBConnection() as db:
    print("Using database...")
# Output:
# Connecting to database...
# Using database...
# Closing connection...
```

**Using `contextlib`:**
```python
from contextlib import contextmanager

@contextmanager
def managed_resource():
    print("Setup")
    yield               # Code in 'with' block runs here
    print("Cleanup")

with managed_resource():
    print("Working...")
# Setup → Working... → Cleanup
```

---

## 4.9 Magic Methods (Dunder Methods)

**Simple Definition:** Special methods Python calls automatically. Named with double underscore on both sides like `__init__`. "Dunder" = "Double UNDERscore".

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):                    # Called by print()
        return f"Vector({self.x}, {self.y})"

    def __repr__(self):                   # Called by repr(), debugging
        return f"Vector(x={self.x}, y={self.y})"

    def __add__(self, other):             # Called by +
        return Vector(self.x + other.x, self.y + other.y)

    def __len__(self):                    # Called by len()
        return int((self.x**2 + self.y**2)**0.5)

    def __eq__(self, other):              # Called by ==
        return self.x == other.x and self.y == other.y

    def __call__(self, scale):            # Called when object() is used
        return Vector(self.x * scale, self.y * scale)

    def __iter__(self):                   # Makes object iterable
        yield self.x
        yield self.y

v1 = Vector(3, 4)
v2 = Vector(1, 2)
print(v1)           # Vector(3, 4)  — __str__
print(v1 + v2)      # Vector(4, 6)  — __add__
print(len(v1))      # 5             — __len__
print(v1 == v2)     # False         — __eq__
print(v1(2))        # Vector(6, 8)  — __call__
for val in v1: print(val)  # 3, 4   — __iter__
```

**Common Dunder Methods:**
| Method | Triggered by |
|---|---|
| `__init__` | `Class()` |
| `__str__` | `print(obj)`, `str(obj)` |
| `__repr__` | `repr(obj)`, debugging |
| `__len__` | `len(obj)` |
| `__add__` | `obj + other` |
| `__eq__` | `obj == other` |
| `__lt__` | `obj < other` |
| `__call__` | `obj()` |
| `__iter__` | `for x in obj` |
| `__next__` | `next(obj)` |
| `__enter__` | `with obj as` |
| `__exit__` | end of `with` block |
| `__getitem__` | `obj[key]` |
| `__setitem__` | `obj[key] = val` |
| `__contains__` | `x in obj` |

---

## 4.10 zip() and enumerate()

```python
# zip() — pair up elements from multiple iterables
names = ["Alice", "Bob", "Charlie"]
scores = [90, 85, 92]
for name, score in zip(names, scores):
    print(f"{name}: {score}")

# enumerate() — add index to iteration
for i, name in enumerate(names):
    print(f"{i}: {name}")

for i, name in enumerate(names, start=1):   # Start from 1
    print(f"{i}: {name}")
```

---

# ═══════════════════════════════════════════════
# PART 5 — MEMORY MANAGEMENT
# ═══════════════════════════════════════════════

---

## 5.1 Stack vs Heap Memory

**Stack:** Small, fast memory. Stores function calls, local variables. LIFO (Last In, First Out).
**Heap:** Large, flexible memory. Stores objects (everything in Python is an object).

```python
def foo():
    x = 10          # x (reference) stored on Stack
    y = [1, 2, 3]   # y (reference) on Stack, [1,2,3] object on Heap

foo()               # Stack frame created
# foo() returns → stack frame destroyed
# If no more references to [1,2,3] → garbage collected from Heap
```

---

## 5.2 Reference Counting

**Python tracks HOW MANY variables point to an object.**
When count reaches 0, object is deleted.

```python
import sys
a = [1, 2, 3]
print(sys.getrefcount(a))   # 2 (a + getrefcount arg)

b = a                        # b also points to same object
print(sys.getrefcount(a))   # 3

del b                        # Remove one reference
print(sys.getrefcount(a))   # 2 — object still alive!

del a                        # Remove last reference → count = 0 → deleted!
```

---

## 5.3 Garbage Collection

**Python has TWO mechanisms:**
1. **Reference Counting** — immediate, for simple cases
2. **Cyclic GC** — for circular references

**Circular Reference Problem:**
```python
import gc

class Node:
    def __init__(self):
        self.ref = None

a = Node()
b = Node()
a.ref = b    # a points to b
b.ref = a    # b points to a — CIRCULAR REFERENCE!

del a
del b
# Reference count never reaches 0!
# Python's cyclic GC detects and cleans this up
gc.collect()   # Force garbage collection
```

---

## 5.4 Shallow Copy vs Deep Copy

**Shallow Copy:** Creates a new object but SAME references inside. Like making a copy of a folder but the files inside are shortcuts.

**Deep Copy:** Creates a completely new object with new copies of everything inside. Like making actual new files.

```python
import copy

original = [[1, 2, 3], [4, 5, 6]]

# Shallow copy — new list, but SAME inner lists!
shallow = copy.copy(original)
shallow[0][0] = 999
print(original[0][0])   # 999 — CHANGED! (same inner list)

# Deep copy — completely new, independent copy
deep = copy.deepcopy(original)
deep[0][0] = 999
print(original[0][0])   # 1 — NOT changed! (different inner list)
```

**Memory Trick:**
- Shallow = new container, same contents (references)
- Deep = new container, new contents (completely independent)

---

## 5.5 Python Interning

**Python reuses objects for small integers and strings to save memory.**

```python
# Integer interning (-5 to 256)
a = 100
b = 100
a is b   # True — same object! (interned)

a = 1000
b = 1000
a is b   # False — different objects (NOT interned)

# String interning
s1 = "hello"
s2 = "hello"
s1 is s2   # True — interned (no spaces, simple string)

s1 = "hello world"
s2 = "hello world"
s1 is s2   # May be False (implementation dependent)
```

**Why:** Optimization. Small integers are used constantly. Reusing them saves memory and time.

---

## 5.6 Memory Management Interview Questions

**Q1: What is the difference between `del` and `gc.collect()`?**
> `del` removes a variable reference (decrements ref count). If count reaches 0, object is freed. `gc.collect()` manually runs the cyclic garbage collector for circular references.

**Q2: When would you use deep copy vs shallow copy?**
> Shallow copy: when inner objects are immutable or you want to share them. Deep copy: when you need a completely independent clone with no shared state, especially for nested mutable objects.

**Q3: What is Python interning?**
> Python caches small integers (-5 to 256) and some strings in memory. Instead of creating new objects each time, Python reuses the cached ones. This is why `a = 100; b = 100; a is b` is `True`.

---

# ═══════════════════════════════════════════════
# PART 6 — MULTITHREADING / MULTIPROCESSING / ASYNC
# ═══════════════════════════════════════════════

---

## 6.1 Key Concepts

**Thread:** Smallest unit of execution WITHIN a process. Lightweight. Shares same memory.
**Process:** Independent program with its own memory space. Heavier.
**Concurrency:** Doing multiple things by SWITCHING between them quickly. (One cook, multiple dishes).
**Parallelism:** Doing multiple things TRULY at the same time. (Multiple cooks, multiple dishes).

---

## 6.2 GIL — Global Interpreter Lock

**Simple Definition:** GIL is a LOCK inside CPython that allows ONLY ONE thread to execute Python code at a time, even on multi-core CPUs.

**Why GIL exists:**
- Python's memory management (reference counting) is NOT thread-safe
- GIL prevents two threads from modifying reference counts simultaneously
- Easier to implement C extensions

**Impact:**
- Multi-threading is LIMITED in Python for CPU-bound tasks
- For IO-bound tasks, threading still works well (GIL released during IO)

**Memory Trick:** GIL = "Government-Issued Lock" — only one person (thread) in the government building at a time!

---

## 6.3 Threading

**Best for: IO-bound tasks** (network calls, file reads, API calls — GIL is released during IO wait)

```python
import threading
import time

def download(url):
    print(f"Downloading {url}")
    time.sleep(2)   # Simulates IO wait — GIL released here
    print(f"Done: {url}")

# Sequential (slow): 3 × 2 seconds = 6 seconds
# Threaded (fast): ~2 seconds (all wait simultaneously)

threads = []
urls = ["url1", "url2", "url3"]

for url in urls:
    t = threading.Thread(target=download, args=(url,))
    threads.append(t)
    t.start()

for t in threads:
    t.join()   # Wait for all threads to finish

print("All downloads complete!")
```

**Thread Safety — Lock:**
```python
import threading

counter = 0
lock = threading.Lock()

def increment():
    global counter
    for _ in range(100000):
        with lock:             # Only one thread at a time
            counter += 1

t1 = threading.Thread(target=increment)
t2 = threading.Thread(target=increment)
t1.start(); t2.start()
t1.join(); t2.join()
print(counter)   # 200000 (correct, thanks to lock)
```

---

## 6.4 Multiprocessing

**Best for: CPU-bound tasks** (calculations, image processing, ML — bypasses GIL with separate processes)

```python
import multiprocessing

def heavy_compute(n):
    return sum(i**2 for i in range(n))

if __name__ == "__main__":
    with multiprocessing.Pool(processes=4) as pool:   # 4 cores
        results = pool.map(heavy_compute, [10**6, 10**6, 10**6, 10**6])
    print(results)
```

---

## 6.5 Async / Await (Asyncio)

**Best for: High-volume IO-bound tasks** (thousands of concurrent API calls, websockets)

**Simple Definition:** Asyncio lets you pause a task while waiting (like waiting for API response) and run another task in the meantime. Like a waiter taking orders from multiple tables while one table's food is being prepared.

```python
import asyncio

async def fetch_data(url):           # 'async def' makes it a coroutine
    print(f"Fetching {url}")
    await asyncio.sleep(1)           # 'await' pauses here, switches to other tasks
    print(f"Got data from {url}")
    return f"data from {url}"

async def main():
    # Run concurrently
    results = await asyncio.gather(
        fetch_data("api1"),
        fetch_data("api2"),
        fetch_data("api3")
    )
    print(results)

asyncio.run(main())   # Run the event loop
```

**How Event Loop works:**
1. Run task 1 → hits `await` → pause task 1
2. Run task 2 → hits `await` → pause task 2
3. Run task 3 → hits `await` → pause task 3
4. Task 1's wait finishes → resume task 1
5. And so on...

---

## 6.6 ThreadPoolExecutor / ProcessPoolExecutor

```python
from concurrent.futures import ThreadPoolExecutor, ProcessPoolExecutor

def process_item(item):
    return item * 2

# Threading pool
with ThreadPoolExecutor(max_workers=5) as executor:
    results = list(executor.map(process_item, [1,2,3,4,5]))
print(results)   # [2, 4, 6, 8, 10]

# Process pool
with ProcessPoolExecutor(max_workers=4) as executor:
    results = list(executor.map(process_item, [1,2,3,4,5]))
```

---

## 6.7 Comparison Tables

### When to Use What?
| Use Case | Best Approach |
|---|---|
| Download 100 files | Threading or Asyncio |
| Process 4K images | Multiprocessing |
| Scrape 1000 websites | Asyncio |
| ML model training | Multiprocessing |
| Database queries (async DB) | Asyncio |
| Calculate primes | Multiprocessing |

### Threading vs Multiprocessing vs Async
| | Threading | Multiprocessing | Asyncio |
|---|---|---|---|
| GIL bypass | No | Yes | No |
| Memory | Shared | Separate | Shared |
| Best for | IO-bound | CPU-bound | High-concurrency IO |
| Overhead | Low | High | Very Low |
| Complexity | Medium | Medium | High |

### Parallelism vs Concurrency
| | Concurrency | Parallelism |
|---|---|---|
| Definition | Tasks start & stop interleaved | Tasks truly run simultaneously |
| Requires | Single core OK | Multiple cores needed |
| Python support | Threading, Asyncio | Multiprocessing |

---

## 6.8 Concurrency Interview Questions

**Q1: What is GIL and why does it exist?**
> GIL (Global Interpreter Lock) is a mutex in CPython that allows only one thread to run Python code at a time. It exists because Python's memory management (reference counting) is not thread-safe. Without GIL, two threads could corrupt reference counts simultaneously.

**Q2: How do you achieve true parallelism in Python?**
> Use `multiprocessing` module. Each process has its own GIL, so they run in true parallel on multiple CPU cores.

**Q3: Threading vs Asyncio — when to use which?**
> Use Threading for moderate IO-bound tasks (tens of threads). Use Asyncio for high-concurrency IO (thousands of concurrent connections) — it's more efficient because it's single-threaded with cooperative multitasking.

---

# ═══════════════════════════════════════════════
# PART 7 — FILE HANDLING & EXCEPTION HANDLING
# ═══════════════════════════════════════════════

---

## 7.1 File Handling

```python
# Writing
with open("data.txt", "w") as f:
    f.write("Hello, World!\n")
    f.writelines(["Line 1\n", "Line 2\n"])

# Reading
with open("data.txt", "r") as f:
    content = f.read()          # All content as string
    # OR
    lines = f.readlines()       # List of lines
    # OR
    for line in f:              # Memory efficient for large files
        print(line.strip())

# Appending
with open("data.txt", "a") as f:
    f.write("New line\n")
```

**File Modes:**
| Mode | Meaning |
|---|---|
| `r` | Read (default) |
| `w` | Write (overwrites!) |
| `a` | Append |
| `rb` | Read binary |
| `wb` | Write binary |
| `r+` | Read + Write |

---

## 7.2 JSON Handling

```python
import json

# Python dict → JSON string
data = {"name": "Alice", "age": 25, "hobbies": ["reading", "coding"]}
json_str = json.dumps(data, indent=2)   # Pretty print with indent

# JSON string → Python dict
parsed = json.loads(json_str)

# Write to file
with open("data.json", "w") as f:
    json.dump(data, f, indent=2)

# Read from file
with open("data.json", "r") as f:
    loaded = json.load(f)
```

**Memory Trick:**
- `json.dumps` → dump to **S**tring
- `json.dump` → dump to **F**ile
- `json.loads` → load from **S**tring
- `json.load` → load from **F**ile

---

## 7.3 CSV Handling

```python
import csv

# Write CSV
with open("data.csv", "w", newline="") as f:
    writer = csv.DictWriter(f, fieldnames=["name", "age"])
    writer.writeheader()
    writer.writerow({"name": "Alice", "age": 25})
    writer.writerow({"name": "Bob", "age": 30})

# Read CSV
with open("data.csv", "r") as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row["name"], row["age"])
```

---

## 7.4 Exception Handling

**Why needed:** Programs encounter errors (file not found, division by zero, network failure). Without handling, the whole program crashes. With handling, you can recover gracefully.

```python
try:
    result = 10 / 0             # Code that might fail
except ZeroDivisionError as e:  # Specific exception
    print(f"Error: {e}")
except (ValueError, TypeError):  # Multiple exceptions
    print("Value or Type error")
except Exception as e:           # Catch all other exceptions
    print(f"Unexpected error: {e}")
else:
    print("No error occurred!")  # Runs if NO exception
finally:
    print("Always runs!")        # Cleanup code — ALWAYS runs

# raise — manually raise exception
def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero!")
    return a / b
```

---

## 7.5 Custom Exceptions

```python
class InsufficientFundsError(Exception):
    def __init__(self, amount, balance):
        self.amount = amount
        self.balance = balance
        super().__init__(f"Cannot withdraw {amount}. Balance: {balance}")

class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def withdraw(self, amount):
        if amount > self.balance:
            raise InsufficientFundsError(amount, self.balance)
        self.balance -= amount

try:
    acc = BankAccount(100)
    acc.withdraw(200)
except InsufficientFundsError as e:
    print(e)   # Cannot withdraw 200. Balance: 100
```

---

## 7.6 Logging

**Why logging instead of print:**
- Log levels (DEBUG, INFO, WARNING, ERROR, CRITICAL)
- Can write to files, multiple destinations
- Can disable without removing code
- Timestamps, line numbers automatically

```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(name)s - %(levelname)s - %(message)s",
    handlers=[
        logging.FileHandler("app.log"),    # Write to file
        logging.StreamHandler()             # Also print to console
    ]
)

logger = logging.getLogger(__name__)

logger.debug("Detailed debug info")       # Development only
logger.info("Server started on port 8080")
logger.warning("Low memory: 90% used")
logger.error("Database connection failed")
logger.critical("System is shutting down!")
```

---

# ═══════════════════════════════════════════════
# PART 8 — PYTHON INTERNALS
# ═══════════════════════════════════════════════

---

## 8.1 LEGB Rule — Variable Scope

**LEGB = Local → Enclosing → Global → Built-in**

Python searches for variables in this ORDER.

```python
x = "global"          # Global scope

def outer():
    x = "enclosing"   # Enclosing scope

    def inner():
        x = "local"   # Local scope
        print(x)      # 'local' — found in Local first!

    inner()
    print(x)          # 'enclosing'

outer()
print(x)              # 'global'
```

**`global` and `nonlocal` keywords:**
```python
count = 0

def increment():
    global count     # Access global variable
    count += 1

def outer():
    x = 10
    def inner():
        nonlocal x   # Access enclosing variable
        x += 1
```

---

## 8.2 Namespace

**Namespace = Dictionary mapping names to objects.**

```python
# Built-in namespace: print, len, range — always available
# Global namespace: variables/functions at module level
# Local namespace: variables inside a function

import math
print(dir(math))      # See all names in math namespace
print(locals())       # Current local namespace
print(globals())      # Current global namespace
```

---

## 8.3 Metaclass

**Simple Definition:** A metaclass is a "class of a class." If `Dog` is a class that creates dog objects, a metaclass creates class objects.

```python
# type() is the default metaclass
print(type(42))        # <class 'int'>
print(type(int))       # <class 'type'> — int's metaclass is type!
print(type(type))      # <class 'type'> — type's metaclass is itself!

# Custom metaclass
class SingletonMeta(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=SingletonMeta):
    def __init__(self):
        print("Database created")

db1 = Database()   # Database created
db2 = Database()   # (nothing — same instance returned)
print(db1 is db2)  # True — Singleton!
```

---

## 8.4 Monkey Patching

**Simple Definition:** Changing a class or module AT RUNTIME, from outside the class.

```python
class Dog:
    def bark(self): print("Woof")

def new_bark(self): print("SUPER WOOF!")

Dog.bark = new_bark      # Monkey patch!
d = Dog()
d.bark()   # SUPER WOOF!
```

**Real-World Use:** Testing — patching external API calls with mock functions.

---

## 8.5 Serialization — Pickle

**Pickle:** Convert Python object to bytes (for saving to disk or network transfer).

```python
import pickle

data = {"name": "Alice", "scores": [95, 87, 92]}

# Serialize (pickle)
with open("data.pkl", "wb") as f:
    pickle.dump(data, f)

# Deserialize (unpickle)
with open("data.pkl", "rb") as f:
    loaded = pickle.load(f)

print(loaded)   # {'name': 'Alice', 'scores': [95, 87, 92]}
```

**Warning:** Never unpickle data from untrusted sources! Pickle can execute arbitrary code.

---

## 8.6 Hashing

**Hash function:** Takes input → returns fixed-size number. Same input → always same output.

```python
hash("hello")    # Always same number for same Python session
hash(42)         # 42
hash((1, 2, 3))  # Tuple is hashable

# hash([1,2,3])  # TypeError — list is not hashable!
```

**Why lists are not hashable:** Lists are mutable. If you store a list as dict key and then change it, the hash would change — key would be lost. Python prevents this by making mutable types unhashable.

---

# ═══════════════════════════════════════════════
# PART 9 — CODING QUESTIONS
# ═══════════════════════════════════════════════

---

## 9.1 String Problems

**Q: Reverse a string**
```python
s = "hello"
print(s[::-1])         # "olleh" — O(n) time, O(n) space
```

**Q: Check if palindrome**
```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]

print(is_palindrome("racecar"))   # True
print(is_palindrome("hello"))     # False
```

**Q: Count character frequency**
```python
from collections import Counter
s = "programming"
freq = Counter(s)
print(freq)        # Counter({'g': 2, 'r': 2, ...})
print(freq.most_common(3))  # Top 3 most common
```

**Q: Check if two strings are anagrams**
```python
def are_anagrams(s1, s2):
    return sorted(s1.lower()) == sorted(s2.lower())
    # OR: Counter(s1.lower()) == Counter(s2.lower())

print(are_anagrams("listen", "silent"))   # True
```

**Q: Find all permutations**
```python
from itertools import permutations
perms = list(permutations("abc"))
print(perms)   # All 6 permutations
```

---

## 9.2 List Problems

**Q: Remove duplicates preserving order**
```python
def remove_dups(lst):
    seen = set()
    return [x for x in lst if not (x in seen or seen.add(x))]
```

**Q: Find second largest element**
```python
def second_largest(lst):
    unique = sorted(set(lst), reverse=True)
    return unique[1] if len(unique) > 1 else None
```

**Q: Flatten nested list**
```python
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

print(flatten([1, [2, [3, 4]], 5]))   # [1, 2, 3, 4, 5]
```

**Q: Rotate list by k positions**
```python
def rotate(lst, k):
    k = k % len(lst)
    return lst[k:] + lst[:k]

print(rotate([1,2,3,4,5], 2))   # [3, 4, 5, 1, 2]
```

---

## 9.3 Dictionary Problems

**Q: Group words by length**
```python
from collections import defaultdict

words = ["cat", "dog", "elephant", "ant", "bear"]
grouped = defaultdict(list)
for word in words:
    grouped[len(word)].append(word)
print(dict(grouped))
# {3: ['cat', 'dog', 'ant'], 8: ['elephant'], 4: ['bear']}
```

**Q: Find top N words in a text**
```python
from collections import Counter
text = "the quick brown fox jumps over the lazy dog the"
words = text.split()
top_3 = Counter(words).most_common(3)
print(top_3)   # [('the', 3), ('quick', 1), ('brown', 1)]
```

---

## 9.4 OOPs Coding

**Q: Implement a Stack using OOPs**
```python
class Stack:
    def __init__(self):
        self._data = []

    def push(self, item):
        self._data.append(item)

    def pop(self):
        if self.is_empty():
            raise IndexError("Stack is empty")
        return self._data.pop()

    def peek(self):
        if self.is_empty():
            raise IndexError("Stack is empty")
        return self._data[-1]

    def is_empty(self):
        return len(self._data) == 0

    def __len__(self):
        return len(self._data)

s = Stack()
s.push(1); s.push(2); s.push(3)
print(s.pop())    # 3
print(s.peek())   # 2
```

**Q: Implement Singleton Pattern**
```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

s1 = Singleton()
s2 = Singleton()
print(s1 is s2)   # True — same instance!
```

---

## 9.5 Recursion Problems

**Q: Fibonacci**
```python
# Simple recursive (slow — exponential time)
def fib(n):
    if n <= 1: return n
    return fib(n-1) + fib(n-2)

# Memoized (fast — O(n) time)
from functools import lru_cache

@lru_cache(maxsize=None)
def fib_memo(n):
    if n <= 1: return n
    return fib_memo(n-1) + fib_memo(n-2)

print(fib_memo(50))   # Very fast!
```

**Q: Factorial**
```python
def factorial(n):
    if n == 0: return 1           # Base case
    return n * factorial(n - 1)  # Recursive case
```

---

## 9.6 Sorting & Searching

**Q: Implement Binary Search**
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid          # Found!
        elif arr[mid] < target:
            left = mid + 1      # Search right half
        else:
            right = mid - 1     # Search left half
    return -1                   # Not found

arr = [1, 3, 5, 7, 9, 11, 15]
print(binary_search(arr, 7))   # 3 (index)
# Time: O(log n), Space: O(1)
```

**Q: Sort using key**
```python
employees = [
    {"name": "Alice", "salary": 50000},
    {"name": "Bob", "salary": 70000},
    {"name": "Charlie", "salary": 45000}
]

# Sort by salary
sorted_emp = sorted(employees, key=lambda e: e["salary"], reverse=True)
# Bob (70000), Alice (50000), Charlie (45000)
```

---

## 9.7 Multithreading Coding

**Q: Thread-safe counter**
```python
import threading

class ThreadSafeCounter:
    def __init__(self):
        self._count = 0
        self._lock = threading.Lock()

    def increment(self):
        with self._lock:
            self._count += 1

    def get(self):
        with self._lock:
            return self._count

counter = ThreadSafeCounter()
threads = [threading.Thread(target=counter.increment) for _ in range(1000)]
for t in threads: t.start()
for t in threads: t.join()
print(counter.get())   # 1000 (always correct)
```

---

## 9.8 Async Coding

**Q: Fetch multiple URLs concurrently**
```python
import asyncio

async def fake_fetch(url, delay):
    await asyncio.sleep(delay)
    return f"Response from {url}"

async def main():
    urls = [("api1", 1), ("api2", 2), ("api3", 0.5)]
    tasks = [fake_fetch(url, delay) for url, delay in urls]
    results = await asyncio.gather(*tasks)
    for r in results: print(r)

asyncio.run(main())
# All complete in ~2 seconds (longest delay) instead of 3.5 seconds!
```

---

# ═══════════════════════════════════════════════
# PART 10 — INTERVIEW QUESTIONS MASTER LIST
# ═══════════════════════════════════════════════

---

## 10.1 BEGINNER QUESTIONS

| Q | Best Answer |
|---|---|
| What is Python? | High-level, interpreted, dynamically-typed, general-purpose language. |
| What is PEP 8? | Python's style guide. Rules for writing clean, readable code. Covers indentation (4 spaces), naming conventions, line length (79 chars). |
| What is `None`? | Python's null value. Represents absence of value. Type is `NoneType`. |
| Difference between `list` and `tuple`? | List is mutable (can change), tuple is immutable. Tuple faster and less memory. |
| What are Python keywords? | Reserved words like `if`, `for`, `class`, `def` — can't use as variable names. |
| What is `*args`? | Allows function to accept any number of positional args. Stored as tuple. |
| What is `**kwargs`? | Allows function to accept any number of keyword args. Stored as dict. |
| What is list comprehension? | Concise way to create lists: `[x**2 for x in range(10)]` |
| `is` vs `==`? | `==` compares values. `is` compares identity (same memory location). |
| What are falsy values? | `0`, `""`, `[]`, `{}`, `()`, `None`, `False` |

---

## 10.2 INTERMEDIATE QUESTIONS

| Q | Best Answer |
|---|---|
| What is a decorator? | A function that wraps another function to add behavior without modifying it. Used for logging, auth, timing. |
| What is a generator? | Function with `yield` that produces values lazily, one at a time. Memory efficient for large data. |
| Shallow vs Deep copy? | Shallow copies container but shares inner objects. Deep copy creates fully independent clone. |
| What is GIL? | Global Interpreter Lock in CPython. Allows only one thread to run Python code at a time. |
| What is LEGB? | Scope search order: Local → Enclosing → Global → Built-in |
| What is `__init__` vs `__new__`? | `__new__` creates the object. `__init__` initializes it. `__new__` called first. |
| What is `@classmethod` vs `@staticmethod`? | `@classmethod` gets `cls` first arg (class access). `@staticmethod` gets nothing (utility function). |
| What is `@property`? | Makes a method accessible like an attribute. Provides getter/setter/deleter control. |
| What is duck typing? | "If it walks like a duck and quacks like a duck, it's a duck." Python uses behavior, not type. |
| What is `__slots__`? | Restricts instance attributes to predefined list. Saves memory by avoiding `__dict__`. |

---

## 10.3 ADVANCED QUESTIONS

| Q | Best Answer |
|---|---|
| How does Python's GC work? | Reference counting (immediate) + cyclic GC (for circular references). `gc` module controls cyclic GC. |
| What is a metaclass? | Class's class. Controls how classes are created. `type` is the default metaclass. |
| What is `__mro__`? | Method Resolution Order — order Python searches for methods in inheritance. Uses C3 linearization. |
| How do coroutines differ from generators? | Generators produce values (`yield`). Coroutines are awaitable functions (`async def`, `await`). Both use suspension mechanism. |
| What is `functools.lru_cache`? | Decorator that caches function results. Memoization. Returns cached result for same args. |
| What is `__slots__`? | Class-level dict replacement. Defines exact attributes allowed. Memory saving 30-40%. |
| What is `weakref`? | Reference to object that doesn't prevent garbage collection. Used for caches, event listeners. |
| Explain `contextlib.contextmanager` | Decorator to create context managers from generator functions instead of class with `__enter__/__exit__`. |
| What is thread starvation? | A thread never gets CPU time because other threads always hold the lock. Avoided with fair locking. |
| What is `asyncio.gather` vs `asyncio.wait`? | `gather` returns results in order, raises first exception. `wait` gives more control over completion criteria. |

---

## 10.4 SENIOR / PRODUCTION-LEVEL QUESTIONS

**Q: How do you handle high memory usage in a Python service?**
> Profile with `memory_profiler` or `tracemalloc`. Look for: large lists (use generators instead), accumulating caches (use `lru_cache` with max size), circular references (use `weakref`). Consider `__slots__` for classes with many instances. Use streaming for large files.

**Q: How would you make a Python API handle 10,000 concurrent requests?**
> Use `asyncio` with an async web framework (FastAPI, aiohttp). Use async database drivers (asyncpg, motor). Use connection pooling. Deploy multiple workers with gunicorn/uvicorn. Use Redis for caching. Consider message queues (Celery/RabbitMQ) for heavy tasks.

**Q: What causes thread safety issues and how do you fix them?**
> When multiple threads read-modify-write shared state. Fix with: `threading.Lock()` for critical sections, `threading.RLock()` for reentrant locks, `queue.Queue` for thread-safe data passing, `threading.local()` for thread-local storage. Prefer immutable data structures.

**Q: How do you debug a Python memory leak in production?**
> 1. Use `tracemalloc` to track allocations. 2. Use `objgraph` to find most common objects. 3. Look for growing caches/lists. 4. Check for circular references. 5. Profile with `py-spy` for running processes. 6. Monitor with `psutil` for RSS/heap growth.

**Q: Explain Python's import system.**
> `import` searches `sys.path` (current dir, PYTHONPATH, installation dirs). Module loaded once, cached in `sys.modules`. Subsequent imports return cached. `importlib` can reload. Circular imports can be resolved by lazy imports or restructuring.

---

## 10.5 SCENARIO-BASED QUESTIONS

**Q: You need to process 10 million records from a CSV. How?**
```python
# Use generator — don't load all into memory
def process_csv(filename):
    with open(filename) as f:
        reader = csv.DictReader(f)
        for row in reader:
            yield process_row(row)   # Process one at a time

for result in process_csv("huge_file.csv"):
    save_to_db(result)   # Save each, not all at once
```

**Q: You notice your Flask API is slow. How do you diagnose?**
> 1. Add timing decorators to measure slow endpoints. 2. Check database queries — N+1 problem? Add `.explain()`. 3. Use caching (Redis) for repeated queries. 4. Profile with `cProfile`. 5. Check if async could help. 6. Look for blocking IO calls.

**Q: Two threads are deadlocked. How do you identify and fix?**
> Identify: Use `threading` module's thread dump or `py-spy`. Deadlock = Thread A holds Lock1, wants Lock2. Thread B holds Lock2, wants Lock1. Fix: Always acquire locks in same order. Use `timeout` in `lock.acquire(timeout=5)`. Use `asyncio` to avoid threads altogether.

---

# ═══════════════════════════════════════════════
# PART 11 — PRODUCTION-LEVEL PYTHON
# ═══════════════════════════════════════════════

---

## 11.1 SOLID Principles (Simplified)

| Principle | Simple Meaning | Example |
|---|---|---|
| **S** — Single Responsibility | One class = One job | `UserAuth` only handles auth, not emails |
| **O** — Open/Closed | Open for extension, closed for modification | Add new payment via subclass, not editing existing code |
| **L** — Liskov Substitution | Subclass should work wherever parent works | `Square` subclassing `Rectangle` should behave correctly |
| **I** — Interface Segregation | Don't force classes to implement unused methods | Split big interface into smaller ones |
| **D** — Dependency Inversion | Depend on abstractions, not concrete classes | Inject DB interface, not specific DB class |

---

## 11.2 Clean Code Practices

```python
# BAD
def p(d, t):
    return d * t / 100

# GOOD — descriptive names
def calculate_tax(amount: float, tax_rate: float) -> float:
    """Calculate tax amount for given amount and rate."""
    return amount * tax_rate / 100

# Type hints (Python 3.5+)
def get_user(user_id: int) -> dict | None:
    pass

# Constants in UPPER_CASE
MAX_RETRIES = 3
DEFAULT_TIMEOUT = 30
DATABASE_URL = "postgresql://..."
```

---

## 11.3 Caching

```python
from functools import lru_cache
import redis

# In-memory cache (for pure functions)
@lru_cache(maxsize=128)
def expensive_calculation(n: int) -> int:
    return sum(i**2 for i in range(n))

# Redis cache (for distributed/persistent caching)
cache = redis.Redis(host="localhost", port=6379)

def get_user(user_id: int):
    key = f"user:{user_id}"
    cached = cache.get(key)
    if cached:
        return json.loads(cached)      # Cache HIT

    user = db.fetch_user(user_id)      # Cache MISS — hit DB
    cache.setex(key, 3600, json.dumps(user))  # Cache for 1 hour
    return user
```

---

## 11.4 Environment Variables

```python
import os
from dotenv import load_dotenv   # pip install python-dotenv

load_dotenv()   # Load .env file

DATABASE_URL = os.getenv("DATABASE_URL", "default_value")
SECRET_KEY = os.environ["SECRET_KEY"]   # Raises error if missing
DEBUG = os.getenv("DEBUG", "False").lower() == "true"
```

**.env file:**
```
DATABASE_URL=postgresql://user:pass@localhost/mydb
SECRET_KEY=super-secret-key-here
DEBUG=False
```

**Never commit .env to git! Add to .gitignore.**

---

## 11.5 Virtual Environment

```bash
# Create
python -m venv venv

# Activate
source venv/bin/activate       # Linux/Mac
venv\Scripts\activate          # Windows

# Install packages
pip install flask sqlalchemy redis

# Freeze dependencies
pip freeze > requirements.txt

# Install from requirements
pip install -r requirements.txt

# Deactivate
deactivate
```

---

## 11.6 Design Patterns

```python
# Singleton — one instance only
class DatabasePool:
    _instance = None

    def __new__(cls):
        if not cls._instance:
            cls._instance = super().__new__(cls)
        return cls._instance

# Factory — create objects without specifying class
class NotificationFactory:
    @staticmethod
    def create(notification_type: str):
        if notification_type == "email":
            return EmailNotification()
        elif notification_type == "sms":
            return SMSNotification()
        raise ValueError(f"Unknown type: {notification_type}")

# Observer — event-driven
class EventBus:
    def __init__(self):
        self._listeners = {}

    def subscribe(self, event, callback):
        self._listeners.setdefault(event, []).append(callback)

    def publish(self, event, data):
        for callback in self._listeners.get(event, []):
            callback(data)
```

---

# ═══════════════════════════════════════════════
# PART 12 — IMPORTANT COMPARISONS (QUICK REFERENCE)
# ═══════════════════════════════════════════════

---

## Master Comparison Table

### List vs Tuple
| | List | Tuple |
|---|---|---|
| Mutable | ✅ Yes | ❌ No |
| Syntax | `[]` | `()` |
| Speed | Slower | Faster |
| Dict key | ❌ No | ✅ Yes |
| Memory | More | Less |

### Set vs Frozenset
| | Set | Frozenset |
|---|---|---|
| Mutable | ✅ Yes | ❌ No |
| Dict key | ❌ No | ✅ Yes |
| Operations | All set ops | All set ops |

### Deep Copy vs Shallow Copy
| | Shallow | Deep |
|---|---|---|
| Container | New | New |
| Inner objects | Same (shared) | New (independent) |
| Speed | Faster | Slower |
| Risk | Shared mutation | No risk |

### Thread vs Process
| | Thread | Process |
|---|---|---|
| Memory | Shared | Separate |
| GIL bypass | ❌ No | ✅ Yes |
| Communication | Easy (shared mem) | Hard (IPC) |
| Best for | IO-bound | CPU-bound |
| Overhead | Low | High |

### Lambda vs Function
| | Lambda | Function |
|---|---|---|
| Syntax | `lambda x: x*2` | `def square(x): return x*2` |
| Name | Anonymous | Named |
| Body | Single expression | Multiple statements |
| Docstring | ❌ No | ✅ Yes |
| Use case | Short, one-time | Reusable, complex |

### Generator vs Iterator
| | Generator | Iterator |
|---|---|---|
| Created with | `yield` / `()` | Class with `__iter__` + `__next__` |
| Code | Less | More |
| Memory | Lazy (low) | Lazy (low) |
| Use case | Simple sequences | Complex stateful iteration |

### `append` vs `extend`
```python
a = [1, 2, 3]
a.append([4, 5])   # [1, 2, 3, [4, 5]]   — adds as ONE element
a = [1, 2, 3]
a.extend([4, 5])   # [1, 2, 3, 4, 5]     — adds each element
```

### `remove` vs `pop`
```python
lst = [1, 2, 3, 2]
lst.remove(2)   # removes FIRST occurrence of VALUE 2 → [1, 3, 2]
lst.pop(1)      # removes element at INDEX 1, returns it → returns 3
lst.pop()       # removes LAST element, returns it
```

### `is` vs `==`
```python
a = [1, 2, 3]
b = [1, 2, 3]
a == b    # True  — same VALUE
a is b    # False — different OBJECTS

c = a
a is c    # True  — same OBJECT (same memory address)
```

### `copy` vs `deepcopy`
```python
import copy
original = [[1, 2], [3, 4]]
shallow = copy.copy(original)    # Inner lists are SHARED
deep = copy.deepcopy(original)   # Completely INDEPENDENT
```

### `__str__` vs `__repr__`
| | `__str__` | `__repr__` |
|---|---|---|
| Called by | `print()`, `str()` | `repr()`, debugger |
| Purpose | Human-friendly | Developer/debug-friendly |
| Should be | Readable | Unambiguous, recreatable |

---

# ═══════════════════════════════════════════════
# PART 13 — QUICK REVISION NOTES
# ═══════════════════════════════════════════════

---

## 🧠 TOP 50 MEMORY TRICKS

1. **Python = Interpreted** but compiles to bytecode first
2. **GIL = Government-Issued Lock** — one thread at a time
3. **List = Mutable bag**, **Tuple = Locked bag**
4. **Dict = Hash map** — O(1) lookup
5. **Set = Unique hash set** — O(1) membership test
6. **`{}` = empty dict**, **`set()` = empty set**
7. **LEGB = Local → Enclosing → Global → Built-in**
8. **`is` = identity** (same object), **`==` = equality** (same value)
9. **Shallow = same refs inside**, **Deep = completely new**
10. **Decorator = gift wrapper** for functions
11. **Generator = lazy producer** — one at a time
12. **Iterator = knows position** — has `__next__`
13. **`*args` = tuple**, **`**kwargs` = dict**
14. **Closure = function remembers outer scope**
15. **`map` = transform**, **`filter` = keep**, **`reduce` = combine**
16. **`json.dumps` = to String**, **`json.dump` = to File**
17. **Threading = IO-bound**, **Multiprocessing = CPU-bound**
18. **Asyncio = many IO concurrently** (single thread)
19. **`try/except/else/finally`** — else if no error, finally always
20. **`@classmethod` gets `cls`**, **`@staticmethod` gets nothing**
21. **MRO = Left to Right, Depth First** (C3 algorithm)
22. **`super()` = call parent's method**
23. **`__init__` = initializer**, **`__new__` = creator**
24. **Abstract class = cannot be instantiated**
25. **Encapsulation = data hiding** with `_` and `__`
26. **Polymorphism = same name, different behavior**
27. **Composition = object inside object** (owns it)
28. **Aggregation = object gets object** (doesn't own it)
29. **Singleton = one instance only**
30. **`lru_cache` = memoization decorator**
31. **`with` statement = context manager** (auto cleanup)
32. **`yield` = pause + return** (generator)
33. **`await` = pause coroutine** (asyncio)
34. **Pickling = Python object → bytes**
35. **Interning = Python caches small ints and strings**
36. **Hashing = key → memory address** (that's why dict is fast)
37. **`nonlocal` = modify enclosing scope variable**
38. **`global` = modify global variable from function**
39. **f-strings = fastest string formatting** (Python 3.6+)
40. **`sorted()` returns new list**, **`.sort()` modifies in place**
41. **`list()` vs `tuple()` vs `set()` = type conversion**
42. **`enumerate()` = index + value**
43. **`zip()` = pair elements**
44. **`Counter` = frequency counting**
45. **`defaultdict` = dict with default value**
46. **`OrderedDict` = dict remembers insertion order** (pre-3.7)
47. **`namedtuple` = tuple with named fields**
48. **`dataclass` = class with auto `__init__`, `__repr__`, `__eq__`**
49. **`functools.partial` = pre-fill function arguments**
50. **`os.getenv()` = read environment variable**

---

## 🎯 INTERVIEW CHEAT SHEET — COMMON TRAPS

| Trap | Wrong Assumption | Correct Answer |
|---|---|---|
| `{}` type | "It's a set" | Empty dict! Use `set()` for empty set |
| Mutable default arg | `def f(lst=[]):` is fine | DANGEROUS! Same list reused each call. Use `None` default |
| `is` for strings | `"hello" is "hello"` always True | Only for interned strings. Use `==` for comparison |
| Late binding closure | Variables in loops | `lambda i=i: i` to capture value immediately |
| Threading = Parallel | Python threads run in parallel | GIL prevents true parallelism. Use multiprocessing |
| `del` = memory freed | `del x` deletes object | Deletes reference. Object freed only when ref count = 0 |
| `sort()` returns list | `result = list.sort()` | Returns `None`. Use `sorted()` to get new list |
| Integer interning | `1000 is 1000` is True | Only -5 to 256 are interned. Larger ints may differ |

---

## 🚀 FINAL QUICK REVISION — KEY CONCEPTS

```
PYTHON BASICS:
  Interpreted → Compiled to bytecode → PVM runs bytecode
  Dynamic typing — type determined at runtime
  Everything is an object (even functions, classes)

DATA TYPES:
  Mutable:   list, dict, set, bytearray
  Immutable: tuple, str, int, float, bool, frozenset, bytes

OOPs:
  4 Pillars: Encapsulation, Inheritance, Polymorphism, Abstraction
  MRO: C3 Linearization — left to right, depth first
  super() — calls parent class

ADVANCED:
  Decorator = wrapper function
  Generator = yield → lazy iteration
  Closure = inner function + outer scope variable
  *args = tuple, **kwargs = dict
  Context Manager = __enter__ + __exit__

MEMORY:
  Reference Counting + Cyclic GC
  Shallow: new container, same refs
  Deep: completely new, no sharing
  Interning: -5 to 256, simple strings cached

CONCURRENCY:
  GIL: 1 thread at a time (CPython)
  Threading: IO-bound
  Multiprocessing: CPU-bound
  Asyncio: High concurrency IO

INTERNALS:
  LEGB: Local → Enclosing → Global → Built-in
  Hash: key → hash number → memory slot
  Pickle: serialize Python objects to bytes
```

---

*📌 Study this guide daily. Revise Part 12 (Comparisons) and Part 13 (Memory Tricks) the night before your interview.*

*✅ Practice coding questions daily on LeetCode/HackerRank.*

*🎯 Focus areas for TCS: Basic Python, OOPs, File handling, Exception handling, Basic algorithms.*

*🎯 Focus areas for Product companies: Advanced Python, OOPs, Concurrency, System design, Optimization, Clean code.*

---
**END OF PYTHON COMPLETE INTERVIEW MASTER GUIDE**
---
