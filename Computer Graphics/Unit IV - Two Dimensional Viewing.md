# Unit IV - Two Dimensional Viewing

### Window
- A window is an opening that allows a viewer to observe a specific part of the outside world or graphical scene.
- In computer graphics, windowing enables the selection and enlargement of specific portions of a graphical object or scene. By defining a window, users focus on areas of interest and ignore irrelevant details.
- Imagine looking through a rectangular frame, where only the scene visible within that frame matters, while the rest is discarded or ignored.

#### Windowing Process
- The windowing process involves selecting a portion of a graphical drawing or object based on user-defined parameters.
- Once a portion is selected, it can be enlarged or modified for better visualization or focus on particular details within the scene.

### Unseen Parts and Clipping
- Clipping is the process of eliminating parts of a drawing or object that fall outside the window, meaning they are not of interest in the current view.
- The primary goal of clipping is to manage which parts of the image are visible and to ignore or remove irrelevant portions that do not contribute to the current view.
- Clipping is achieved through transformations that align with the viewing transformation, which is essential in constructing and managing 2D images effectively.

#### Entities Subject to Clipping
- When performing clipping in a graphical scene, we typically need to focus on three types of entities:
     - Lines: Line segments or edges that may partially extend beyond the window.
     - Polygons: Polygonal shapes that might intersect with the window's boundaries.
     - Text: Text elements that may need to be displayed within a particular viewing area and clipped accordingly.

### Two-Dimensional Window Concept

#### 1. Nature of a Window: 
- In computer graphics, a window is usually conceptualized as a rectangular region within the drawing area, representing a section of the scene that will be visible to the user.
   
#### 2. Window Specifications:
- Windows are defined by a set of boundary coordinates, typically including:
    - $X_{min}$: The minimum x-coordinate of the window (left boundary).
    - $X_{max}$: The maximum x-coordinate of the window (right boundary).
    - $Y_{min}$: The minimum y-coordinate of the window (bottom boundary).
    - $Y_{max}$: The maximum y-coordinate of the window (top boundary).
   
#### 3. Coordinate Terminology:
- In the context of windowing and clipping, it's important to recognize that:
- "Window coordinates," "User coordinates," and "World coordinates" often refer to the same concept.
- They represent the coordinates of objects in the virtual world, where graphical elements are defined before they are mapped to the display device.

### Coordinate Systems

#### 1. World Coordinate System (WCS)
- The World Coordinate System is a coordinate system used to define objects within the entire virtual scene.
- It establishes the original, logical positions of graphical elements before they are processed or mapped to physical devices.

#### 2. Physical Device Coordinate System (PDCS)
- The Physical Device Coordinate System is specific to each display device (such as monitors, printers, etc.) and represents how images are rendered on that device.
- Each device has its own coordinate system, which may vary depending on screen resolution, orientation, and physical dimensions.

#### 3. Normalized Device Coordinate System (NDCS)
- The Normalized Device Coordinate System is a standardized coordinate system that simplifies the transition between the World Coordinate System and device-specific coordinates.
- It ensures consistency across different devices by normalizing coordinates to a standardized range, often between 0 and 1. This allows seamless mapping from the virtual world to physical devices, irrespective of device-specific differences.

### Viewing Transformation in Computer Graphics
 
- The viewing transformation is the process of mapping a specified area in the world coordinate scene (also known as object space) to device coordinates (such as the screen space).
- This transformation translates the scene from the world coordinate system (WCS) to a format suitable for display on a physical device coordinate system (PDCS).

#### Key Terminology
- *Window* - An area in the world coordinate system selected for display. It defines "WHAT" part of the scene should be viewed.
- *Viewport* - A rectangular area on the device screen where the contents of the window are displayed. It defines "WHERE" the selected part of the scene will appear on the screen.
- *Clipping* - The technique used to omit parts of the scene that fall outside the defined window. Clipping ensures only the area within the window is displayed in the viewport.

#### Window and Viewport
- A window represents a subsection of the world coordinate space. It is the part of the scene that we choose to display.
- Defined by minimum and maximum coordinates in the x and y directions:
    - $Xw_{min}$ - Minimum x-coordinate of the window
    - $Xw_{max}$ - Maximum x-coordinate of the window
    - $Yw_{min}$ - Minimum y-coordinate of the window
    - $Yw_{max}$ - Maximum y-coordinate of the window
- A viewport represents a rectangular display area on the device screen where the contents of the window will appear.
- Defined by minimum and maximum coordinates in the viewport space:
    - $Xv_{min}$ - Minimum x-coordinate of the viewport
    - $Xv_{max}$ - Maximum x-coordinate of the viewport
    - $Yv_{min}$ - Minimum y-coordinate of the viewport
    - $Yv_{max}$ - Maximum y-coordinate of the viewport

#### World Coordinate System (Object Space)
- The space in which the application model is defined, often using real-world units (e.g., meters, inches) or abstract units (e.g., arbitrary units for vector graphics).
- It is the reference coordinate system for defining objects and their geometry.
- Characteristics:
    - Objects in the world coordinate system are described in terms of position and dimensions.
    - The coordinates are often referred to as world coordinates.

#### Screen Coordinate System (Image Space)
- The coordinate system used by the display device, such as a monitor, to render the graphical scene.
- Typically measured in pixels (e.g., 800x600 pixels) but could use other units depending on the device.
- It is where the rasterized image of an object is defined for display.

#### Normalized Device Coordinate System (NDCS)
- A standardized coordinate system that helps map the world coordinates to the device-specific coordinates.
- It simplifies the transition between world and device coordinates, ensuring the graphics render correctly across various display devices.

#### Window-Viewport Mapping Process
- The mapping process from world coordinates (window) to screen coordinates (viewport) involves:
- Choosing an object or part of an image from the larger world scene.
    - *Transformation:*
       - The object is scaled to fit the dimensions of the viewport. This scaling adjusts the object’s size to match the viewport’s proportions.
       - The object is then translated to align with the viewport’s position on the screen.
    - *Mapping Sequence:*
        - WCS → NDCS → PDCS
        - WCS (World Coordinate System): Represents the original, infinite space containing all objects.
        - NDCS (Normalized Device Coordinate System): A normalized, finite space simplifying the mapping.
        - PDCS (Physical Device Coordinate System): The finite, device-specific space where the object appears on the screen.
   
#### Window to Viewport Transformation
- The Window to Viewport Transformation is the process of converting 2D world coordinates to device coordinates.
- It maps objects inside the world window to the corresponding viewport on the screen.
- It also ensures that selected portions of the world scene display correctly in the designated area on the screen.

#### General Terms
- The Cartesian coordinates used to define the object in the world space, such as $Xw_{min}$, $Xw_{max}$, $Yw_{min}$, $Yw_{max}$.
- The screen coordinates where the object will be displayed, such as $Xv_{min}$, $Xv_{max}$, $Yv_{min}$, $Yv_{max}$.

### General Terms

##### World Coordinate:
- The Cartesian coordinate system relative to which the graphical objects are defined.
- Example Coordinates: $Xw_{min}$, $Xw_{max}$, $Yw_{min}$, $Yw_{max}$ represent the minimum and maximum $x$ and $y$ coordinates in the world space.

##### Device Coordinate:
- The coordinate system of the display device (e.g., screen) where objects are ultimately displayed.
- Example Coordinates: $Xv_{min}$, $Xv_{max}$, $Yv_{min}$, $Yv_{max}$ represent the minimum and maximum $x$ and $y$ coordinates in the viewport on the screen.

##### Window:
- The area in the world coordinate system that is selected for display. It defines "WHAT" portion of the scene should be displayed.

##### Viewport:
- The area in the device coordinate system where the contents of the window will be mapped and displayed. It defines "WHERE" the selected part of the scene will appear on the device.

### Mathematical Calculation of Window to Viewport Transformation

- In cases where the size of the viewport differs from the size of the window, we need to adjust the window's content to fit the viewport. 
- This is achieved through scaling, a process that either enlarges or shrinks the contents of the window to match the viewport dimensions.

#### Transformation Notation:
- $(x_w, y_w)$ - A point in the Window (world coordinate system).
- $(x_v, y_v)$ - The corresponding point in the Viewport (device coordinate system).

> Our goal is to calculate $(x_v, y_v)$ so that the relative position of the point within the window is maintained in the viewport.

#### Mathematical Formula:
To map (x_w, y_w) from window coordinates to viewport coordinates, we use the following transformations for the x and y coordinates:

1. X-coordinate Transformation:
```math
   $$
   x_v = Xv_{\text{min}} + (x_w - Xw_{\text{min}}) \cdot S_x
   $$
```

3. Y-coordinate Transformation:
```math
   $$
   y_v = Yv_{\text{min}} + (y_w - Yw_{\text{min}}) \cdot S_y
   $$
```

   Where:
   - $S_x = \frac{Xv_{max} - Xv_{min}}{Xw_{max} - Xw_{min}}$ is the scaling factor for the x-coordinate.
   - $S_y = \frac{Yv_{max} - Yv_{min}}{Yw_{max} - Yw_{min}}$ is the scaling factor for the y-coordinate.


### Viewing and Clipping
- In computer graphics, clipping is used to remove objects, lines, or segments that lie outside the designated viewing area, called the viewing pane or viewing volume.
- Importance: This process is essential because the viewing transformation does not inherently consider the position of points relative to the viewer’s position, particularly those behind the viewer. Clipping eliminates these points before rendering the scene, improving both performance and visual accuracy.

#### Types of Clipping
1. Point Clipping:
- Point clipping determines whether a point lies within the boundaries of a given window (viewing area). If the point is within these boundaries, it is included in the display; if not, it is excluded.
- Conditions for Point Clipping:
  - Given a point $(X, Y)$ and a window defined by minimum and maximum x and y coordinates $Wx1$, $Wx2$, $Wy1$, $Wy2$:
  - The x-coordinate of the point is within the window if - $Wx1 \leq X \leq Wx2$.
  - The y-coordinate of the point is within the window if: - $Wy1 \leq Y \leq Wy2$.
  - If both conditions are met, the point $(X, Y)$ is within the window and is retained.
  - If either condition fails, the point is outside the window and is clipped (removed).

2. Line Clipping:
- Line clipping involves determining which portions of a line lie within a given window and discarding the parts outside of it.
- Process:
    - The line segment is checked to see if it crosses the window boundaries.
    - Portions of the line inside the window are retained, while the segments outside the window are clipped away.
   - Methods:
     - Cohen-Sutherland Algorithm: A common line clipping algorithm that categorizes line segments based on their positions relative to the window boundaries and determines the visible portions.
     - Liang-Barsky Algorithm: Another efficient algorithm that uses parameterized line equations to calculate intersections with the window edges, determining the visible segments quickly.

### Cohen-Sutherland Line Clipping Algorithm
- The Cohen-Sutherland Line Clipping Algorithm is a method used to clip lines based on a defined rectangular clipping window. 
- It efficiently determines whether a line segment should be:
    - Accepted if it is entirely inside the window,
    - Rejected if it is completely outside, or
    - Partially clipped if only part of it lies within the window.
- The clipping region is defined by:
  - Minimum coordinates: $(XW_{min}, YW_{min})$
  - Maximum coordinates: $(XW_{max}, YW_{max})$

#### Region Code
- Each endpoint of a line segment is assigned a *4-bit region code* based on its position relative to the clipping window. 
- The 4 bits represent the Top/Above, Bottom, Right, and Left of the region, often abbreviated as TBRL/ABRL.
- The bit positions in the region code correspond to:
  - Top (T) - Set to 1 if the point is above the window else 0 if not.
  - Bottom (B) - Set to 1 if the point is below the window else 0 if not.
  - Right (R) - Set to 1 if the point is to the right of the window else 0 if not.
  - Left (L) - Set to 1 if the point is to the left of the window else 0 if not.

#### Possible Outcomes for a Line Segment
1. Completely Inside:
    - Both endpoints have a region code of 0000 (indicating they are within the window).
    - Action: Accept the line without any modification.

2. Completely Outside:
    - The logical AND operation of both endpoints' region codes yields a non-zero result (meaning both endpoints are outside, in the same region).
    - Action: Reject the line entirely.

3. Partially Inside:
   - The line passes through the clipping window with only one endpoint inside.
   - Action: Perform clipping by finding the intersection points with the window boundaries and keep only the portion of the line within the window.

#### Algorithm Steps
1. Assign Region Codes:
   - For each endpoint of the line segment, determine its region code based on its position relative to the clipping window.

2. Initial Check for Acceptance:
   - If both endpoints have region code 0000, accept the line as it is entirely inside the window.

3. Initial Check for Rejection:
   - Perform the logical AND operation on the region codes of both endpoints. If the result is not 0000, reject the line as it lies completely outside the window.

4. Clipping Process for Partially Inside Lines:
    - Select an endpoint that is outside the window (one with a non-zero region code).
    - Based on the region code, find the intersection point of the line with the window boundary. This can be done by calculating the intersection with the corresponding boundary (Top, Bottom, Left, or Right).
    - Replace the selected endpoint with the calculated intersection point and update its region code.
    - Repeat Steps 2 and 3 until the line segment is either accepted (both endpoints have a region code of 0000) or rejected (non-zero result from the AND operation).

5. Repeat for All Lines:
   - Continue the above steps for each line segment to be clipped.

### Liang-Barsky Line Clipping Algorithm
- The Liang-Barsky Line Clipping Algorithm is a computational method used in computer graphics to clip lines within a rectangular window. 
- It is considered more efficient than the Cohen-Sutherland Line Clipping Algorithm because it reduces the number of intersection calculations needed.
#### Parametric Equations
- The algorithm uses the parametric form of a line:
```math
  $$
  x = x_1 + t \cdot X, \quad y = y_1 + t \cdot Y
  $$
```

  Where:
  - $X = x_2 - x_1$ 
  - $Y = y_2 - y_1$
  - $t$ is a parameter that varies between $0$ and $1$.

- For a line segment to be within the clipping window:
```math
  $$
  x_{min} \leq x_1 + tX \leq x_{max}
  $$
```
```math
  $$
  y_{\text{min}} \leq y_1 + tY \leq y_{\text{max}}
  $$
```

#### Conditions for Clipping
- The conditions above are expressed using two parameters, $p$ and $q$, as:
```math
  $$
  t \cdot p_i < q_i \quad where \; i = 1, 2, 3, 4, ...
  $$
```

#### Interpreting the Values of $p_i$
- If $p_i = 0$:
  - The line is parallel to the $i^{th}$ boundary.
- If $q_i < 0$:
  - The line is completely outside the boundary and can be discarded.
#### Calculating the Parameter $t$
- For non-zero values of $p_i$, the line intersects the clipping boundary, and we calculate:
```math
  $$
  t = \frac{q_i}{p_i}
  $$
```
- The algorithm finds two values:
  - $t_1$: The largest value among intersections with boundaries where $p_i < 0$.
  - $t_2$: The smallest value among intersections where $p_i > 0$.

- If $t_1 < t_2$:
  - The line segment within the clipping window can be computed using:
```math
    $$
    x_1' = x_1 + t_1 \cdot X, \quad y_1' = y_1 + t_1 \cdot Y
    $$
```
```math
    $$
    x_2' = x_1 + t_2 \cdot X, \quad y_2' = y_1 + t_2 \cdot Y
    $$
```
  - These endpoints $(x_1', y_1')$ and $(x_2', y_2')$ form the clipped line segment that can be drawn.
#### Advantages of the Liang-Barsky Algorithm
- More efficient than the Cohen-Sutherland algorithm because it reduces intersection calculations.
- It requires only one division to update the parameters $p_1$ and $p_2$.
- The window intersections are computed only once, improving computational speed.

### Polygon Clipping (Sutherland-Hodgman Algorithm)
- Polygon Clipping involves cutting a polygon to fit within a defined clipping window. 
- The Sutherland-Hodgman Algorithm is widely used for clipping two-dimensional polygons, ensuring that any part of the polygon outside the clipping window is discarded.
- The Sutherland-Hodgman Algorithm is specifically designed for polygon clipping against a rectangular clipping window.
- The process involves clipping the polygon edges against each boundary (left, right, top, and bottom) of the window sequentially.
- The vertices of the polygon are processed one at a time to generate new vertices, ensuring that only the parts of the polygon within the clipping window are retained.
#### Step-by-Step Explanation
- The polygon is first clipped against the left edge of the clipping window to get a set of new vertices.
- These newly obtained vertices are then used to clip against the right edge.
- The process continues similarly for the top edge and then the bottom edge of the clipping window.
#### Polygon Clipping Process
- If an edge is completely inside the window, it is retained.
- If an edge intersects the window boundary, an intersection point is calculated. The portion of the edge outside the window is clipped, and only the part inside is kept.
- The process generates new vertices that define the clipped polygon.

> The figures illustrating clipping against left, right, top, and bottom edges are essential for visualizing how each edge is processed sequentially.

### Text Clipping
- Text Clipping refers to the process of clipping text to fit within a defined boundary or window. 
- The approach used depends on the requirements of the application and the method used to generate characters. 
- The three main methods for text clipping are:
#### 1. All-or-None String Clipping
- In this method, either the entire string is kept or rejected based on whether it fits inside the clipping window.
- Example:
  - If a string (like "STRING2") is entirely within the window, it is kept.
  - If another string (like "STRING1") is only partially within the window, it is rejected entirely.
#### 2. All-or-None Character Clipping
- This method focuses on individual characters rather than the entire string.
- If the string is fully inside the clipping window, it is retained.
- If part of the string extends outside the window:
  - Only the characters completely outside are rejected.
  - If a character is on the boundary, the entire character is discarded, but the rest of the string is kept.
#### 3. Partial Text Clipping
- In this method, clipping is performed on the individual portions of characters that extend beyond the boundary.
- If a string is entirely inside the window, it is kept.
- If part of a character extends beyond the window:
  - Only the portion of the character that is outside is clipped.
  - The part of the character within the window is retained.

### Bitmap Graphics
- Bitmap Graphics refers to the use of pixels to represent and display images on a computer screen. 
- In this type of graphics, images are stored as a collection of individual pixels, where each pixel has its own color value. 
- This technique is called "bitmap" because the image is essentially mapped out bit by bit.
- A bitmap is essentially a grid of tiny squares (pixels), each holding a color value.
- Bitmaps are used extensively in computer graphics for storing and displaying images on screens.
- The computer stores the color information of each pixel to recreate the image when displayed.
##### Example: 
Drawing a Smiley Face Using Bitmap Graphics
- To understand how bitmaps work, consider an example of a smiley face drawn using bitmap graphics.
  - Each pixel on the screen is assigned a specific color value to form the shape of the smiley.
  - The computer stores the image by recording the color value of every pixel that forms the smiley.
#### Storage Representation Using Bitmaps
- The smiley face is stored in the computer using bits that represent different sections of the image.
- For example:
  - Blue lines in the smiley face may be represented as B1, B2 and the edges as E1, E2.
  - The smiley itself is stored using specific bit patterns for its features. For instance:
  - A4, B5, C6, D6, E5, F4 might denote the coordinates of different parts of the smiley face (like eyes, mouth, etc.).
  
> Figures illustrating the bit-by-bit representation and storage are essential to understand how computers handle bitmap images.

#### Disadvantages of Bitmap Graphics
- **Resizing Issues:**
  - Bitmap images cannot be resized without losing quality.
  - Enlarging a bitmap image results in pixelation, where the individual pixels become visible, making the image appear blurry or jagged.
- **Large File Sizes:**
  - Colored bitmaps can take up a lot of storage space because they store color information for each individual pixel.
  - The more colors and higher resolution an image has, the larger the file size will be.

