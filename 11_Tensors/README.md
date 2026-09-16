
# Tensors

## What are Tensors?

A **tensor** is a mathematical object used to store and represent data in multiple dimensions. In Machine Learning and Deep Learning, tensors are commonly used to represent numbers, vectors, matrices, images, videos, and batches of data.

A tensor is a generalization of scalars, vectors, and matrices to any number of dimensions.

In simple words:

> A tensor is a container that holds numerical data organized into one or more dimensions.

Tensors are the fundamental data structures used in popular Deep Learning frameworks such as:

- TensorFlow
- PyTorch
- JAX

### Why are Tensors Important in Machine Learning?

Tensors are important because they allow ML and Deep Learning models to efficiently store and process data.

Examples:

| Data | Tensor Representation |
|---|---|
| A single number | 0D Tensor |
| A list of numbers | 1D Tensor |
| A table of numbers | 2D Tensor |
| A color image | 3D Tensor |
| A batch of images | 4D Tensor |
| A video batch | 5D Tensor |

---

## Rank, Axes and Shape

To understand tensors, we need to understand three important terms:

1. Rank
2. Axes
3. Shape

### 1. Rank

The **rank** of a tensor is the number of dimensions or axes it has.

For example:

- Scalar → Rank 0
- Vector → Rank 1
- Matrix → Rank 2
- 3D Tensor → Rank 3
- 4D Tensor → Rank 4
- 5D Tensor → Rank 5

> Note: In Machine Learning libraries, rank usually means the number of dimensions of a tensor. This is different from matrix rank in linear algebra.

### 2. Axes

An **axis** is a direction or dimension along which data is organized.

For a 2D tensor:

```python
[
    [1, 2, 3],
    [4, 5, 6]
]
```

There are two axes:

- Axis 0 → Rows
- Axis 1 → Columns

The axis numbering starts from `0`.

### 3. Shape

The **shape** of a tensor tells us how many elements are present along each axis.

For example:

```python
[
    [1, 2, 3],
    [4, 5, 6]
]
```

Shape:

```python
(2, 3)
```

Explanation:

- 2 rows
- 3 columns

### Rank vs Shape vs Axes

| Concept | Meaning | Example |
|---|---|---|
| Rank | Number of dimensions | 2 |
| Axes | Dimensions of the tensor | Axis 0, Axis 1 |
| Shape | Size along each dimension | `(2, 3)` |

---

# 0D Tensors / Scalar

A **0D tensor** is a tensor that contains a single numerical value.

It is also called a **scalar**.

A scalar has:

- Rank: 0
- Number of axes: 0
- Shape: `()`

### Example of 0D Tensor

```python
import numpy as np

scalar = np.array(10)

print(scalar)
print("Rank:", scalar.ndim)
print("Shape:", scalar.shape)
```

Output:

```text
10
Rank: 0
Shape: ()
```

### Another Example

```python
import tensorflow as tf

scalar = tf.constant(10)

print(scalar)
print("Rank:", len(scalar.shape))
print("Shape:", scalar.shape)
```

Output:

```text
tf.Tensor(10, shape=(), dtype=int32)
Rank: 0
Shape: ()
```

### Real-Life Examples

- Age = 20
- Temperature = 30
- Price = 500
- Model loss = 0.25

Each of these can be represented as a scalar.

---

# 1D Tensors / Vector

A **1D tensor** is a tensor containing a sequence of values in a single dimension.

It is commonly called a **vector**.

A 1D tensor has:

- Rank: 1
- Number of axes: 1
- Shape: `(n,)`

Where `n` is the number of elements.

### Example of 1D Tensor

```python
import numpy as np

vector = np.array([10, 20, 30, 40, 50])

print(vector)
print("Rank:", vector.ndim)
print("Shape:", vector.shape)
```

Output:

```text
[10 20 30 40 50]
Rank: 1
Shape: (5,)
```

### Explanation

```python
[10, 20, 30, 40, 50]
```

- Rank = 1
- Shape = `(5,)`
- Contains 5 elements
- Axis 0 contains all 5 values

### Real-Life Examples

A vector can represent:

- Student marks
- A list of ages
- A single feature's values
- Word embedding
- Model weights

Example:

```python
marks = np.array([85, 90, 78, 92])
```

Shape:

```python
(4,)
```

---

# 2D Tensors / Matrices

A **2D tensor** is a tensor arranged in rows and columns.

It is commonly called a **matrix**.

A 2D tensor has:

- Rank: 2
- Number of axes: 2
- Shape: `(rows, columns)`

### Examples of 2D Tensors

```python
import numpy as np

matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(matrix)
print("Rank:", matrix.ndim)
print("Shape:", matrix.shape)
```

Output:

```text
[[1 2 3]
 [4 5 6]]
Rank: 2
Shape: (2, 3)
```

### Explanation

```python
[
    [1, 2, 3],
    [4, 5, 6]
]
```

- Rank = 2
- Shape = `(2, 3)`
- 2 rows
- 3 columns
- Total elements = 2 × 3 = 6

### Axis Representation

| Axis | Meaning |
|---|---|
| Axis 0 | Rows |
| Axis 1 | Columns |

### Real-Life Examples

2D tensors are used to represent:

- Tabular datasets
- Grayscale images
- Feature matrices
- Weight matrices in neural networks
- Student marks tables

Example of a student dataset:

```python
students = np.array([
    [20, 85, 90],
    [21, 78, 88],
    [19, 92, 95]
])
```

Shape:

```python
(3, 3)
```

---

# ND Tensors

An **N-dimensional tensor** is a tensor with N axes.

The letter `N` represents any number of dimensions.

Examples:

| Tensor | Rank | Shape Example |
|---|---:|---|
| Scalar | 0 | `()` |
| Vector | 1 | `(5,)` |
| Matrix | 2 | `(2, 3)` |
| 3D Tensor | 3 | `(2, 3, 4)` |
| 4D Tensor | 4 | `(2, 3, 4, 5)` |
| 5D Tensor | 5 | `(2, 3, 4, 5, 6)` |

As the rank increases, the tensor can represent more complex structures.

---

# Examples of 3D Tensors

A **3D tensor** contains multiple 2D matrices stacked together.

A 3D tensor has:

- Rank: 3
- Number of axes: 3
- Shape: `(depth, rows, columns)`

### Example

```python
import numpy as np

tensor_3d = np.array([
    [
        [1, 2, 3],
        [4, 5, 6]
    ],
    [
        [7, 8, 9],
        [10, 11, 12]
    ]
])

print(tensor_3d)
print("Rank:", tensor_3d.ndim)
print("Shape:", tensor_3d.shape)
```

Output:

```text
[
    [
        [1  2  3]
        [4  5  6]
    ]

    [
        [7  8  9]
        [10 11 12]
    ]
]

Rank: 3
Shape: (2, 2, 3)
```

### Explanation

Shape:

```python
(2, 2, 3)
```

- 2 matrices
- Each matrix has 2 rows
- Each row has 3 columns

Total elements:

```python
2 × 2 × 3 = 12
```

### Real-Life Example: Color Image

A color image can be represented as a 3D tensor.

Typical shape:

```python
(height, width, channels)
```

For example:

```python
(224, 224, 3)
```

Explanation:

- Height = 224 pixels
- Width = 224 pixels
- Channels = 3 (Red, Green, Blue)

> Image layout can vary between frameworks. PyTorch commonly uses `(channels, height, width)` for image tensors.

---

# Examples of 4D Tensors

A **4D tensor** contains data organized across four dimensions.

In Deep Learning, 4D tensors are commonly used to represent a **batch of images**.

A typical image batch shape is:

```python
(batch_size, height, width, channels)
```

### Example

```python
import numpy as np

tensor_4d = np.zeros((2, 3, 4, 5))

print("Rank:", tensor_4d.ndim)
print("Shape:", tensor_4d.shape)
```

Output:

```text
Rank: 4
Shape: (2, 3, 4, 5)
```

### Explanation

Shape:

```python
(2, 3, 4, 5)
```

- 2 images
- Height = 3
- Width = 4
- Channels = 5

Total elements:

```python
2 × 3 × 4 × 5 = 120
```

### Real-Life Example: Batch of RGB Images

For a batch of 32 RGB images, each having a height and width of 224 pixels:

```python
(32, 224, 224, 3)
```

Explanation:

- 32 images
- Height = 224
- Width = 224
- 3 color channels

### TensorFlow Example

```python
import tensorflow as tf

images = tf.random.normal((32, 224, 224, 3))

print("Shape:", images.shape)
print("Rank:", len(images.shape))
```

Output:

```text
Shape: (32, 224, 224, 3)
Rank: 4
```

---

# Examples of 5D Tensors

A **5D tensor** contains data organized across five dimensions.

In Deep Learning, 5D tensors are commonly used for video data or sequences of images.

A typical video batch shape is:

```python
(batch_size, frames, height, width, channels)
```

### Example

```python
import numpy as np

tensor_5d = np.zeros((2, 4, 3, 5, 6))

print("Rank:", tensor_5d.ndim)
print("Shape:", tensor_5d.shape)
```

Output:

```text
Rank: 5
Shape: (2, 4, 3, 5, 6)
```

### Explanation

Shape:

```python
(2, 4, 3, 5, 6)
```

- 2 video samples
- 4 frames per video
- Height = 3
- Width = 5
- Channels = 6

Total elements:

```python
2 × 4 × 3 × 5 × 6 = 720
```

### Real-Life Example: Batch of Videos

Suppose we have:

- 8 videos
- Each video contains 16 frames
- Each frame has a height of 224 pixels
- Each frame has a width of 224 pixels
- Each frame has 3 RGB channels

The tensor shape is:

```python
(8, 16, 224, 224, 3)
```

### TensorFlow Example

```python
import tensorflow as tf

videos = tf.random.normal((8, 16, 224, 224, 3))

print("Shape:", videos.shape)
print("Rank:", len(videos.shape))
```

Output:

```text
Shape: (8, 16, 224, 224, 3)
Rank: 5
```

---

# Tensor Rank Summary

| Tensor Type | Rank | Shape Example | Common Use |
|---|---:|---|---|
| 0D Scalar | 0 | `()` | Single number |
| 1D Vector | 1 | `(5,)` | List of values |
| 2D Matrix | 2 | `(2, 3)` | Tabular data |
| 3D Tensor | 3 | `(2, 3, 4)` | Color image |
| 4D Tensor | 4 | `(32, 224, 224, 3)` | Batch of images |
| 5D Tensor | 5 | `(8, 16, 224, 224, 3)` | Batch of videos |

---

# NumPy Tensor Operations

NumPy is commonly used to create and manipulate tensors.

```python
import numpy as np

# 0D Tensor
tensor_0d = np.array(10)

# 1D Tensor
tensor_1d = np.array([1, 2, 3])

# 2D Tensor
tensor_2d = np.array([
    [1, 2],
    [3, 4]
])

# 3D Tensor
tensor_3d = np.zeros((2, 3, 4))

# 4D Tensor
tensor_4d = np.zeros((2, 3, 4, 5))

# 5D Tensor
tensor_5d = np.zeros((2, 3, 4, 5, 6))

print("0D:", tensor_0d.shape)
print("1D:", tensor_1d.shape)
print("2D:", tensor_2d.shape)
print("3D:", tensor_3d.shape)
print("4D:", tensor_4d.shape)
print("5D:", tensor_5d.shape)
```

Output:

```text
0D: ()
1D: (3,)
2D: (2, 2)
3D: (2, 3, 4)
4D: (2, 3, 4, 5)
5D: (2, 3, 4, 5, 6)
```

---

# Important Tensor Attributes

| Attribute | Meaning |
|---|---|
| `ndim` | Number of dimensions / rank |
| `shape` | Size of each dimension |
| `size` | Total number of elements |
| `dtype` | Data type of elements |
| `reshape()` | Changes the shape without changing the total number of elements |

### Example

```python
import numpy as np

tensor = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print("Rank:", tensor.ndim)
print("Shape:", tensor.shape)
print("Size:", tensor.size)
print("Data Type:", tensor.dtype)
```

Output:

```text
Rank: 2
Shape: (2, 3)
Size: 6
Data Type: int64
```

> The exact default integer dtype may vary by platform and NumPy version.

---

# Key Takeaways

- A tensor is a multidimensional data structure.
- A scalar is a 0D tensor.
- A vector is a 1D tensor.
- A matrix is a 2D tensor.
- Higher-dimensional tensors are used for complex data such as images and videos.
- Rank tells us the number of axes.
- Shape tells us the size of each axis.
- Axes are numbered starting from 0.
- Tensors are essential in Deep Learning frameworks like TensorFlow and PyTorch.
- The total number of elements is the product of all dimensions in the shape.

---

## Conclusion

Tensors are one of the most important concepts in Machine Learning and Deep Learning.

Understanding tensors, rank, axes, and shape helps us work with datasets, images, neural networks, and models efficiently.

