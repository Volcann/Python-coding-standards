# PEP 8 (Code formatting)
PEP 8 (Python Enhancement Proposal 8) is the official style guide for Python code. It provides guidelines to improve the readability and consistency of Python code.  

**Common PEP 8 Issues in Python:**  

1. **Indentation Errors**  
   - Use **4 spaces per indentation level** (avoid tabs).  
   - ❌ **Bad:**  
     ```python
     def foo():
       print("Hello")  # Incorrect indentation (2 spaces)
     ```
   - ✅ **Good:**  
     ```python
     def foo():
         print("Hello")  # Correct indentation (4 spaces)
     ```

2. **Line Length Exceeds 79 Characters**  
   - Keep lines **≤79 characters** (preferably **≤72 for comments**).  
   - Use line breaks or implicit line continuation (`\`).  
   - ❌ **Bad:**  
     ```python
     print("This is a very long line that exceeds the recommended 79 characters limit, which should be avoided.")  
     ```
   - ✅ **Good:**  
     ```python
     print(
         "This is a very long line that exceeds the recommended 79 characters limit, "
         "which should be avoided."
     )
     ```

3. **Whitespace Issues**  
   - Avoid extra spaces around operators or inside parentheses.  
   - ❌ **Bad:**  
     ```python
     a = ( 1, 2 )  # Spaces inside parentheses
     b  =  5  + 2  # Extra spaces around `=`, `+`
     ```
   - ✅ **Good:**  
     ```python
     a = (1, 2)
     b = 5 + 2
     ```

4. **Blank Lines**  
   - Use **2 blank lines** before top-level functions and classes.  
   - Use **1 blank line** between methods inside a class.  
   - ❌ **Bad:**  
     ```python
     def foo():
         pass
     def bar():
         pass
     ```
   - ✅ **Good:**  
     ```python
     def foo():
         pass
     
     
     def bar():
         pass
     ```

5. **Improper Naming Conventions**  
   - Variable names should be **lower_case_with_underscores**.  
   - Constants should be **UPPER_CASE_WITH_UNDERSCORES**.  
   - Class names should use **CamelCase**.  
   - ❌ **Bad:**  
     ```python
     myVariable = 10  # Wrong variable naming
     class myclass:  # Wrong class naming
         pass
     ```
   - ✅ **Good:**  
     ```python
     my_variable = 10  
     
     class MyClass:
         pass
     ```

6. **Unused Imports**  
   - Remove unused imports to keep the code clean.  
   - ❌ **Bad:**  
     ```python
     import os  # Not used in the script
     import sys  # Not used either
     ```
   - ✅ **Good:**  
     ```python
     import os  # Used in the script
     print(os.name)
     ```

7. **Trailing Whitespace**  
   - Avoid unnecessary spaces at the end of a line.  
   - ❌ **Bad:**  
     ```python
     print("Hello, World!")    
     ```
   - ✅ **Good:**  
     ```python
     print("Hello, World!")
     ```

8. **Improper Use of `if __name__ == "__main__":`**  
   - Always use this when writing scripts that should only execute when run directly.  
   - ✅ **Good:**  
     ```python
     def main():
         print("Running script")
     
     if __name__ == "__main__":
         main()
     ```

9. **Improper Exception Handling**  
   - Avoid using `except:` without specifying the exception type.  
   - ❌ **Bad:**  
     ```python
     try:
         x = 1 / 0
     except:
         print("Error!")  # Catches all exceptions (bad practice)
     ```
   - ✅ **Good:**  
     ```python
     try:
         x = 1 / 0
     except ZeroDivisionError:
         print("Cannot divide by zero.")
     ```
   
### 10. **Module and Import Ordering**  
   - Follow the correct import order:  
     1. **Standard library imports** (e.g., `os`, `sys`)  
     2. **Third-party imports** (e.g., `numpy`, `pandas`)  
     3. **Local application imports**  
   - Separate each section with a **blank line**.  
   - ❌ **Bad:**  
     ```python
     import numpy as np
     import os
     from my_module import my_function
     ```
   - ✅ **Good:**  
     ```python
     import os  
     import sys  

     import numpy as np  
     import pandas as pd  

     from my_module import my_function  
     ```

### 11. **Trailing Commas in Lists, Tuples, and Dicts**  
   - Use trailing commas in multi-line structures to avoid syntax errors when adding new elements.  
   - ✅ **Good:**  
     ```python
     my_dict = {
         "name": "Alice",
         "age": 25,
         "city": "New York",  # Trailing comma makes future edits easier
     }
     ```

### 12. **Docstrings and Comments**  
   - Use **docstrings** for modules, functions, and classes.  
   - Write comments **sparingly** and only when necessary.  
   - ❌ **Bad:**  
     ```python
     def add(a, b):  # This function adds two numbers
         return a + b
     ```
   - ✅ **Good:**  
     ```python
     def add(a, b):
         """Return the sum of two numbers."""
         return a + b
     ```

### 13. **Avoid Mutable Default Arguments**  
   - Default arguments should **not** be mutable (like lists or dictionaries) to prevent unexpected behavior.  
   - ❌ **Bad:**  
     ```python
     def add_item(item, items=[]):  # Dangerous!
         items.append(item)
         return items
     ```
   - ✅ **Good:**  
     ```python
     def add_item(item, items=None):
         if items is None:
             items = []
         items.append(item)
         return items
     ```

### 14. **Use Meaningful Variable Names**  
   - Avoid single-letter variables (except in loops or mathematical expressions).  
   - ❌ **Bad:**  
     ```python
     x = 10  # What is 'x'?
     ```
   - ✅ **Good:**  
     ```python
     user_age = 10  
     ```

### 15. **Avoid Multiple Statements on One Line**  
   - Write **one statement per line** for better readability.  
   - ❌ **Bad:**  
     ```python
     if x > 0: print("Positive")  # Avoid
     ```
   - ✅ **Good:**  
     ```python
     if x > 0:
         print("Positive")
     ```

---

# PEP 257: Docstring Conventions for Better Documentation

PEP 257 provides conventions for writing docstrings in Python, ensuring better documentation and readability.

## 1. **What is a Docstring?**
A docstring is a **string literal** used to document a module, class, function, or method.

```python
"""This is a module-level docstring."""

def example_function():
    """This is a function-level docstring."""
    pass
```

## 2. **General Guidelines**
- Use **triple double-quotes** (`"""`), even for one-liners.
- The docstring should be the **first statement** in the module, function, or class.
- Keep lines **≤72 characters** for readability.
- Use **complete sentences** and end with a period (`.`).

## 3. **Module Docstrings**
- Describe the module’s purpose.
- List any dependencies or usage notes.

```python
"""Utility functions for data processing.

This module provides helper functions for data validation and transformation.
"""
```

## 4. **Class Docstrings**
- Describe the class purpose and attributes.

```python
class Car:
    """A class representing a car.
    
    Attributes:
        make (str): The manufacturer of the car.
        model (str): The model of the car.
        year (int): The year of manufacture.
    """
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
```

## 5. **Function and Method Docstrings**
- Describe what the function does.
- List parameters and return values.

```python
def add(a, b):
    """Return the sum of two numbers.
    
    Args:
        a (int): First number.
        b (int): Second number.
    
    Returns:
        int: The sum of `a` and `b`.
    """
    return a + b
```

## 6. **One-Line vs. Multi-Line Docstrings**
- **One-liner:** For simple functions.

```python
def square(n):
    """Return the square of a number."""
    return n * n
```

- **Multi-line:** For detailed explanations.

```python
def divide(a, b):
    """Divide two numbers and return the result.
    
    This function returns `a / b`. If `b` is zero, it raises a `ZeroDivisionError`.
    
    Args:
        a (int): Numerator.
        b (int): Denominator.
    
    Returns:
        float: The result of division.
    
    Raises:
        ZeroDivisionError: If `b` is zero.
    """
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero.")
    return a / b
```

## 7. **Docstrings for Special Methods**
- Document special methods like `__init__`.

```python
class Animal:
    """A class representing an animal."""
    
    def __init__(self, name):
        """Initialize the animal with a name.
        
        Args:
            name (str): The name of the animal.
        """
        self.name = name
```

## 8. **Consistent Formatting**
- Use indentation and spacing properly.
- Maintain a uniform style across all docstrings.

---

# Type Hinting: Using PEP 484 and PEP 526 for Type Safety

Python introduced type hinting in **PEP 484** and **PEP 526** to improve code readability, maintainability, and error detection. Type hints help developers understand expected data types and enable static analysis tools to catch potential bugs early.

---

## **PEP 484: Type Hints**

PEP 484 introduced **type hints** to annotate function signatures, variables, and return types. It allows for **optional static typing** while keeping Python dynamically typed.

### **Basic Syntax**

```python
# Function with type hints
def add(x: int, y: int) -> int:
    return x + y
```

- `x: int` and `y: int` indicate that both parameters should be integers.
- `-> int` specifies that the function returns an integer.

### **Using Built-in Types**

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"
```

### **Optional and Union Types**

Use `Optional` or `Union` from `typing` for multiple possible types.

```python
from typing import Optional, Union

def get_length(data: Union[str, list]) -> int:
    return len(data)

def fetch_data(user_id: int) -> Optional[str]:
    if user_id == 1:
        return "User Data"
    return None  # Could return `None`, so we use Optional
```

### **Using Lists, Tuples, and Dicts**

```python
from typing import List, Tuple, Dict

def process_numbers(numbers: List[int]) -> Tuple[int, int]:
    return min(numbers), max(numbers)

def get_user_info() -> Dict[str, str]:
    return {"name": "Alice", "role": "Admin"}
```

### **Callable and Any**

- `Callable` defines function signatures.
- `Any` allows any type.

```python
from typing import Callable, Any

def apply_function(func: Callable[[int, int], int], x: int, y: int) -> int:
    return func(x, y)

def unknown_function(data: Any) -> Any:
    return data
```

---

## **PEP 526: Variable Annotations**

PEP 526 introduced **variable annotations** for specifying types outside of functions.

### **Example Usage**

```python
name: str = "Alice"
age: int = 30
scores: List[int] = [85, 90, 95]
```

This improves readability and helps static analysis tools detect errors.

---

## \*\*Type Checking with \*\***`mypy`**

To enforce type checking, use **`mypy`**:

```sh
pip install mypy
mypy script.py
```

Errors will be reported if types don't match the annotations.

---

# Naming Conventions: Best Practices for Variables, Functions, and Classes

Consistent naming conventions improve code readability, maintainability, and collaboration. Following best practices ensures that your code is understandable by both humans and machines.

---

## **1. Variable Naming**

- Use **lowercase_with_underscores** (snake_case) for variables.
- Choose meaningful and descriptive names.
- Avoid using single-character variable names (except for loop counters, e.g., `i`, `j`).

### **Examples:**
```python
user_name = "Alice"
max_retries = 5
```

### **Constants**
- Use **UPPERCASE_WITH_UNDERSCORES** for constants.
- Constants should be defined at the top of the file or inside a separate config file.

```python
MAX_CONNECTIONS = 100
API_KEY = "your_api_key_here"
```

---

## **2. Function Naming**

- Use **lowercase_with_underscores** for function names.
- Function names should be verbs or action-based to indicate behavior.
- Avoid abbreviations unless they are commonly understood.

### **Examples:**
```python
def calculate_total(price: float, tax: float) -> float:
    return price + (price * tax)

def send_email(recipient: str, subject: str) -> None:
    print(f"Sending email to {recipient} with subject: {subject}")
```

---

## **3. Class Naming**

- Use **PascalCase** (also known as UpperCamelCase) for class names.
- Class names should be nouns and represent objects or entities.

### **Examples:**
```python
class UserProfile:
    def __init__(self, name: str, age: int):
        self.name = name
        self.age = age

class OrderProcessor:
    def process_order(self, order_id: int) -> None:
        print(f"Processing order: {order_id}")
```

---

## **4. Method & Attribute Naming**

- Use **lowercase_with_underscores** for methods and attributes.
- Private methods or attributes should start with an underscore (`_`), indicating they are intended for internal use.

### **Examples:**
```python
class DatabaseConnection:
    def __init__(self, db_url: str):
        self._db_url = db_url  # Private attribute

    def connect(self) -> None:
        print(f"Connecting to {self._db_url}")
```

---

## **5. Module & Package Naming**

- Use **lowercase_with_underscores** for module names.
- Package names should also be **lowercase** but can be single words without underscores.

### **Examples:**
```
project_root/
    ├── data_processing.py  # Module
    ├── user_auth.py        # Module
    ├── analytics/         # Package
    │   ├── reports.py     # Module
    │   ├── trends.py      # Module
```

---

## **6. Exception Naming**

- Use **PascalCase** and end with "Error" for exception classes.

### **Examples:**
```python
class InvalidInputError(Exception):
    pass

class DatabaseConnectionError(Exception):
    pass
```

---

## **7. Boolean & Flag Naming**

- Use `is_`, `has_`, `can_`, or `should_` prefixes for boolean variables and functions.

### **Examples:**
```python
is_logged_in = False
has_permission = True

def can_execute_command(user_role: str) -> bool:
    return user_role == "admin"
```

---

## **8. Underscore Conventions**

- `_single_leading_underscore`: Internal/private attributes and methods.
- `__double_leading_underscore`: Name mangling (not commonly used).
- `single_trailing_underscore_`: Used to avoid conflicts with Python keywords.

### **Examples:**
```python
class Example:
    def __init__(self):
        self._internal_value = 42  # Private attribute
        self.class_ = "example"  # Avoids conflict with Python keyword 'class'
```

---

 

