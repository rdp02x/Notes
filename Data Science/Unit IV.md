### 4.1 Introduction to SciPy

- **Overview:** SciPy is a free, open-source library in Python designed for scientific and mathematical computations. It extends NumPy and provides additional functionality for mathematical calculations, data manipulation, and visualization.
  
- **Advantages:**
  1. **Open-source:** Freely available for use and modification.
  2. **Ease of Use:** User-friendly and efficient for various computational tasks.
  3. **High-Level Commands:** Includes tools for data visualization and manipulation.
  4. **Support for Parallel Programming:** Includes classes and routines that assist with parallel processing.

- **Installation:**
  1. **Using pip:**
     ```bash
     pip install scipy
     ```
  2. **Using Anaconda:**
     ```bash
     conda install -c anaconda scipy
     ```

- **Importing SciPy:**
  ```python
  import scipy
  ```

### 4.2 SciPy Sub Packages

**1. cluster:** Cluster algorithms like vector quantization and K-means.

**2. constants:** Physical and mathematical constants.

**3. fftpack:** Algorithms for computing Fourier transforms.

**4. integrate:** Integration routines.

**5. interpolation:** Tools for interpolation and smoothing splines.

**6. io:** Input and output tools for data.

**7. lib:** Wrapper to external libraries.

**8. linalg:** Routines for linear algebra.

**9. misc:** Miscellaneous tools for reading and writing images.

**10. ndimage:** N-dimensional image processing.

**11. odr:** Orthogonal distance regression.

**12. optimize:** Optimization algorithms.

**13. signal:** Tools for signal processing.

**14. sparse:** Sparse matrices and related routines.

**15. spatial:** Spatial data structures and algorithms.

**16. special:** Special mathematical functions.

**17. stats:** Statistical functions and distributions.

**18. weave:** Deprecated package for embedding C++/C code.

### 4.3 SciPy Sub Package: Integration and Optimization

**1. Clustering Algorithms:**
   - **K-Means Clustering:**
     - **Definition:** An unsupervised algorithm that partitions data into clusters by minimizing the variance within each cluster.
     - **Steps:**
       1. Choose K initial centroids.
       2. Assign each data point to the nearest centroid.
       3. Update centroids to the mean of assigned points.
       4. Repeat steps 2 and 3 until convergence.

   - **Functions:**
     - **`cluster.vq.whiten()`:** Normalizes data points.
     - **`cluster.vq.kmeans()`:** Performs K-means clustering with convergence threshold.
     - **`cluster.vq.kmeans2()`:** Performs K-means clustering without convergence threshold.
     - **`cluster.vq.vq()`:** Maps observations to centroids.

**2. Hierarchical Clustering:**
   - Provides methods for hierarchical clustering and visualization of clusters.

**3. FFT (Fast Fourier Transform):**
   - **Purpose:** Converts spatial data to frequency data.
   - **Functions:** Use `scipy.fftpack` for computing FFT.

**4. Integration:**
   - **Purpose:** Contains functions for calculating integrals.
   - **Function:** Use `scipy.integrate` for various integration tasks.

### 4.4 Demo: Calculating Eigenvalues and Eigenvectors

- **Linear Algebra with SciPy:**
  - **Functions:**
    - **`scipy.linalg.eig()`:** Computes eigenvalues and eigenvectors.
    - **`scipy.linalg.det()`:** Computes the determinant of a matrix.
    - **`scipy.linalg.solve()`:** Solves linear equations.

  ```python
  from scipy import linalg
  import numpy as np

  A = np.array([[2, 1, -2], [1, 0, 0], [0, 1, 0]])
  values, vectors = linalg.eig(A)

  # Determinant
  A = np.array([[1, 2, 9], [3, 4, 8], [7, 8, 4]])
  det = linalg.det(A)

  # Solving Linear Equations
  a = np.array([[1, 2, -3], [2, -5, 4], [5, 4, -1]])
  b = np.array([[-3], [13], [5]])
  x = linalg.solve(a, b)
  ```

### 4.5 SciPy Sub Package: Statistics, Weave, and IO

**1. SciPy IO:**
   - Handles various file formats (e.g., MATLAB, NetCDF).

**2. SciPy Ndimage:**
   - Provides functions for image processing (e.g., filtering, segmentation).

**3. SciPy Stats:**
   - **Functions:**
     - **`rv_continuous`:** Base class for continuous distributions.
     - **`rv_discrete`:** Base class for discrete distributions.
     - **`rv_histogram`:** Distribution based on histograms.

**4. SciPy Weave:**
   - Deprecated package for including C/C++ code. Replaced by other tools like Cython.

### 4.6 Performing CDF and PDF Using SciPy

- **Probability Density Function (PDF):**
  - **Function:** `scipy.stats.norm.pdf(x, loc=0, scale=1)`

  ```python
  from scipy.stats import norm
  import numpy as np
  import matplotlib.pyplot as plt

  x = np.linspace(-5, 5, num=100)
  pdf = norm.pdf(x, loc=0, scale=1)
  plt.plot(x, pdf)
  plt.xlabel('x')
  plt.ylabel('pdf')
  plt.title('Normal Distribution')
  plt.show()
  ```

- **Cumulative Distribution Function (CDF):**
  - **Function:** `scipy.stats.norm.cdf(x, loc=0, scale=1)`

  ```python
  x = np.linspace(-3, 3, num=100)
  cdf = norm.cdf(x)
  plt.plot(x, cdf)
  plt.xlabel('x')
  plt.ylabel('CDF')
  plt.title('CDF of a Standard Normal Distribution')
  plt.show()
  ```
