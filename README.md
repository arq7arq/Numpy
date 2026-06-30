# NumPy Cheat Sheet

This repository/notebook is a beginner-friendly NumPy cheat sheet. It shows the most common NumPy operations for creating arrays, checking array properties, indexing values, changing data, doing math, reshaping arrays, loading data from files, and filtering with boolean masks.

The examples are written in a Jupyter Notebook: `numpy.ipynb`.

## Requirements

Install NumPy and Jupyter before running the notebook:

```bash
pip install numpy notebook
```

Then start Jupyter:

```bash
jupyter notebook
```

Open `numpy.ipynb` and run the cells from top to bottom.

## Import NumPy

```python
import numpy as np
```

`np` is the standard short name used for NumPy.

## Creating Arrays

Create a one-dimensional array:

```python
a = np.array([1, 2, 3], dtype="int16")
print(a)
```

Create a two-dimensional array:

```python
b = np.array([[7.28, 28.7, 3.4], [20, 28, 7]])
print(b)
```

## Checking Array Information

| Operation | Code | Meaning |
| --- | --- | --- |
| Dimensions | `a.ndim` | Number of array dimensions |
| Shape | `a.shape` | Rows, columns, and other dimensions |
| Data type | `a.dtype` | Type of values stored in the array |
| Item size | `a.itemsize` | Size of each item in bytes |
| Number of items | `a.size` | Total number of elements |
| Total memory | `a.nbytes` | Total memory used by the array |

Example:

```python
print(a.ndim)
print(a.shape)
print(a.dtype)
print(a.itemsize)
print(a.size)
print(a.nbytes)
```

## Accessing and Changing Values

Example array:

```python
A = np.array([
    [1, 2, 3, 4, 5, 6, 7],
    [8, 9, 10, 11, 12, 13, 14]
])
```

Get a specific element:

```python
A[0, -1]
```

Get a full row:

```python
A[0, :]
```

Get a full column:

```python
A[:, 1]
```

Get a sub-array using slicing:

```python
A[0:2, 0:7:2]
```

Change one value:

```python
A[1, 1] = 28
```

Change a full row:

```python
A[0, :] = 7
```

Change a full row with different values:

```python
A[0, :] = [1, 2, 3, 4, 5, 6, 7]
```

## Initializing Arrays

Create an array filled with zeros:

```python
np.zeros((3, 4))
```

Create an array filled with ones:

```python
np.ones((2, 3), dtype="int32")
```

Create an array filled with a specific number:

```python
np.full((3, 3), 7)
```

Create an array using the same shape as another array:

```python
np.full_like(A, 28)
```

Create random decimal numbers:

```python
np.random.rand(3, 3)
```

Create random integers:

```python
np.random.randint(7, 29, size=(7, 7))
```

Create an identity matrix:

```python
np.identity(3, dtype="int32")
```

## Array Challenge

Create this matrix without typing every value manually:

```text
1 1 1 1 1
1 0 0 0 1
1 0 9 0 1
1 0 0 0 1
1 1 1 1 1
```

Solution:

```python
output = np.ones((5, 5), dtype="int32")
output[1:-1, 1:-1] = np.zeros((3, 3), dtype="int32")
output[2, 2] = 9
print(output)
```

## Mathematics

NumPy can apply math operations to every element in an array:

```python
a = np.array([1, 2, 3, 4])

print(a + 2)
print(a - 2)
print(a * 2)
print(a / 2)
print(a ** 2)
```

Trigonometry:

```python
print(np.sin(a))
print(np.cos(a))
```

## Linear Algebra

Matrix multiplication:

```python
a = np.ones((2, 3))
b = np.full((3, 4), 2)

np.matmul(a, b)
```

Determinant of a matrix:

```python
c = np.identity(3)
np.linalg.det(c)
```

## Statistics

```python
a = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8]
])

np.min(a)
np.max(a)
np.sum(a)
```

Useful extra functions to try:

```python
np.mean(a)
np.median(a)
np.std(a)
```

## Reorganizing Arrays

Reshape an array:

```python
a = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8]
])

a.reshape((2, 2, 2))
```

Vertically stack arrays:

```python
v1 = np.array([1, 2, 3, 4])
v2 = np.array([4, 5, 6, 8])

np.vstack([v1, v2, v1])
```

Horizontally stack arrays:

```python
h1 = np.ones((2, 4))
h2 = np.zeros((2, 2))

np.hstack((h1, h2))
```

## Loading Data from a File

The notebook expects a comma-separated file named `data.txt`.

```python
file_data = np.genfromtxt("data.txt", delimiter=",")
file_data = file_data.astype("int32")
```

Example `data.txt` format:

```text
1,13,21,11,196
3,42,12,33,766
9,39,32,75,123
```

## Boolean Masking and Advanced Indexing

Check which values match a condition:

```python
file_data > 20
```

Return only values that match a condition:

```python
file_data[file_data < 20]
```

Select specific items using row and column index arrays:

```python
file_data[[0, 1, 2], [1, 3, 4]]
```

This means:

| Row index | Column index |
| --- | --- |
| `0` | `1` |
| `1` | `3` |
| `2` | `4` |

## Main Concepts Practiced

- Creating NumPy arrays
- Checking array shape, size, data type, and memory usage
- Indexing rows, columns, and specific elements
- Slicing arrays
- Updating values inside arrays
- Creating arrays with zeros, ones, full values, random values, and identity matrices
- Performing element-wise math
- Using matrix multiplication and determinants
- Calculating basic statistics
- Reshaping and stacking arrays
- Loading data from text files
- Filtering data with boolean masks
- Using advanced indexing

## Notes

- Use `array[row, column]` for 2D indexing.
- Negative indexes count from the end, so `A[0, -1]` gets the last item in the first row.
- Slicing uses `start:end:step`.
- Many NumPy operations work element by element automatically.
- For file-loading examples, make sure `data.txt` is in the same folder as the notebook.
