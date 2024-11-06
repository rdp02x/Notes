# Unit I - Introduction to Computer Graphics.md

- It is the study of creation and manipulation of images using computers. It involves:
	- Modeling — Creating the shapes and geometry in 3D.
	- Rendering — Converting 3D models into 2D images.
	- Animations — Showing how objects change over time.
- It makes information more understandable.
- Simplifies complex data with help of graphs and charts.
- Helps in creating automated designs and blueprints.
- Visualizes complex mathematical models.
- Simulates motion dynamics for experimenting with moving objects.

## Basic Computer Graphics
- It includes several essential components like processor, memory, I/O Devices.
- A processor performs basic graphics operations.
- Memory / Frame Buffer stores the content to be displayed.
- I/O devices are as usuals.

## Computation Stage
- A **frame buffer** is a dedicated memory block holding the display content for a frame. (Buffer 640 x 480 pixels allocates 640 x 480 bits)
- **Bit Depth** - Number of pixels per bit.
	- 16 Bits per pixel —> High Color
	- 32 Bits per pixel —> True Color

## Key Terms
1. **Pixel** - Smallest addressable unit/element on a display screen.
2. **CRT** - Cathode Ray Tube that uses RGB phosphor dots to create an image. 
3. **LCD** - Liquid Crystal Display that uses single color elements to create an image.
4. **Screen Resolution** - Measured by the number of pixels horizontally(m) and vertically(n) on a screen.

## Graphics Types

#### 1. Vector Graphics
- Uses the primitive shapes such as lines, points, and circle to define the image.
- Attributes:
	- Primitive shapes — Points, Lines, Circles, etc.
	- Size and Position — Each shape has a specific dimension and coordinate.
	- Resolution Independent — The quality remains the same.
- Rendering:
	- Before display, vector graphics need to be converted into a raster image.
- Formats:
	- Common formats are OpenGL, SVG, PS, and VRML.
#### 2. Raster Graphics
- Represents images in 2D array of pixels, where each pixel is a small dot that collectively forms an image.
- Attributes:
	- Pixels — Specific image content.
	- Resolution Independent — The quality remains the same.
	- Detail — Provides richer details compared to vector graphics.
- Formats:
	- Common formats includes BMP, GIF, JPEG, etc.

## Display Technologies

#### 1. Random Scan Display
- Also known as vector display
- Uses line drawing technologies to create images.
- Mechanism:
	- Line drawing instructions — Stored in memory to direct the drawings.
	- Electron beams directed only to the parts of the screen where the image need to be drawn, creating the picture.
#### 2. Raster Scan Display
- It was developed in early 70s.
- Still dominates the tech in today’s graphics system.
- Mechanism:
	- Raster — The picture is produced as an array of pixels.
	- Pixels — Corresponds to a specific locations.
	- Frame Buffer — Pixel memory stored in this.
- Attributes:
	- Almost all the modern graphics system uses the raster display based technologies due to its ability to handle complex images and high efficiency.

## Refresh Rate
- The **Refresh Rate** is the number of times per second that an image is redrawn on the display.
- It Represents how frequently the entire contents of the frame buffer are displayed on the screen to avoid flicker.
- To ensure a steady and flicker-free images, the same path must be refreshed at least 60 times per second.
- Modern raster-scan display typically refreshed at a rate of 60 - 80 FPS and upto 120 FPS with some advanced systems.
- Refresh Rates units are measured  in Hertz(Hz), where one hertz equals one cycle per second.

## Cathode Ray Tube (CRT)
- The **Cathode Ray Tube** is a vacuum tube containing an electron gun and a fluorescent screen, with mechanics that accelerates and deflects the electron beam, and create the image.
##### Features
1. Electron Gun —
	- Produces electrons at high, fixed velocity through thermionic emission.
2. Deflection System —
	- Contains two perpendicular sets of electric / magnetic fields.
	- Controls both horizontals and vertical deflection by varying the voltage applied to the fields.
3. Fluorescent Screen —
	- Displays where the electrons hits the CRT.
	- Coated with materials like zinc sulfide / phosphorus that emits lights when struck by electrons.
4. Glass Tube and Base —
	- Long, clear tube with an elevated glass envelope, making it larger deep and heavy.
	- Contains an assembly in the neck to produce electron stream
	- Electricals connections are made through metal pins extended out at the back of the tube.

##### How CRT works
1. **Image Creation -** A CRT monitor contains a millions of tiny red, green and blue phosphorus  dots that glows when struck by an electron beam.
2. **Electron Beam -** The cathode is heated filament in a vacuum inside the glass tube, emitting electrons that are attracted to the positively charged screen.
3. **Scanning -** The electron beam scans, creating images from many fluorescent dots. Each scan alternatives between odd and even lines.

##### Applications of CRT
- Television
- Computer Monitors
- Radar Displays
- Cathode Ray Oscilloscopes

##### Advantages and Disadvantages of CRT

| Advantages                                               | Disadvantages                                           |
| -------------------------------------------------------- | ------------------------------------------------------- |
| Brightness can be easily increased by reflecting monitor | Emits a small amount of X-ray radiations.               |
| Can produce more colors                                  | Constantly refreshing                                   |
| Better image quality compared to LCD and Plasma Screens  | Operates at a very high voltage leading to over heating |
| Excellent color rendering                                | Large, Heavy, and Fragile                               |

## Display Methods of CRT

#### Raster Scan Display
- This method is similar to television technology. The electron beam moves line-by-line across the screen.
- As the beam moves, the intensity of the beam is turned on and off as it need to create images.
- The picture definition is stored in a memory area called the **Refresh Buffer**.

#### Random Scan Display
- Also known as stroke writing, calligraphic display, or vector display
- Here, the electron beam is only directed to the path where the picture is to be drawn.
- Draws only one line at a time.
- The refresh rate depends on the number of lines to be displayed.

### Color CRT Monitor

- CRT monitors can display different colors by using various phosphors that emit different colored lights.
- By combining these emitted lights, a range of colors can be generated.
- There are two main methods to produce color on the screen:
  1. Beam Penetration Method
  2. Shadow Mask Method

| **Method**                 | **Beam Penetration Method**                                                                                                                               | **Shadow Mask Method**                                                        |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Usage**                  | Commonly used with random scan monitors.                                                                                                                  | Commonly used in television systems.                                          |
| **Phosphor Layers / Dots** | Two layers of phosphors (red and green) on the CRT screen.                                                                                                | Each pixel has three phosphor dots (red, green, and blue).                    |
| **Electron Speed**         | - Slow electrons: excite the outer red layer. <br> - Fast electrons: excite the inner green layer.<br> - Medium speed: produces orange and yellow colors. | Not applicable (color is created by mixing intensities of beams).             |
| **Color Control**          | Controlled by adjusting the beam’s accelerating voltage, which varies the electron speed.                                                                 | Varying beam intensity from each electron gun produces a range of colors.     |
| **Color Range**            | Limited to four colors (red, green, orange, yellow).                                                                                                      | Produces a wider range of colors by combining red, green, and blue.           |
| **Advantage**              | Cost-effective.                                                                                                                                           | Higher color variety and better image quality.                                |
| **Disadvantage**           | Limited color range and lower picture quality.                                                                                                            | More complex and potentially higher cost compared to beam penetration method. |

## Direct View Storage Tubes (DVST)

#### Function: 
  - DVSTs are used to maintain the picture on the screen without needing frequent refreshes.
  - Picture information is stored as a charge distribution behind the phosphor-coated screen.
  - DVSTs use two electron guns:
    - The **primary gun** stores the picture pattern.
    - The **flood gun** refreshes and maintains the stored image on the screen.
#### Advantages
  - **No Refreshing Needed**: Unlike raster displays, DVSTs do not require continuous refreshing, which helps in displaying high-resolution images without flickering.
#### Disadvantages:
  - **No Color Display**: DVSTs are limited to black-and-white images and cannot display colors.
  - **Editing Limitations**: Selected parts of the image cannot be erased individually; the entire image must be redrawn if modifications are needed. This erasing and redrawing process can take several seconds for complex images, making DVSTs less efficient for dynamic content.
  - **Popularity**: Due to these limitations, DVSTs are less commonly used than raster systems, which offer more flexibility and efficiency for modern graphics applications.

## Persistence
- It refers to how long the phosphorus continuously emits light after being excited by the electron beam.
- It is defined as the time taken by the emitted light to decay to ⅒ of its original intensity.
- Low persistence required a higher refresh rate to maintain a stable image. It is useful for animations due to quick decay.
- High persistence is suitable for complex and static images.

## Resolution
- The maximum number of distinct points that can be displayed without overlapping is called **Resolution**.
- It is measured in points per centimeter horizontally and vertically
- Example - 1920 x 1080, 640 x 800, etc.

## Aspect Ratio
- It is the ratio of vertical points to horizontal points.
- a general, default aspect ratio is 3:4.

## Interlacing
- A technology used in CRT displays to improve the image quality without increasing the bandwidth is called **Interlacing**.
- Horizontal Raytracing:
	- The electron beam returns to the left side of the screen after completing each line.
- Vertical Raytracing:
	- The electron beam returns to the left side of the screen to begin the next frame after completing each frame.
- Interlaced Scanning:
	- Instead of displaying all the lines in one pass, the screen is refreshed in two passes
	- First pass displays the odd lines
	- Second pass displays the even lines.

## Flat Panel Displays
#### Definition: 
  - Flat panel displays are lightweight, low-power video devices that have a slimmer design compared to traditional CRTs (Cathode Ray Tubes).
  - Their compact size allows them to be mounted on walls, integrated into wearable devices, or used in portable electronics.  
#### Applications: 
  - Commonly used in devices like pocket notepads, portable TVs, calculators, video games, laptops, and monitors.
### Categories of Flat Panel Displays:  
#### 1. Emissive Displays:
  - **Description**: These displays generate light by converting electrical energy directly into visible light.
- **Examples**:
	- **Plasma Panel Display**: Uses small cells containing electrically charged ionized gases to produce light.
    - **LED (Light Emitting Diode)**: Each diode emits light when electrical current passes through it.
    - **Thin Film Electroluminescent Devices**: Emit light when an electric field excites the thin-film phosphors.
#### 2. Non-Emissive Displays:
- **Description**: These displays do not produce light directly but instead use optical effects to modulate external light sources.
- **Examples**:
	- **LCD (Liquid Crystal Display)**: Uses liquid crystals that change alignment when electrically charged, allowing the display to control the passage of light from an external source to form images. This technology is common in devices like watches, calculators, and monitors.

### Applications of Emissive Devices
#### 1. Plasma Panel (Gas Discharge Display)
   - Constructed using two glass plates with a gas mixture (often containing neon) between them.
   - Vertical ribbons are placed on one glass panel, and horizontal ribbons on the other.
   - When voltage is applied to a pair of horizontal and vertical conductors, gas at the intersection glows, creating plasma.
   - Picture information is stored in a refresh buffer, and firing voltage refreshes pixel positions at 60 frames per second.
   - Initially displayed only black and white but now supports color and grayscale.
   - Uses alternating current for faster firing voltage application and brighter display.
#### 2. Light Emitting Diode (LED)
   - Diodes arranged in a matrix form the pixel positions.
   - Picture information is stored in a refresh buffer.
   - Voltage levels read from the buffer are applied to diodes to produce the light display, similar to CRT.
#### 3. Liquid Crystal Display (LCD)
   - Two glass plates with polarizers at right angles sandwich a layer of liquid crystal.
   - Horizontal conductors are built into one plate, vertical conductors into the other.
   - Intersection of two conductors defines a pixel position.

### Types of LCDs and Their Operation

| **LCD Type**           | **Description**                                                                                                                                                                                                                                                                                                                                                           | **Advantages**                                                                                                                          |     |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --- |
| **Passive Matrix LCD** | - Polarized light is twisted in the liquid crystal layer to allow passage through an opposite polarizer, creating an "On" state.<br> - "Off" state is achieved by adjusting voltage to prevent light passage.<br> - Picture definitions are stored in a refresh buffer and updated at 60 frames per second.<br> - Colors are displayed using different dyes or materials. | - Cost-effective<br> - Suitable for low-power applications like digital clocks and calculators.                                         |     |
| **Active Matrix LCD**  | - Incorporates a thin-film transistor (TFT) at each pixel location.<br> - Transistors control pixel voltage, maintaining brightness and reducing charge leakage.<br> - This setup provides sharper, clearer images and faster refresh rates compared to passive matrices.                                                                                                 | - Used in high-resolution applications like laptops, monitors, and smartphones.<br> - Provides higher image quality and color accuracy. |     |

