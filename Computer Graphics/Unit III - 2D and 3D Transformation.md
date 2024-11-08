# Unit III - 2D and 3D Transformation

## Transformation

- **Transformation** in computer graphics involves modifying an object's properties, such as position, size, or orientation, by applying specific mathematical rules.
- it is essential for displaying graphics in different positions or forms on a screen.

### Purpose of Transformation:
- **Repositioning:** Move graphics to different locations on the screen.
- **Resizing:** Change the dimensions of graphics.
- **Changing Orientation:** Rotate or flip graphics.

### Basic Types of Transformations:
1. **Translation:** Shifts a graphic from one position to another without altering its size, shape, or orientation.
2. **Rotation:** Rotates a graphic around a specific point, changing its orientation.
3. **Scaling:** Alters the size of a graphic by expanding or contracting it along specified axes.
4. **Shearing:** Skews a graphic, altering its shape by shifting one part in a direction while keeping the other part fixed.
5. **Reflection:** Creates a mirror image of a graphic across a specific line or axis.

### Transformation in a 2D Plane:
- When transformations are applied to objects in a 2D plane (two-dimensional space), it is referred to as **2D Transformation**.
- Each transformation is represented mathematically, using transformation matrices that define how to alter the position or size of graphics.

### Composite Transformation Process
- To achieve complex transformations, multiple transformations can be combined.
- A sequential process helps in building complex transformations by combining simpler ones, enabling more versatile manipulation of graphics.
- The process for performing a **composite transformation** in sequence includes the following steps:

1. **Translation of Coordinates:** First, adjust the object's coordinates by moving it to the desired location.
2. **Rotation of Translated Coordinates:** Next, rotate the translated coordinates to change the orientation of the object.
3. **Scaling of Rotated Coordinates:** Finally, scale the rotated coordinates to resize the object as needed.

## Homogeneous Coordinate System in Computer Graphics
- The **Homogeneous Coordinate System** is a system used in computer graphics to represent points and transformations more effectively, especially when handling multiple transformations in sequence.
- This system allows transformations to be represented in a consistent format, facilitating complex manipulations.
#### 3×3 Transformation Matrix: 
  - In 2D transformations, a 3×3 matrix is often used instead of a 2×2 matrix.
  - The additional dimension (third row and column) enables a more flexible representation of transformations, such as translation, scaling, and rotation.
##### Conversion from 2×2 to 3×3 Matrix:
  - To convert a 2×2 transformation matrix into a 3×3 matrix, an extra coordinate, often referred to as the "dummy" coordinate, $W$, is added.
  - This allows for more complex operations by embedding translation along with rotation and scaling in the same transformation.
#### Representation of Points in Homogeneous Coordinates:
- Any point in 2D space, originally represented by two coordinates$P(X, Y)$, can be converted into a **homogeneous coordinate** form by adding an additional coordinate:
  - The point $P(X, Y)$ becomes $P'(X_h, Y_h, h)$in homogeneous coordinates, where $h$ is a non-zero scalar, typically set to 1 for simplicity.
  - Homogeneous coordinates allow for all transformation operations (like translation, scaling, rotation) to be represented as matrix multiplications.
  - Example:
  - Cartesian point $P(X, Y)$ in Cartesian coordinates becomes $P'(X_h, Y_h, h)$, where $X_h = X \times h$and $Y_h = Y \times h$.

## Translation

- **Translation** in computer graphics is the process of shifting an object or point from one location to another on the screen. 
- The distance and direction of this shift are determined by a specified translation vector.
- It moves an object to a new position by adjusting its coordinates.
- It is used to relocate objects on the screen without altering their shape, size, or orientation.
#### Translation in 2D:
- In a 2D plane, a point’s position can be shifted by adding the translation distances $t_x$ and $t_y$ to the original coordinates.
- Given a point $P(X, Y)$, its new translated position $P'(X', Y')$ is calculated as:
  - $X' = X + t_x$
  - $Y' = Y + t_y$
- Here, $(t_x, t_y)$ is called the **translation vector** or **shift vector**.
#### Matrix Representation of Translation:
- Translation can also be represented using matrix notation, which is useful for performing transformations on multiple points or objects efficiently.
- This provides a straightforward way to compute the new position of points after translation by adding the translation vector to the original coordinates.

1. Column Vector Representation:
   - Original point $P$ in column vector form:
```math
$$P = \begin{bmatrix} X \\ Y \end{bmatrix}$$
```
   - Translated point $P'$: 
```math
$$P' = \begin{bmatrix} X' \\ Y' \end{bmatrix}$$
```
2. Translation Vector $T$**:
```math
$$T = \begin{bmatrix} t_x \\ t_y \end{bmatrix}$$
```
3. Transformation Equation:
   $P' = P + T$

## Rotation

- **Rotation** is a transformation that rotates a point or an object around a specified axis, often around the origin in a 2D plane. 
- This operation is defined by an angle $\theta$ which determines the extent of the rotation.
- The angle $\theta$ represents the degree by which the object is rotated. (i.e the **Angle of Rotation**)
- For simplicity, objects are typically rotated around the origin $(0,0)$ in a 2D plane.
  This coordinate is called **Origin of Rotation**.
#### How Rotation Works with Coordinates:
- Imagine a point $P(X, Y)$ located at a certain angle $\phi$ from the x-axis and a distance $r$ from the origin.

1. **Starting Coordinates of Point $P(X, Y)$**:
   - $X = r \cdot \cos(\phi)$
   - $Y = r \cdot \sin(\phi)$
   - Here, $r$ is the distance from the origin, and $\phi$ is the angle of the point from the x-axis.

2. **New Coordinates After Rotation**:
   - When the point rotates by an angle $\theta$, its new position $P'(X', Y')$ is calculated as: 
     - $X' = X \cdot \cos(\theta) - Y \cdot \sin(\theta)$ 
     - $Y' = X \cdot \sin(\theta) + Y \cdot \cos(\theta)$ 

#### Rotation Using a Matrix:
Rotation can be done more easily using matrices. This is helpful when rotating multiple points.

1. **Rotation Matrix**:
   - To rotate by an angle $\theta$, we use the rotation matrix:
```math
$$R = \begin{bmatrix} \cos(\theta) & -\sin(\theta) \\ \sin(\theta) & \cos(\theta) \end{bmatrix}$$ 
```
2. **Applying the Matrix to Rotate a Point**:
   - Multiply the point’s coordinates $P(X, Y)$ by the rotation matrix $R$ to get the new coordinates $P'(X', Y')$:
```math
$$\begin{bmatrix} X' \\ Y' \end{bmatrix} = \begin{bmatrix} \cos(\theta) & -\sin(\theta) \\ \sin(\theta) & \cos(\theta) \end{bmatrix} \begin{bmatrix} X \\ Y \end{bmatrix}$$ 
```
#### Rotation Direction:
- **Counterclockwise (Positive)**: A positive angle rotates the object counterclockwise.
- **Clockwise (Negative)**: For a negative angle, the matrix changes slightly:
```math
$$R = \begin{bmatrix} \cos(\theta) & \sin(\theta) \\ -\sin(\theta) & \cos(\theta) \end{bmatrix}$$
```
> [!Note]
> 
> - $sin(A + B) = sin(A) . cos(B) + cos(A) . sin(B)$
> - $sin(A - B) = sin(A) . cos(B) - cos(A) . sin(B)$
> - $cos(A + B) = cos(A) . cos(B) - sin(A) . sin(B)$ 
> - $cos(A - B) = cos(A) . cos(B) + sin(A) . sin(B)$ 
> 
> | **Function**       | **0°**    | **30°**              | **45°**              | **60°**              | **90°**   |
> | ------------------ | --------- | -------------------- | -------------------- | -------------------- | --------- |
> | **sin $\theta$**   | 0         | $\frac{1}{2}$        | $\frac{\sqrt{2}}{2}$ | $\frac{\sqrt{3}}{2}$ | 1         |
> | **cos $\theta$**   | 1         | $\frac{\sqrt{3}}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{1}{2}$        | 0         |
> | **tan $\theta$**   | 0         | $\frac{1}{\sqrt{3}}$ | 1                    | $\sqrt{3}$           | undefined |
> | **sec $\theta$**   | 1         | $\frac{2}{\sqrt{3}}$ | $\sqrt{2}$           | 2                    | undefined |
> | **cosec $\theta$** | undefined | 2                    | $\sqrt{2}$           | $\frac{2}{\sqrt{3}}$ | 1         |
> | **cot $\theta$**   | undefined | $\sqrt{3}$           | 1                    | $\frac{1}{\sqrt{3}}$ | 0         |

## Scaling

- **Scaling** is a transformation used to change the size of an object by either expanding or compressing its dimensions. 
- This transformation is applied by multiplying the original coordinates by a scaling factor.
- Scaling increases or decreases the size of an object along the x-axis, y-axis, or both.
- **Scaling Factor**: Values that determine how much to stretch or shrink the object. 
  - A scaling factor greater than 1 enlarges the object.
  - A scaling factor less than 1 shrinks the object.

#### Scaling Formulas:
Let assume that:
- $(X, Y)$ - Original coordinates of a point on the object.
- $S_x$ - Scaling factor in the x-direction.
- $S_y$ - Scaling factor in the y-direction.
- $(X', Y')$ - New coordinates after scaling.

Then, the new coordinates can be calculated as:
- $X' = X \cdot S_x$ 
- $Y' = Y \cdot S_y$ 

#### Matrix Representation of Scaling:
- Scaling can also be represented as a matrix operation, which is helpful for applying transformations consistently.

1. **Scaling Matrix**:
   - The scaling transformation can be represented by the following matrix $S$:
```math
$$S = \begin{bmatrix} S_x & 0 \\ 0 & S_y \end{bmatrix}$$ 
```
2. **Applying the Scaling Matrix**:
   - To scale a point $P(X, Y)$, multiply its coordinates by the scaling matrix to get $P'(X', Y')$:
```math
$$\begin{bmatrix} X' \\ Y' \end{bmatrix} = \begin{bmatrix} S_x & 0 \\ 0 & S_y \end{bmatrix} \begin{bmatrix} X \\ Y \end{bmatrix}$$
``` 
   - This can also be written as:
     $P' = P \cdot S$ 
#### Effects of Scaling Factors:
- $S_x, S_y > 1$: Enlarges the object in the respective directions.
- $0 < S_x, S_y < 1$: Reduces the size of the object in the respective directions. 

## Reflection

- **Reflection** is a transformation that creates a mirror image of an object across a specific axis or point. 
- Unlike other transformations, reflection does not change the size or shape of the object—it only alters its orientation, effectively flipping it over a line (axis) or point.
- It can be thought of as a "flip" or "mirror image" transformation.
- Reflection is similar to rotating an object by 180°.
- Only the position is flipped, the object's dimensions remain the same.

#### Types of Reflection:
- Reflections can be performed across the x-axis, y-axis, or through the origin, each creating different mirrored effects.
##### 1. Reflection Across the X-Axis

When reflecting across the **x-axis**, the object's x-coordinates remain the same, but the y-coordinates are inverted.

- **Reflection Equations**:
  $X' = X$ 
  $Y' = -Y$ 

- **Matrix Form**:
```math
$$\begin{bmatrix} X' \\ Y' \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix} \begin{bmatrix} X \\ Y \end{bmatrix}$$ 
```
- **Homogeneous Coordinates (3x3 Matrix)**:
```math
$$\begin{bmatrix} 1 & 0 & 0 \\ 0 & -1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
```  
##### 2. Reflection Across the Y-Axis

When reflecting across the **y-axis**, the object's y-coordinates remain the same, but the x-coordinates are inverted.

- **Reflection Equations**:
  $X' = -X$ 
  $Y' = Y$ 

- **Matrix Form**:
```math
$$\begin{bmatrix} X' \\ Y' \end{bmatrix} = \begin{bmatrix} -1 & 0 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} X \\ Y \end{bmatrix}$$ 
```

- **Homogeneous Coordinates (3x3 Matrix)**:
```math
$$\begin{bmatrix} -1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
```

##### 3. Reflection Through the Origin

Reflecting through the **origin** is equivalent to flipping both $x$ and $y$ coordinates, effectively creating a rotation of 180° around the origin.

- **Reflection Equations**:
  $X' = -X$ 
  $Y' = -Y$ 

- **Matrix Form**:
```math
$$\begin{bmatrix} X' \\ Y' \end{bmatrix} = \begin{bmatrix} -1 & 0 \\ 0 & -1 \end{bmatrix} \begin{bmatrix} X \\ Y \end{bmatrix}$$ 
```
- **Homogeneous Coordinates (3x3 Matrix)**:
```math
  $$\begin{bmatrix} -1 & 0 & 0 \\ 0 & -1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
```
## Shear 

- **Shearing** is a transformation that skews the shape of an object along a particular axis, creating a slanted appearance. 
- Shearing is also known as **skewing**. 
- This transformation affects either the x-coordinates or y-coordinates of an object, while the other coordinates remain unchanged. 
- Shearing transformations are used to create effects where shapes appear slanted or skewed, adjusting only one axis while keeping the other axis constant.
- There are two types of shear transformations -  **X-Shear** and **Y-Shear**.

#### 1. X-Shear Transformation
In **X-Shear**, the y-coordinates of points remain unchanged, while the x-coordinates are shifted. This results in the object tilting to the right or left along the vertical lines.
##### X-Shear Formulas:
- $X_{\text{new}}$ - New x-coordinate after shearing.
- $X_{\text{old}}$ - Original x-coordinate.
- $Y_{\text{old}}$ - Original y-coordinate.
- $Sh_x$ - Shear factor for x-axis.

The transformation can be represented as:
- $X_{\text{new}} = X_{\text{old}} + Sh_x \times Y_{\text{old}}$ 
- $Y_{\text{new}} = Y_{\text{old}}$ 

##### X-Shear Matrix Representation:
```math
$$\begin{bmatrix} X_{\text{new}} \\ Y_{\text{new}} \end{bmatrix} = \begin{bmatrix} 1 & Sh_x \\ 0 & 1 \end{bmatrix} \begin{bmatrix} X_{\text{old}} \\ Y_{\text{old}} \end{bmatrix}$$
```
##### Homogeneous Coordinates (3x3 Matrix):
```math
$$\begin{bmatrix} 1 & Sh_x & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
``` 

#### 2. Y-Shear Transformation
In **Y-Shear**, the x-coordinates remain unchanged, while the y-coordinates are shifted. This causes horizontal lines to slope upwards or downwards.
##### Y-Shear Formulas:
- $Y_{\text{new}}$ -  New y-coordinate after shearing.
- $X_{\text{old}}$ -  Original x-coordinate.
- $Sh_y$ -  Shear factor for y-axis.

The transformation can be represented as:
- $X_{\text{new}} = X_{\text{old}}$ 
- $Y_{\text{new}} = Y_{\text{old}} + Sh_y \times X_{\text{old}}$ 
##### Y-Shear Matrix Representation:
```math
$$\begin{bmatrix} X_{\text{new}} \\ Y_{\text{new}} \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ Sh_y & 1 \end{bmatrix} \begin{bmatrix} X_{\text{old}} \\ Y_{\text{old}} \end{bmatrix}$$
``` 
##### Homogeneous Coordinates (3x3 Matrix):
```math
$$\begin{bmatrix} 1 & 0 & 0 \\ Sh_y & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
``` 

## Composite Transformation
- **Composite Transformation** refers to combining two or more transformations into a single operation. 
- If a transformation $T_1$  is followed by another transformation $T_2$, the resulting transformation can be represented as a single transformation $T$ , which is the **composition** of $T_1$  and $T_2$ . 
- Composite transformations enable efficient and simplified transformations by combining multiple transformation matrices into one.
- The order of operations is crucial, as the resulting transformation depends on how the individual transformations are arranged.
- This is written as —> $T = T_1 \cdot T_2$ 
- A composite transformation can be achieved by multiplying the individual transformation matrices together to obtain a combined matrix.
```math
$$[T] \cdot [X] = [X] \cdot [T_1] \cdot [T_2] \cdot [T_3] \cdots [T_n]$$
``` 
  _Where_, $[T_1], [T_2], [T_3], \ldots, [T_n]$  are transformation matrices for **Translation**, **Scaling**, **Shearing**, **Rotation**, and **Reflection**.

- The order of transformations is important in composite transformations. Since matrix multiplication is not commutative (i.e., $[A] \cdot [B] \neq [B] \cdot [A]$ ), changing the order of transformations will lead to different results.
#### Purpose:
- **Efficiency**: Instead of applying multiple transformations one by one, a composite transformation allows for a single transformation matrix to be applied, making the process more efficient.
- **Simplification**: Reduces the number of operations and matrix calculations needed to transform an object.

#### Sample Steps:
- To rotate an object about a specific point $(X_p, Y_p)$ , we can use a composite transformation involving three steps:
  1. **Translate** the point $(X_p, Y_p)$  to the origin. This is done by subtracting $X_p$  and $Y_p$  from the object's coordinates. 
  2. **Rotate** the object about the origin by applying a rotation matrix. 
  3. **Translate** the object back to its original position by adding $X_p$  and $Y_p$  to the coordinates.
This can be represented as:
```math
$$T = T_{\text{translate}}(X_p, Y_p) \cdot T_{\text{rotate}}(\theta) \cdot T_{\text{translate}}(-X_p, -Y_p)$$
```
_Where_,
- $T_{\text{translate}}(X_p, Y_p)$  is the translation matrix to move the object to the origin.
- $T_{\text{rotate}}(\theta)$  is the rotation matrix for the angle $\theta$ .
- $T_{\text{translate}}(-X_p, -Y_p)$  is the translation matrix to move the object back to the original point.

# 3D Transformations
- In Computer Graphics, transformations are essential for manipulating 3D objects. 
- These transformations help in adjusting the **position, size, and orientation** of objects in a 3D space, allowing us to generate realistic images and animations.
- With these transformations, we can express the location of objects relative to others, simulate object movements, and change viewpoints.

### Key Points of 3D Transformations:
1. **Purpose**:
   - Used to change the **position**, **size**, or **orientation** of objects in 3D space.
   - Helpful in viewing changes, where the viewpoint might change quickly or objects may move relative to one another.
   - A sequence of transformations can be applied repeatedly to achieve the desired effect.

2. **Matrix Representations**:
   - **2D Transformations**: 
     - Use a **2 × 2 matrix** for linear transformations (like rotation and scaling) or a **3 × 3 matrix** for homogeneous coordinates.
   - **3D Transformations**:
     - Use a **3 × 3 matrix** for transformations involving **linear algebraic equations** (like scaling, rotation).
     - Use a **4 × 4 matrix** for **homogeneous coordinates**, which includes translation, allowing for more complex transformations.

### Importance of Using Matrices in 3D Transformations:
- Matrices allow for the **concatenation** of multiple transformations into a single transformation matrix, improving efficiency.
- Using a **4 × 4 matrix** for homogeneous coordinates in 3D ensures that all transformations, including translation, scaling, rotation, and perspective projections, can be combined seamlessly.
- It simplifies complex calculations and helps in efficient processing of transformations in computer graphics systems.

## Translation in 3D Transformations
- Translation refers to shifting an object from one position to another in a coordinate system.
- It involves changing the object's position without altering its shape, size, or orientation.
- The translation process uses translation vectors to move objects in different directions.
- It affects the position of the object but does not change its shape or orientation.
- To translate a 3D object, every vertex of the object needs to be transformed using the translation vectors.
- Translations require three vectors in the $x$, $y$, and $z$ directions:
  - $T_x$: Translation in the x-direction.
  - $T_y$: Translation in the y-direction.
  - $T_z$: Translation in the z-direction.

##### Example
- Let’s say $P$ is a point in 3D space with coordinates $(x, y, z)$.
- After applying translation using vectors $T_x$, $T_y$, and $T_z$, the new coordinates of the point become:
  - $x1 = x + Tx$
  - $y1 = y + Ty$
  - $z1 = z + Tz$
- Thus, the translated point has coordinates $(x_1, y_1, z_1)$.

#### Matrix Representation for 3D Translation
- Translation transformations in 3D can be represented using a 4x4 matrix. This matrix is used to perform translation on homogeneous coordinates.
  
1. The matrix for translation can be represented as:   
```math
   $$
   \begin{bmatrix}
   _1 & 0 & 0 & T_x \\
   0 & _1 & 0 & T_y \\
   0 & 0 & _1 & T_z \\
   0 & 0 & 0 & _1
   \end{bmatrix}
   $$
```

3. To translate a point $P$ with coordinates $(x, y, z)$, the translation matrix is multiplied with the point in homogeneous coordinates. Homogeneous coordinate of point $P$ is represented as:  
```math
     $$
     \begin{bmatrix}
     x \\
     y \\
     z \\
     _1
     \end{bmatrix}
     $$
```

4. Matrix multiplication for translation:
```math
   $$
   \begin{bmatrix}
   x_1 \\
   y_1 \\
   z_1 \\
   _1
   \end{bmatrix}
   = 
   \begin{bmatrix}
   _1 & 0 & 0 & T_x \\
   0 & _1 & 0 & T_y \\
   0 & 0 & _1 & T_z \\
   0 & 0 & 0 & _1
   \end{bmatrix}
   \times
   \begin{bmatrix}
   x \\
   y \\
   z \\
   _1
   \end{bmatrix}
   $$
```
   - Resulting coordinates after translation:
     - $x_1 = x + T_x$
     - $y_1 = y + T_y$
     - $z_1 = z + T_z$

## Scaling in 3D Transformations
- Scaling is a transformation used to change the size of an object, either by increasing or decreasing its dimensions.
- Scaling alters the object's size while maintaining its shape and orientation.

### Scaling Factors in 3D
- Scaling in 3D requires three scaling factors:
  - $S_x$: Scaling factor along the x-axis
  - $S_y$: Scaling factor along the y-axis
  - $S_z$: Scaling factor along the z-axis

- The scaling factors determine how much an object will stretch or shrink along each axis.

### Scaling Equations
- To scale a point $(X_{old}, Y_{old}, Z_{old})$ by factors $S_x$, $S_y$, $S_z$, the _{new} coordinates $(X_{new}, Y_{new}, Z_{new})$ are calculated using the following equations:
  - $X_{new} = X_{old} \times S_x$
  - $Y_{new} = Y_{old} \times S_y$
  - $Z_{new} = Z_{old} \times S_z$

### Matrix Representation for 3D Scaling

Matrix Format:
- Scaling transformations in 3D can be represented using a 4x4 matrix. This matrix is used to perform scaling on homogeneous coordinates.

1. The matrix for scaling can be represented as:
```math
   $$
   \begin{bmatrix}
   S_x & 0  & 0  & 0 \\
   0  & S_y & 0  & 0 \\
   0  & 0  & S_z & 0 \\
   0  & 0  & 0  & 1
   \end{bmatrix}
   $$
```

3. To scale a point $P$ with coordinates $(x, y, z)$, the scaling matrix is multiplied with the point in homogeneous coordinates. Homogeneous coordinate of point P is represented as:
```math
     $$
     \begin{bmatrix}
     x \\
     y \\
     z \\
     1
     \end{bmatrix}
     $$
```

4. Matrix multiplication for scaling:
```math
   $$
   \begin{bmatrix}
   x_{new} \\
   y_{new} \\
   z_{new} \\
   1
   \end{bmatrix}
   =
   \begin{bmatrix}
   S_x & 0  & 0  & 0 \\
   0  & S_y & 0  & 0 \\
   0  & 0  & S_z & 0 \\
   0  & 0  & 0  & 1
   \end{bmatrix}
   \times
   \begin{bmatrix}
   x \\
   y \\
   z \\
   1
   \end{bmatrix}
   $$
```

   - Resulting coordinates after scaling:
     - $x_{new} = x \times S_x$
     - $y_{new} = y \times S_y$
     - $z_{new} = z \times S_z$

### Types of Scaling
1. Uniform Scaling:
   - If all scaling factors $S_x = S_y = S_z$, then the scaling is called uniform scaling.
   - This results in the object increasing or decreasing in size uniformly in all directions.

2. Differential Scaling:
   - If the scaling factors are different $(S_x ≠ S_y ≠ S_z)$, it is called differential scaling.
   - The object will stretch or shrink differently along each axis.

### Scaling of an Object Relative to a Fixed Point
- Sometimes, scaling needs to be performed relative to a specific point $(a, b, c)$ rather than the origin.
- To scale an object relative to a fixed point, follow these steps:
  1. Translate the fixed point to the origin.
  2. Scale the object relative to the origin using the scaling matrix.
  3. Translate the object back to its original position.

## 3D Rotation in Computer Graphics
- Rotation in 3D graphics refers to rotating an object around one of the three coordinate axes $(x, y, z)$.
- The object's position changes, but its shape remains the same.
- When rotating around a specific axis, the coordinate corresponding to that axis remains unchanged.

### General Rules for 3D Rotation
- Rotation is applied to a specific axis, and the coordinate along that axis remains the same:
  - Rotation across X-axis: The x coordinate remains unchanged $(X' = X)$.
  - Rotation across Y-axis: The y coordinate remains unchanged $(Y' = Y)$.
  - Rotation across Z-axis: The z coordinate remains unchanged $(Z' = Z)$.

### Inverse Transformation Matrix
- The inverse transformation matrix for a 3D rotation is a 4x4 identity matrix, which is used to transform points back to their original positions if needed:
```math
  $$
  \begin{bmatrix}
  1 & 0 & 0 & 0 \\
  0 & 1 & 0 & 0 \\
  0 & 0 & 1 & 0 \\
  0 & 0 & 0 & 1
  \end{bmatrix}
  $$
```

### 3D Rotation Types
There are three types of rotations in 3D:
1. Rotation around the X-axis
2. Rotation around the Y-axis
3. Rotation around the Z-axis

#### 1. Rotation Around the X-Axis
Equations for Rotation:
- $X' = X$
- $Y' = Y \times cos(\theta) - Z \times sin(\theta)$
- $Z' = Y \times sin(\theta) + Z \times cos(\theta)$

Matrix Representation:
```math
$$
\begin{bmatrix}
1 & 0      & 0       & 0 \\
0 & \cos\theta  & -\sin\theta  & 0 \\
0 & \sin\theta  & \cos\theta   & 0 \\
0 & 0      & 0       & 1
\end{bmatrix}
$$
```

- Let O be the original coordinates (X, Y, Z).
- After applying the rotation matrix, the new coordinates O' will be:
  $O' = R_x \times O$
#### 2. Rotation Around the Y-Axis
Equations for Rotation:
- $X' = Z \times sin(\theta) + X \times cos(\theta)$
- $Y' = Y$
- $Z' = Z \times cos(\theta) - X \times sin(\theta)$

Matrix Representation:
```math
$$
\begin{bmatrix}
\cos\theta  & 0 & \sin\theta & 0 \\
0      & 1 & 0     & 0 \\
-\sin\theta & 0 & \cos\theta & 0 \\
0      & 0 & 0     & 1
\end{bmatrix}
$$
```

- After applying the rotation matrix, the new coordinates O' will be:
  $O' = R_y \times O$
  
#### 3. Rotation Around the Z-Axis
Equations for Rotation:
- $X' = X \times cos(\theta) - Y \times sin(\theta)$
- $Y' = X \times sin(\theta) + Y \times cos(\theta)$
- $Z' = Z$

Matrix Representation:
```math
$$
\begin{bmatrix}
\cos\theta  & -\sin\theta & 0 & 0 \\
\sin\theta  & \cos\theta  & 0 & 0 \\
0      & 0      & 1 & 0 \\
0      & 0      & 0 & 1
\end{bmatrix}
$$
```

- After applying the rotation matrix, the new coordinates O' will be:
  $O' = R_z \times O$  
## 3D Shearing in Computer Graphics
- Shearing in 3D graphics refers to transforming an object so that its shape is distorted in one or more directions. 
- It shifts the coordinates of an object in one axis, based on the displacement in another axis.
- Shearing can be applied along the $x$, $y$, or $z$ directions using shearing parameters.
### Shearing Parameters in 3D
- Let the initial coordinates of an object $O$ be $(X, Y, Z)$.
- Shearing is controlled by the parameters:
  - $Sh_x$: Shearing parameter along the x-direction
  - $Sh_y$: Shearing parameter along the y-direction
  - $Sh_z$: Shearing parameter along the z-direction
### Types of 3D Shearing
Shearing in 3D can be applied in three ways:
1. Shearing in the $X$ direction
2. Shearing in the $Y$ direction
3. Shearing in the $Z$ direction
#### 1. Shearing in the X Direction
Equations for X-axis Shearing:
- $X' = X$
- $Y' = Y + Sh_y \times X$
- $Z' = Z + Sh_z \times X$

Matrix Representation:
```math
$$
\begin{bmatrix}
1 & Sh_y & Sh_z & 0 \\
0 & 1   & 0   & 0 \\
0 & 0   & 1   & 0 \\
0 & 0   & 0   & 1
\end{bmatrix}
$$
```
- In matrix form, the point $(X, Y, Z, 1)$ is transformed using the shearing matrix for the X-axis:
```math
  $$
  \begin{bmatrix}
  X' \\
  Y' \\
  Z' \\
  1
  \end{bmatrix}
  =
  \begin{bmatrix}
  1 & Sh_y & Sh_z & 0 \\
  0 & 1   & 0   & 0 \\
  0 & 0   & 1   & 0 \\
  0 & 0   & 0   & 1
  \end{bmatrix}
  \times
  \begin{bmatrix}
  X \\
  Y \\
  Z \\
  1
  \end{bmatrix}
  $$
```

#### 2. Shearing in the Y Direction

Equations for Y-axis Shearing:
- $X' = X + Sh_x \times Y$
- $Y' = Y$
- $Z' = Z + Sh_z \times Y$

Matrix Representation:
```math
$$
\begin{bmatrix}
1   & 0   & 0   & 0 \\
Sh_x & 1   & Sh_z & 0 \\
0   & 0   & 1   & 0 \\
0   & 0   & 0   & 1
\end{bmatrix}
$$
```

- In matrix form, the point (X, Y, Z, 1) is transformed using the shearing matrix for the Y-axis:
```math
  $$
  \begin{bmatrix}
  X' \\
  Y' \\
  Z' \\
  1
  \end{bmatrix}
  =
  \begin{bmatrix}
  1   & 0   & 0   & 0 \\
  Sh_x & 1   & Sh_z & 0 \\
  0   & 0   & 1   & 0 \\
  0   & 0   & 0   & 1
  \end{bmatrix}
  \times
  \begin{bmatrix}
  X \\
  Y \\
  Z \\
  1
  \end{bmatrix}
  $$
```
  
#### 3. Shearing in the Z Direction

Equations for Z-axis Shearing:
- $X' = X + Sh_x \times Z$
- $Y' = Y + Sh_y \times Z$
- $Z' = Z$

Matrix Representation:
```math
$$
\begin{bmatrix}
1   & 0   & Sh_x & 0 \\
0   & 1   & Sh_y & 0 \\
0   & 0   & 1   & 0 \\
0   & 0   & 0   & 1
\end{bmatrix}
$$
```
- In matrix form, the point $(X, Y, Z, 1)$ is transformed using the shearing matrix for the Z-axis:
```math
  $$
  \begin{bmatrix}
  X' \\
  Y' \\
  Z' \\
  1
  \end{bmatrix}
  =
  \begin{bmatrix}
  1   & 0   & Sh_x & 0 \\
  0   & 1   & Sh_y & 0 \\
  0   & 0   & 1   & 0 \\
  0   & 0   & 0   & 1
  \end{bmatrix}
  \times
  \begin{bmatrix}
  X \\
  Y \\
  Z \\
  1
  \end{bmatrix}
  $$
```

