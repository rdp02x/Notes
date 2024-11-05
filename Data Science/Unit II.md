## 2.1 Installation of Anaconda Python Distribution

## 2.2 Data Types with Python

### Numeric Data Types
Numeric data types represent numeric values and can be any number from negative infinity to positive infinity. They are subdivided into three types:

1. **Integer**
   - **Description**: Holds integral values.
   - **Example**:
     ```python
     var1 = int(input('Enter the integer value: '))
     var2 = 2
     print(var1)
     print(var2)
     ```
   - **Use Case**: Commonly used in programming for loop indices and other operations involving whole numbers.

2. **Float**
   - **Description**: Holds decimal values.
   - **Example**:
     ```python
     var1 = float(input('Enter the float value: '))
     var2 = 23.123123
     print(var1)
     print(var2)
     ```
   - **Use Case**: Used for precise calculations that require decimal points.

3. **Complex Number**
   - **Description**: Stores complex numbers, which consist of a real part and an imaginary part.
   - **Example**:
     ```python
     var1 = complex(input('Enter the complex value: '))
     var2 = 2 + 56j
     print(var1)
     print(var2)
     ```
   - **Use Case**: Useful in advanced mathematical calculations.

### Other Data Types

1. **Dictionary**
   - **Description**: An unordered collection of key-value pairs.
   - **Example**:
     ```python
     dictionary = {'Name': 'Rin', 'Contact': 875597, 1: 'id_no'}
     print(dictionary)
     print(dictionary.keys())
     print(dictionary.values())
     ```

2. **Boolean**
   - **Description**: Stores `True` or `False` values.
   - **Example**:
     ```python
     if True:
         print('I am always True')
     else:
         print('I am False')
     
     i = 1
     while i == True:
         print('I am True')
         i = 0
     ```

3. **Set**
   - **Description**: Stores non-repeating values in an unordered collection.
   - **Example**:
     ```python
     Set = set([1, 2, 3, 4, 3, 1, 6])
     print(Set)
     if 1 in Set:
         print('True')
     ```

4. **Sequence**
   - **Description**: A collection of data of same or different types.
   - **Subtypes**:
     - **List**: Ordered, mutable collection.
       - **Example**:
         ```python
         List = [1, 2, 3, 4, 2, 1]
         print(List)
         print(type(List))
         ```
     - **String**: Immutable sequence of characters.
       - **Example**:
         ```python
         STRING = "Have a Good Day"
         print(STRING)
         STR = str(input('Enter the string: '))
         print(STR)
         ```
     - **Tuple**: Immutable sequence of elements.
       - **Example**:
         ```python
         Tuple = (1, 2, 3, 1, 2)
         print(Tuple)
         print(type(Tuple))
         ```

## 2.3 Basic Operators in Python

### Arithmetic Operators
- **Addition (`+`)**: Adds values.
  - **Example**: `a + b`
- **Subtraction (`-`)**: Subtracts values.
  - **Example**: `a - b`
- **Multiplication (`*`)**: Multiplies values.
  - **Example**: `a * b`
- **Division (`/`)**: Divides values.
  - **Example**: `b / a`
- **Modulus (`%`)**: Returns remainder of division.
  - **Example**: `b % a`
- **Exponentiation (`**`)**: Raises to a power.
  - **Example**: `a ** b`
- **Floor Division (`//`)**: Division resulting in the quotient without remainder.
  - **Example**: `9 // 2`

### Comparison Operators
- **Equal (`==`)**: Checks if values are equal.
  - **Example**: `(a == b)`
- **Not Equal (`!=`)**: Checks if values are not equal.
  - **Example**: `(a != b)`
- **Greater Than (`>`)**: Checks if left operand is greater.
  - **Example**: `(a > b)`
- **Less Than (`<`)**: Checks if left operand is less.
  - **Example**: `(a < b)`
- **Greater Than or Equal (`>=`)**: Checks if left operand is greater or equal.
  - **Example**: `(a >= b)`

### Membership Operators
- **In (`in`)**: Checks if value exists in sequence.
  - **Example**: `x in y`
- **Not In (`not in`)**: Checks if value does not exist in sequence.
  - **Example**: `x not in y`

### Identity Operators
- **Is (`is`)**: Checks if variables point to the same object.
  - **Example**: `x is y`
- **Is Not (`is not`)**: Checks if variables do not point to the same object.
  - **Example**: `x is not y`

## 2.4 Python Functions

### Function Basics
- **Definition**: A block of code that performs a specific task.
- **Rules**:
  1. Must start with a letter or an underscore.
  2. Should be lowercase.
  3. Can include numbers but should not start with one.
  4. Can be of any length.
  5. Name should not be a Python keyword.
  6. Use underscores to separate words.
  7. No spaces between words.

### Types of Functions

1. **Built-in Functions**
   - **Description**: Predefined functions provided by Python.
   - **Examples**:
     - `abs(value)`: Returns the absolute value.
       - **Example**:
         ```python
         num = abs(-5.45)
         print(num)  # Output: 5.45
         ```
     - `bin(n)`: Returns binary representation of an integer.
       - **Example**:
         ```python
         num = bin(24)
         print(num)  # Output: 0b11000
         ```
     - `float(n)`: Converts to a floating-point number.
       - **Example**:
         ```python
         num = float(5)
         print(num)  # Output: 5.0
         ```
     - `pow(x, y)`: Returns x raised to the power y.
       - **Example**:
         ```python
         import math
         pw_num = math.pow(4, 2)
         print(pw_num)  # Output: 16.0
         ```
     - `factorial(x)`: Returns the factorial of x.
       - **Example**:
         ```python
         import math
         fact_num = math.factorial(5)
         print(fact_num)  # Output: 120
         ```

2. **User-Defined Functions**
   - **Definition**: Functions created by users to perform specific tasks.
   - **Syntax**:
     ```python
     def function_name(parameters):
         # function body
         return result
     ```

If you need any more details or adjustments, just let me know!
