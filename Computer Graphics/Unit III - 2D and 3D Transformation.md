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

