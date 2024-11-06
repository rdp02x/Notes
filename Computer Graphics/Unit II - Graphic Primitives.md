# Unit II - Graphics Primitives

- Graphics primitives are the simplest graphical elements used to build complex shapes and images in computer graphics.
- They form the foundational elements from which all visual representations are made.
#### Types of Primitives:
  - **Point**: The most basic unit, represented by a single pixel on the screen.
  - **Line**: A straight path connecting two points, used to outline shapes and create structures.
  - **Polygon**: Closed shapes formed by connecting multiple lines, such as triangles and rectangles.
#### Importance of Graphics Primitives
- They enable efficient rendering and manipulation of images.
- Provide control over how shapes, lines, and colors are displayed.
- Allow for complex image construction by combining these basic elements in various ways.

## Line Drawing Algorithms

#### 1. DDA Line Drawing Algorithm
- DDA Algorithm is the simplest line drawing algorithm.
- We are given with followings —
  - Starting coordinates = $(X_0, Y_0)$
  - Ending coordinates = $(X_n, Y_n)$
- **Steps**:
  1. Find $d_x$, $d_y$, $m = \frac{dy}{dx}$, $d_x = x_2 - x_1$, $d_y = y_2 - y_1$
  2. Find which is greater value $d_x$ or $d_y$? Intermediate points between $(x_0, y_0)$ and $(x_n, y_n)$ = $\frac{d_x}{d_y}$
  3. Check $m$ / slope value: $m=1$, $m>1$ or $m<1$, find next subsequent point coordinate values. Compare new $(x,y)$ coordinates value with last coordinates value. If they are same then stop.
  4. Then connect all intermediate points and plot those points across graph

> Current point is $p_k$ then next point will be $p_{k+1}$.

##### Calculation Steps:

1. Calculate $\Delta{X}$, $\Delta{Y}$ and $M$ from the given input.
   These parameters are calculated as
   - $\Delta{X}$ = $X_n$ – $X_0$
   - $\Delta{Y}$ = $Y_n$ - $Y_0$
   - $M$ = $\frac{\Delta{Y}}{\Delta{X}}$

2. Find the number of steps or points in between the starting and ending coordinates.
   - $|\Delta{X}| > |\Delta{Y}|$ —> $M$ = $|\Delta{X}|$;
   - $|\Delta{X}| < |\Delta{Y}|$ —> $M$ = $|\Delta{Y|}$;

3. Suppose the current point is $(X_p, Y_p)$ and the next point is $(X_{p+1}, Y_{p+1})$.
   Find the next point by following the below three cases —
   - Case I: $M < 1$ 
		   - $x_{p+1}$ = round off $(1 + X_p)$
		   - $y_{p+1}$ = round off $(M + Y_p)$ 

   - Case II: $M = 1$ 
		   - $x_{p+1}$ = round off $(1 + X_p)$
		   - $y_{p+1}$ = round off $(1 + Y_p)$ 

   - Case III: $M > 1$ 
		   - $x_{p+1}$ = round off $(\frac{1}{M} + X_p)$
		   - $y_{p+1}$ = round off $(1 + Y_p)$ 
4. Keep repeating _Step-3_ until the end point is reached or the number of generated new points (Including the starting and ending points) equals to the steps count.

##### Advantages and Disadvantages of DDA algorithm

| **Advantages**                                                         | **Disadvantages**                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| It is a simple and easy-to-understand algorithm.                       | Extra overhead is involved due to the use of the `round off()` function.     |
| It is straightforward to implement in code.                            | The `round off()` function increases the time complexity of the algorithm.   |
| Avoids using multiplication operations, which reduces time complexity. | Resulting lines may not appear smooth because of the `round off()` function. |
|                                                                        | The points generated are not always accurate.                                |
#### 2. Bresenham’s Line Drawing Algorithm
- The **Bresenham’s algorithm** mainly uses whole numbers / integers for it’s calculation, which make this algorithm faster and more efficient.
> [!NOTE] Note
> A thing to know is any line in the system is represented by —> $y = mx + c$, where $m$ is the slope of the line (i.e. $\frac{\Delta{y}}{\Delta{x}}$), and $c$ is the point where the line intersects the $y$ axis (y-intercept).
- A line will have a $\frac{\Delta{y}}{\Delta{x}} = 1$, if the angles around the lines are equals $45°$
- If the $\Delta{x}$ is greater than $\Delta{y}$, the slope of the line will be less than 1. ($\frac{\Delta{y}}{\Delta{x}} > 1$)
- If the $\Delta{x}$ is less than $\Delta{y}$, the slope of the line will be greater than 1. ($\frac{\Delta{y}}{\Delta{x}} < 1$)
- The main reason Bresenham’s algorithm was introduced was because the old good DDA gave us the results in float value, which made it slower.
- To know what pixel to light up, when a line goes through 2 pixels at same time, we assume that there is space between pixels, and the pixel nearest to the line should lit up.
##### Derivation:
- $y = mx + c$
- $y = m(x_k + 1) + c$
<br> <br />
- $d_1 = y - y_k$
- $d_2 = y_k + 1 - y$
<br> <br />
- $d_1 = [m(x_k + 1) + c] - y_k$
- $d_2 = y_k + 1 - m(x_k + 1) - c$
<br> <br />
- $d_1 = m(x_k + 1) + c - y_k$
- $d_2 = y_k + 1 - m(x_k + 1) - c$
<br> <br />
- If $d_1 - d_2 < 0$ —> $y_k$
- If $d_1 - d_2 > 0$ —> $y_k + 1$
<br> <br />
• Keeping the values of $d_1 - d_2$:
- $[m(x_k + 1) + c - y_k] - [y_k + 1 - m(x_k + 1) - c]$
- $m(x_k + 1) + c - y_k - y_k - 1 + m(x_k + 1) + c$
- $2m(x_k + 1) + 2c - 2y_k - 1$
<br> <br />
• As we know that, $m = \frac{\Delta{x}}{\Delta{y}}$
- $d_1 - d_2 = 2\frac{\Delta{y}}{\Delta{x}} (x_k + 1) + 2c - 2y_k - 1$
- $\Delta{x}(d_1 - d_2) = 2\Delta yx_k - 2\Delta xy_k + 2\Delta y + 2\Delta xc - \Delta x$
- $P_k = 2\Delta yx_k - 2\Delta xy_k + c$
- $\frac{P_{next}}{p_{k+1}} = 2\Delta yx_{next} - 2\Delta xy_{next}$
<br> <br />
- $P_{next} - P_k = (2\Delta yx_{next} - 2\Delta xy_{next}) - (2\Delta yx_k - 2\Delta xy_k)$
- $P_{next} - P_k = 2\Delta yx_{next} - 2\Delta xy_{next} - 2\Delta yx_k + 2\Delta xy_k$
- $P_{next} - P_k = 2\Delta y(x_{next} - x_k) - 2\Delta x(y_{next} - y_k)$
<br> <br />
• If $P_{next} - P_k < 0$:
- $P_{next} = P_k + 2\Delta y(x_k + 1 - x_k) - 2\Delta x(y_k - y_k)$
- $P_k + 1 = P_k + 2\Delta y$
<br> <br />
• If $P_{next} - P_k \geqslant 0$:
- $P_{next} = P_k + 2\Delta y(x_k + 1 - x_k) - 2\Delta x(y_k + 1 - y_k)$
- $P_k + 1 = P_k + 2\Delta y$
<br> <br />
• Finding the initial value of $P_k$:
- $P_k = 2\Delta yx_k - 2\Delta xy_k + 2\Delta y + 2\Delta xc - x$
<br> <br />
• As we know:
- $y_1 = mx_1 + c$
- $c = y_1 - mx_1$
<br> <br />
- $P_k = 2\Delta yx_1 - 2\Delta xy_1 + 2\Delta x(y_1 - \frac{\Delta y}{\Delta x} x_1) - \Delta x$
- $P_k = 2\Delta yx_1 - 2\Delta xy_1 + 2\Delta xy_1 - 2\Delta yx_1 - \Delta x + 2\Delta y$
- $P_k = 2\Delta y - \Delta x$

##### Programmatic Code:
```syntax
bresenhamAlgorithm (x1, x2, y1, y2) {
	x = x1;
	y = y1;
	dx = y2 - y1;
	p = 2dx - dy;

	while (x <= x2) {
		putPixel(x, y);
		x++;
		if (p < 0) {
			p = p + 2∆y;
		} else {
			p = p + 2∆y - 2∆x;
			y++;
		}
	}
}
```

##### Calculation Steps:
- Given — 
  - Starting coordinates = ($X_0, Y_0$)
  - Ending coordinates = ($X_n, Y_n$)

1. Calculate $\Delta X$ and $\Delta Y$ from the given input. These parameters are calculated as:
   - $\Delta X = X_n – X_0$
   - $\Delta Y =Y_n – Y_0$

2. Calculate the decision parameter $P_k$. It is calculated as:
   - $P_k = 2\Delta Y – \Delta X$

3.  Suppose the current point is $(X_k, Y_k)$ and the next point is $(X_{k+1}, Y_{k+1})$. Find the next point depending on the value of decision parameter $P_k$. Following are the two cases:
   - Case I —> $P_k < 0$
     - $P_{k+1} = P_k + 2\Delta Y$
     - $X_{k+1} = X_k + 1$
     - $Y_{k+1} = Y_k$
   - Case II —> $P_k \geqslant 0$
     - $P_{k+1} = P_k + 2\Delta Y - 2\Delta X$
     - $X_{k+1} = X_k + 1$
     - $Y_{k+1} = Y_k + 1$

4. Keep repeating _Step-3_ until the end point is reached or number of iterations equals to $(\Delta X - 1)$ times.

##### Advantages and Disadvantages of Bresenham’s Algorithm

| **Advantages**                                                         | **Disadvantages**                                                      |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Easy to implement.                                                     | Although accuracy is improved, the resulting line is still not smooth. |
| Fast and incremental in nature.                                        | Designed specifically for basic line drawing.                          |
| Executes quickly, though slightly slower than the DDA Algorithm.       |                                                                        |
| Generates points that are more accurate compared to the DDA Algorithm. |                                                                        |
| Uses only fixed points, enhancing stability and accuracy.              |                                                                        |


## Circle Drawing Algorithms

- There are two popular algorithms for generating a circle − **Bresenham’s Algorithm** and **Midpoint Circle Algorithm**.
- These algorithms are based on the idea of determining the subsequent points required to draw the circle.
- The equation of circle is $X_2 + Y_2 = r_2, X_2 + Y_2 = r_2$, where $r$ is radius.
#### Mid Point Circle Drawing Algorithm
- **Given** -
  - Centre point of Circle = $(X_0, Y_0)$
  - Radius of Circle = $R$
##### Calculation Steps:
1. Assign the starting point coordinates $(X_0, Y_0)$ as-
   - $X_0 = 0$
   - $Y_0 = R$

2. Calculate the value of initial decision parameter $P_0$ as
   - $P_0 = 1 – R$

3. Suppose the current point is $(X_k, Y_k)$ and the next point is $(X_{k+1}, Y_{k+1})$. Find the next point of the **first octant** depending on the value of decision parameter $P_k$. Follow the below two cases -
   - Case I —> $P_k < 0$
     - $X_{k + 1} = X_k + 1$
     - $Y_{k+1} = Y_k$
     - $P_{k+1} = P_k + 2(X_{k+1}) + 1$
   - Case II —> $P_k \geqslant 0$
     - $X_{k + 1} = X_k + 1$
     - $Y_{k+1} = Y_k + 1$ 
     - $P_{k+1} = P_k - 2(Y_{k+1}) + 2(X_{k+1}) + 1$

4. If the given center point $(X_0, Y_0)$ is not $(0, 0)$, then do the following and plot the points -
   - $X_{plot} = X_c + X_0$
   - $Y_{plot} = Y_c + Y_0$

	Here, $(X_c, Y_c)$ denotes the current value of $X$ and $Y$ coordinates.

5. Keep repeating _Step-3_ and _Step-4_ until $X_{plot} \geqslant Y_{plot}$.

6. _Step-5_ generates all the points for one octant. To find the points for other seven octants, follow the eight symmetry property of circle.

#### Advantages and Disadvantages of the Mid-Point Circle Drawing Algorithm:

| **Advantages**                                                                           | **Disadvantages**                             |
| ---------------------------------------------------------------------------------------- | --------------------------------------------- |
| Powerful and efficient algorithm.                                                        | Accuracy of generated points can be an issue. |
| Based on the simple circle equation \( X^2 + Y^2 = R^2 \), making it easy to understand. | The resulting circle may not appear smooth.   |
| Easy to implement from a programmer’s perspective.                                       | Can be time-consuming to execute.             |
| Suitable for generating curves on raster displays.                                       |                                               |

## Polygons

- A **polygon** is defined as an ordered list of vertices.
- Polygons can be classified into two main types: **Convex** and **Concave** polygons. They are further categorized based on their side lengths and angles.
#### Types of Polygons
##### 1. Regular Polygons:
- A regular polygon has all its sides of equal length and all its angles of equal measure.
- Examples:
  - **Equilateral Triangle** - Consists of three equal sides $AB$, $BC$, $CA$ and three equal angles $\angle ABC$, $\angle BCA$, $\angle CAB$. 
  - **Square** - Consists of four equal sides $AB$, $BC$, $CD$, $DA$ and four equal angles $\angle ABC$, $\angle BCD$, $\angle CDA$, $\angle DAB$. 
  - **Regular Pentagon** - Consists of five equal sides $AB$, $BC$, $CD$, $DE$, $EA$ and five equal angles $\angle ABC$, $\angle BCD$, $\angle CDE$, $\angle DEA$, $\angle EAB$. 
##### 2. Irregular Polygons:
- An irregular polygon has sides of unequal lengths and angles of unequal measures.
- Example:
  - **Scalene Triangle** - Consists of three unequal sides $AB$, $BC$, $CA$ and three unequal angles $\angle ABC$, $\angle BCA$, $\angle CAB$. 
#### General Characteristics of Polygons
- A polygon is formed when many lines are closed, resulting in an enclosed figure.
- In a polygon, the starting point $P_1$ and the ending point $P_6$ are the same.
#### Types of Polygons Based on Shape
- **Convex Polygons** - In a convex polygon, any line segment joining two interior points lies entirely inside the polygon. 
- **Concave Polygons** - In a concave polygon, a line segment connecting two points may or may not lie inside the polygon. 

