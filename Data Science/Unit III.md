## 3.1 Introduction to NumPy

- **NumPy (Numerical Python)** is an open source Python library widely used in science and engineering.
- It offers a multidimensional array object with outstanding capabilities and speed for interacting with these arrays.

#### Why Use NumPy?
1. **Faster Execution:** NumPy arrays are optimized for complex mathematical and statistical operations. Operations on NumPy arrays are up to 50x faster than iterating over native Python lists using loops.
2. **Compatibility with Various Libraries:** NumPy works with libraries like Pandas, SciPy, scikit-learn, etc.

#### Installing and Importing NumPy in Python:
- **Installing NumPy:**
  - Install NumPy using `conda install numpy` or `pip install numpy` if you already have Python.
  - Use Anaconda for a simpler start if Python is not installed.
  - Run `pip install numpy` in the command prompt or terminal to download and install the latest version of NumPy from PyPI.

- **Importing NumPy:**
  - Import NumPy in Python as `np`.
  - It’s a common convention to improve readability: `import numpy as np`.

#### NumPy Array Operations and Methods:
1. **Creating One-Dimensional Arrays:**
```python
import numpy as np
array = np.arange(20)
```
Output: 
$$ \begin{matrix}
array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19])
\end{matrix} $$

2. **Creating Two-Dimensional Arrays:**
```python
array = np.arange(20).reshape(4, 5)
```
Output: 
$$ \begin{matrix}
array ([[0, &1, &2, &3, &4], \\ 
\hspace{15mm} [5, &6, &7, &8, &9], \\ 
\hspace{17mm} [10, &11, &12, &13, &14], \\ 
\hspace{17mm} [15, &16, &17, &18, &19]]) 
\end{matrix} $$


#### Other NumPy Functions:
- `np.empty((2, 3))` - Creates a 2 x 3 array of random numbers.
- `np.full((2,2), 3)` - Create a 2 x 2 array with each element as $3$.
- `np.eye(3,3)` - Makes a 3x3 _Identity matrix_ with 1’s along the diagonal and 0’s everywhere else.
- `np.linspace(0, 10, num=4)` - Creates an array of 4 equally spaced numbers between 0 and 10.
- `empty_like()` - Creates a new array with the same shape as another array, but with random, uninitialized values.
- `ones_like()` - Creates a new array with the same shape as another array, filled with 1s.
- `zeros_like()` - Creates a new array with the same shape as another array, filled with 0s.
- `full_like()` - Creates a new array with the same shape as another array, filled with a specific value.
- `asarray()` - Converts an existing list (or other data) into a NumPy array.
- `geomspace()` - Generates numbers spaced evenly on a logarithmic scale.
- `copy()` - Makes a copy of an array.
- `diag()` - Creates or extracts the diagonal from a matrix.
- `frombuffer()` - Converts binary data (a stream of bytes) into an array.
- `fromfile()` - Reads data from a file and turns it into an array.
- `bmat()` - Builds a large array by combining smaller arrays (blocks).
- `mat()` - Converts data into a matrix (a special 2D array).
- `vander()` - Creates a Vandermonde matrix (useful in polynomial equations).
- `triu()` - Returns the upper triangular part of a matrix (everything below the diagonal is 0).
- `tril()` - Returns the lower triangular part of a matrix (everything above the diagonal is 0).
- `tri()` - Creates a matrix with 1s in the lower triangle and 0s elsewhere.
- `diagflat()` - Creates a diagonal array with specified values on the diagonal.
- `fromfunction()` - Creates an array based on a function for each element’s coordinates.
- `logspace()` - Creates numbers spaced evenly on a logarithmic scale.
- `meshgrid()` - Creates coordinate matrices for plotting (used for 3D plots).

## 3.2 Activity - Sequence it Right

#### Sequence in Python using NumPy:
- The `sort()` method sorts an array in ascending order.
- Syntax: 
  ```python
  numpy.sort(arr, axis=-1, kind=None, order=None)
  ```
#### Parameters:
1. **arr:** Input array to sort.
2. **axis:** Axis along which sorting is performed. Default is `-1` (last axis).
3. **order:** Specifies fields to compare first if array is structured.
4. **kind:** Sorting algorithm. Default is 'quicksort'. Other options: 'mergesort', 'heapsort'.
###### Program to Get a Sorted NumPy Array (Ascending Order):
```python
import numpy as np
arr = np.array([3, 1, 2])
sorted_arr = np.sort(arr)
print(sorted_arr)
```
###### How to Get a Sorted NumPy Array (Ascending Order):
```python
arr[::-1].sort()

# This sorts the array in ascending order and then reverses it to descending.
```

## 3.3 Demo 01 - Creating and Printing an Array

```python
import numpy as np
```

```Python
# Creating a 1D array
arr_1d = np.array([1, 2, 3, 4, 5])
```

```Python
# Creating an array with a range of values
range_array = np.arange(0, 10, 2)
```

```Python
# Creating a 2D array
arr_2d = np.array([[1, 2, 3], [4, 5, 6]])
```

```Python
# Creating an array with evenly spaced values
linspace_array = np.linspace(0, 1, 5)
```

```Python
# Creating an array of zeros
zeros = np.zeros((3, 3))
```

```Python
# Creating an array of ones
ones = np.ones((2, 4))
```

```Python
# Printing the array
print(arr_1d)
print(arr_2d)
print(zeros)
print(ones)
print(range_array)
print(linspace_array)
```

## 3.4 Class and Attributes of an Array

#### Class of Array:
- NumPy's array class is `ndarray`.
- `ndarray` - N-dimensional array.
- Also known by the alias `array`.
- A fixed-sized array in memory with data of the same type (e.g., integers or floating-point values).

#### Attributes of Array:
- **ndim:** Number of dimensions.
- **size:** Number of elements.
- **dtype:** Datatype of elements.
- **shape:** Size of the array in each dimension.
- **itemsize:** Size (in bytes) of each element.
- **data:** Buffer containing actual elements.

#### Example:
```python
import numpy as np
array1 = np.array([[1, 2, 3], [6, 7, 8]])

print("Array is of type:", type(array1))
print("Shape of array:", array1.shape)
print("No. of dimensions:", array1.ndim)
print("Size of array:", array1.size)
print("Array stores elements of type:", array1.dtype)
print("Data of array1 is:", array1.data)
```

## 3.5 Basic Operations

#### 1. Element-wise Operations:
- NumPy arrays allow element-wise operations, which perform operations like addition, subtraction, etc., on each element.
- **Example**: If you have an array `[1, 2, 3]` and you add `2`, you get `[3, 4, 5]` because you added `2` to each item.

#### 2. Mathematical Functions:
- **Trigonometric Functions:**
  - `np.sin(data)` - Takes each value in `data` and find the sine for it.
  - `np.cos(data)` - Takes each value in `data` and find the cosine for it.
  - `np.tan(data)` - Takes each value in `data` and find the tangent for it.
  - `np.arcsin(data)` - Takes each value in `data` and gives you the angle whose sine is a number.
  - `np.arccos(data)` - Takes each value in `data` and gives you the angle whose cosine is a number.
  - `np.arctan(data)` - Takes each value in `data` and gives you the angle whose tangent is a number.
  - `np.degrees(data)` - Converts angles from radians to degrees.
  - `np.radians(data)` - Converts angles from degrees to radians.

- **Arithmetic Operations:**
  - Addition: `np.add(d1, d2)` - Adds two arrays, `d1` and `d2`, element by element.
  - Subtraction: `np.subtract(d1, d2)` - Subtracts two arrays, `d1` and `d2`, element by element.
  - Multiplication: `np.multiply(d1, d2)` - Multiplies each element of `d1` with the corresponding element of `d2`.
  - Division: `np.divide(d1, d2)` - Divides elements in one array by corresponding elements in another array.
  - Exponentiation: `np.power(d1, d2)` - Raises elements in `d1` to the power of corresponding elements in `d2`.
  - Modulus: `np.mod(d1, d2)` - Finds the remainder when dividing elements of one array by corresponding elements in another array.

- **Rounding Functions:**
  - `np.round(d1, 2)` - Rounds each number to 2 decimal places.
  - `np.floor(d1)` - Makes each number lower, removing the decimal part.
  - `np.ceil(d1)` - Rounds each number up to the next whole number.

#### 3. Array Manipulations:
- **Creating Arrays:** Covered earlier.
- **Reshaping Arrays:** Covered earlier.
- **Concatenating Arrays:**
  ```python
  arr1 = np.array([1, 2, 3])
  arr2 = np.array([4, 5, 6])
  concatenated_arr = np.concatenate((arr1, arr2))
  ```

- **Adding/Removing Elements:**
  - Adding: `np.append(arr, [4, 5])` - Adds items to an existing array.
  - Removing: `np.delete(arr, [0, 2])` - Removes items at given indices.

## 3.6 Activity - Slicing it

#### NumPy Array Slicing:
- Slicing extracts a range of elements from an array.
- Slicing is performed similarly to Python lists.

#### Types of Indexing:
1. **Field Access:** Direct access using index.
2. **Basic Slicing:** `array[start:end:step]`
3. **Advanced Indexing:** Uses arrays of indices or boolean arrays.

##### Basic Slicing Example:
```python
import numpy as np
a

 = np.arange(10)
s = slice(2, 7, 2)
print(a[s])  # Output: [2 4 6]
```

##### Single Item Slicing Example:
```python
import numpy as np
a = np.arange(15)
b = a[7]
print(b)  # Output: 7
```

## 3.7 Mathematical Functions of NumPy

- NumPy supports various mathematical operations and functions for data analysis and scientific computations.
- Includes functions for algebraic, statistical, and trigonometric computations.

#### Common Functions:
- **Algebraic Operations:**
  - `np.add()`, `np.subtract()`, `np.multiply()`, `np.divide()`
- **Statistical Operations:**
  - `np.mean()`, `np.median()`, `np.std()`, `np.var()`
- **Trigonometric Functions:**
  - `np.sin()`, `np.cos()`, `np.tan()`

#### Example of Using Mathematical Functions:
```python
import numpy as np
data = np.array([0, 1, 2])
Sine_data = np.sin(data)
```

## Questions
1. **How do I sort a 2D NumPy array along a specific axis?**
   - To sort a 2D NumPy array along a specific axis, you use the `axis` parameter in `numpy.sort()`. If you set `axis=0`, it will sort along each column; setting `axis=1` will sort each row.
   - **Example:**
     ```python
     arr = np.array([[3, 2, 1], [6, 5, 4]])
     sorted_arr = np.sort(arr, axis=1)  # Sorts each row
     print(sorted_arr)  # Output: [[1, 2, 3], [4, 5, 6]]
     ```

2. **Can a NumPy array be sorted in descending order?**
   - Yes, you can sort a NumPy array in descending order by sorting it in ascending order first and then reversing it.
   - **Example:**
     ```python
     arr = np.array([3, 1, 2])
     arr[::-1].sort()  # First sorts in ascending order, then reverses
     print(arr)  # Output: [3, 2, 1]
     ```

3. **How to sort a 2D NumPy array along a specific axis?**
   - This question is similar to Question 1: you can specify the axis in `numpy.sort()` to sort along rows (`axis=1`) or columns (`axis=0`) in a 2D array.

4. **Can we sort a NumPy array of strings?**
   - Yes, `numpy.sort()` can sort arrays of strings alphabetically.
   - **Example:**
     ```python
     arr = np.array(['banana', 'apple', 'cherry'])
     sorted_arr = np.sort(arr)
     print(sorted_arr)  # Output: ['apple', 'banana', 'cherry']
     ```

5. **Does `numpy.sort()` modify the original array?**
   - No, `numpy.sort()` does not modify the original array. Instead, it returns a new sorted array. If you want to sort in place (modify the original array), you can use the `sort()` method directly on the array, like `arr.sort()`.