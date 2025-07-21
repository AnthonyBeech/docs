# NumPy

NumPy (Numerical Python) is the fundamental package for scientific computing in Python, providing support for large multi-dimensional arrays and mathematical functions.

## Core Features

### N-dimensional Arrays
- **ndarray** - Homogeneous multidimensional array
- Much faster than Python lists for numerical operations
- Foundation for most data science libraries
- Supports broadcasting for efficient operations

### Universal Functions (ufuncs)
- Vectorized functions operating on arrays
- Element-wise operations
- Mathematical, logical, and comparison functions
- Better performance than pure Python loops

## Array Creation

### Basic Creation
```python
import numpy as np

# From lists
arr = np.array([1, 2, 3, 4, 5])
matrix = np.array([[1, 2], [3, 4]])

# Built-in functions
np.zeros((3, 4))        # Array of zeros
np.ones((2, 3))         # Array of ones
np.full((2, 2), 7)      # Array filled with 7
np.eye(3)               # Identity matrix
```

### Range Functions
```python
np.arange(0, 10, 2)     # [0, 2, 4, 6, 8]
np.linspace(0, 1, 5)    # [0, 0.25, 0.5, 0.75, 1]
np.logspace(0, 2, 3)    # [1, 10, 100]
```

### Random Arrays
```python
np.random.seed(42)              # Set seed for reproducibility
np.random.rand(3, 4)            # Uniform [0, 1)
np.random.randn(3, 4)           # Standard normal
np.random.randint(0, 10, (3, 4)) # Random integers
np.random.choice([1, 2, 3], 5)  # Random choice
```

## Array Properties

### Shape and Size
```python
arr.shape       # Dimensions
arr.size        # Total number of elements
arr.ndim        # Number of dimensions
arr.dtype       # Data type
arr.itemsize    # Size of each element in bytes
```

### Reshaping
```python
arr.reshape(3, 4)       # Change shape
arr.flatten()           # 1D array
arr.ravel()             # 1D view (if possible)
arr.T                   # Transpose
np.transpose(arr)       # Transpose
```

## Array Indexing and Slicing

### Basic Indexing
```python
arr[0]          # First element
arr[-1]         # Last element
arr[1:4]        # Slice
arr[::2]        # Every second element

# 2D arrays
matrix[0, 1]    # Row 0, column 1
matrix[0, :]    # First row
matrix[:, 1]    # Second column
```

### Boolean Indexing
```python
mask = arr > 5
arr[mask]               # Elements greater than 5
arr[arr > 5]            # Same as above
arr[(arr > 2) & (arr < 8)]  # Multiple conditions
```

### Fancy Indexing
```python
indices = [0, 2, 4]
arr[indices]            # Select specific indices
arr[[0, 2], [1, 3]]     # Select specific coordinates
```

## Mathematical Operations

### Basic Arithmetic
```python
arr + 5         # Add scalar
arr * 2         # Multiply by scalar
arr1 + arr2     # Element-wise addition
arr1 * arr2     # Element-wise multiplication
arr1 @ arr2     # Matrix multiplication
np.dot(arr1, arr2)  # Matrix multiplication
```

### Mathematical Functions
```python
np.sqrt(arr)        # Square root
np.exp(arr)         # Exponential
np.log(arr)         # Natural logarithm
np.sin(arr)         # Sine
np.cos(arr)         # Cosine
np.abs(arr)         # Absolute value
```

### Aggregation Functions
```python
np.sum(arr)         # Sum of all elements
np.mean(arr)        # Mean
np.std(arr)         # Standard deviation
np.min(arr)         # Minimum
np.max(arr)         # Maximum
np.argmin(arr)      # Index of minimum
np.argmax(arr)      # Index of maximum
```

### Axis-based Operations
```python
# For 2D arrays
arr.sum(axis=0)     # Sum along rows (column sums)
arr.sum(axis=1)     # Sum along columns (row sums)
arr.mean(axis=0)    # Mean along rows
np.cumsum(arr)      # Cumulative sum
```

## Broadcasting

Broadcasting allows operations between arrays of different shapes:

```python
# Broadcasting examples
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

# Add scalar to array
result = arr + 10

# Add 1D array to 2D array
row = np.array([1, 0, -1])
result = arr + row

# Add column vector
col = np.array([[1], [2]])
result = arr + col
```

## Linear Algebra

### Common Operations
```python
# Matrix operations
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

np.dot(A, B)            # Matrix multiplication
A @ B                   # Matrix multiplication (Python 3.5+)
np.linalg.inv(A)        # Matrix inverse
np.linalg.det(A)        # Determinant
np.linalg.eig(A)        # Eigenvalues and eigenvectors
```

### Solving Linear Systems
```python
# Solve Ax = b
A = np.array([[3, 1], [1, 2]])
b = np.array([9, 8])
x = np.linalg.solve(A, b)

# Least squares solution
x = np.linalg.lstsq(A, b, rcond=None)[0]
```

## Data Types

### Common Data Types
```python
np.int32        # 32-bit integer
np.int64        # 64-bit integer
np.float32      # 32-bit float
np.float64      # 64-bit float (default)
np.bool_        # Boolean
np.complex128   # Complex number
```

### Type Conversion
```python
arr.astype(np.float32)      # Convert to float32
arr.astype('int64')         # Convert to int64
arr.astype(bool)            # Convert to boolean
```

## Performance Tips

### Vectorization
```python
# Slow (Python loop)
result = []
for x in arr:
    result.append(x ** 2)

# Fast (vectorized)
result = arr ** 2

# Use NumPy functions instead of math module
np.sqrt(arr)    # Instead of [math.sqrt(x) for x in arr]
```

### Memory Layout
```python
# C-order (row-major) vs Fortran-order (column-major)
arr_c = np.array([[1, 2], [3, 4]], order='C')
arr_f = np.array([[1, 2], [3, 4]], order='F')

# Check memory layout
arr.flags['C_CONTIGUOUS']
arr.flags['F_CONTIGUOUS']
```

### Views vs Copies
```python
# Views (share memory)
view = arr[1:3]         # Slice creates view
view = arr.reshape(2, 3) # Reshape may create view

# Copies (new memory)
copy = arr.copy()       # Explicit copy
copy = arr[arr > 5]     # Boolean indexing creates copy
```

## Common Patterns

### Normalization
```python
# Z-score normalization
normalized = (arr - np.mean(arr)) / np.std(arr)

# Min-max normalization
normalized = (arr - np.min(arr)) / (np.max(arr) - np.min(arr))
```

### Finding Unique Values
```python
unique_vals = np.unique(arr)
vals, counts = np.unique(arr, return_counts=True)
vals, indices = np.unique(arr, return_index=True)
```

### Conditional Operations
```python
# Where function
result = np.where(arr > 5, arr, 0)  # Keep values > 5, else 0
result = np.where(arr > 5, 'high', 'low')  # Conditional assignment

# Select function
conditions = [arr < 0, arr == 0, arr > 0]
choices = ['negative', 'zero', 'positive']
result = np.select(conditions, choices)
```

## Integration with Other Libraries

### Pandas
```python
import pandas as pd

# NumPy array to pandas
df = pd.DataFrame(arr)
series = pd.Series(arr)

# Pandas to NumPy
arr = df.values
arr = df.to_numpy()
```

### Matplotlib
```python
import matplotlib.pyplot as plt

x = np.linspace(0, 2*np.pi, 100)
y = np.sin(x)
plt.plot(x, y)
```

## Best Practices

### Code Style
- Use descriptive variable names
- Prefer vectorized operations over loops
- Use appropriate data types to save memory
- Document array shapes in comments

### Performance
- Avoid unnecessary copies
- Use in-place operations when possible
- Preallocate arrays when size is known
- Profile code to identify bottlenecks

### Memory Management
- Use views instead of copies when possible
- Delete large arrays when no longer needed
- Use memory-efficient data types
- Monitor memory usage in long-running processes

## Resources

- [NumPy Documentation](https://numpy.org/doc/)
- [NumPy Quickstart Tutorial](https://numpy.org/doc/stable/user/quickstart.html)
- [NumPy for MATLAB Users](https://numpy.org/doc/stable/user/numpy-for-matlab-users.html)
- [SciPy Lecture Notes](https://scipy-lectures.org/)