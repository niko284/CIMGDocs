---
sidebar_position: 2
---

# CImg

## Constructors

### Default

**Description:**
The `CImg()` constructor creates an empty image object. This can be used as a base to initialize an image with specific dimensions, colors, or other properties later.

**Return Type:**
An instance of `CImg`.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    // Create an empty image
    CImg<unsigned char> empty_image;

    return 0;
}
```

### Height, Width, and Depth

**Description:**
The `CImg()` constructor creates an image with specified width, height, depth, and spectrum (number of channels).

| Argument | Type             | Description                                         |
| -------- | ----------------|-----------------------------------------------------|
| size_x   | `unsigned int`  | The width of the image.                             |
| size_y   | `unsigned int`  | The height of the image (default is 1).             |
| size_z   | `unsigned int`  | The depth of the image (default is 1).              |
| size_c   | `unsigned int`  | The number of color channels (default is 1).        |

**Return Type:**
An instance of `CImg`.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    // Create a 640x480 image with a single depth and color channel
    CImg<unsigned char> image(640, 480);

    return 0;
}
```

### File Name

```CImg(const char * filename)```

**Description:**
The `CImg()` constructor creates an image by reading from a specified image file. The pixel values and image dimensions are initialized based on the contents of the file. It requires a valid file name (as a C-string) and can throw an exception if the file cannot be read or if the format is not recognized.

| Argument | Type       | Description                                                                                      |
| -------- | ----------|--------------------------------------------------------------------------------------------------|
| filename | `const char *`  | The file name (as a C-string, or string) of the image to read and initialize the new image instance. |

**Return Type:**
An instance of `CImg`.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    // Construct an image from an existing image file
    CImg<unsigned char> image("example.jpg");

    return 0;
}
```

## Methods

### .width

**Description:**
The `width()` method returns the number of columns in an image, representing its width along the X-axis. This value indicates the horizontal dimension of the image.

**Return Type:**
An `int` representing the number of columns in the image.

**Example:**
```cpp
#include <CImg.h>
#include <iostream>

using namespace cimg_library;
using namespace std;

int main()
{
    CImg<unsigned char> image(640, 480, 1, 3);        // Create a 640x480 RGB image.
    cout << "Image width: " << image.width() << endl; // Output the width of the image.

    return 0;
}
```

### .height

**Description:**
The `height()` method returns the number of rows in an image, representing its height along the Y-axis. This value indicates the vertical dimension of the image.

**Return Type:**
An `int` representing the number of rows in the image.

**Example:**
```cpp
#include <CImg.h>
#include <iostream>

using namespace cimg_library;
using namespace std;

int main() {
    CImg<unsigned char> image(640, 480, 1, 3); // Create a 640x480 RGB image.
    cout << "Image height: " << image.height() << endl; // Output the height of the image.

    return 0;
}
```

## Drawing Methods

### .draw_point

**Description:**
The `draw_point()` method draws a single point on an image at the specified coordinates `(x0, y0)`. The point is drawn with the specified color and opacity.

| Argument   | Type            | Description                                                  |
|------------|-----------------|-------------------------------------------------------------|
| x0         | `int`           | The X-coordinate of the point to be drawn.                    |
| y0         | `int`           | The Y-coordinate of the point to be drawn.                    |
| color      | `const tc*`     | A pointer to an array representing the color in a specific format (e.g., RGB, RGBA). |
| opacity    | `float`         | The opacity of the drawn point, with a default value of 1 (fully opaque). |

**Return Type:**
A reference to the current `CImg<T>` instance, allowing method chaining.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    CImg<unsigned char> img(640, 480, 1, 3); // Create a 640x480 RGB image.
    unsigned char red[] = {255, 0, 0}; // RGB color for red.

    img.draw_point(320, 240, red, 0.75); // Draw a semi-transparent red point at the center.
    
    CImgDisplay disp(640, 480, "Draw Point Example"); // Create a display window.
    img.display(disp); // Display the image in the CImgDisplay window.

    while (!disp.is_closed()) {
        disp.wait(); // Keep the window open until closed.
    }

    return 0;
}
```

### .display

**Description:**
The `display()` method displays the current `CImg` image in a `CImgDisplay` window. This allows visualization of the image in a graphical user interface. It takes a reference to an existing `CImgDisplay` window as its argument and returns a constant reference to the current `CImg` instance.

| Argument  | Type            | Description                               |
|-----------|-----------------|-----------------------------------------|
| disp      | `CImgDisplay&`  | A reference to the `CImgDisplay` window to display the image in. |

**Return Type:**
A constant reference to the current `CImg<T>` instance, allowing method chaining.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    CImg<unsigned char> img(640, 480, 1, 3); // Create a 640x480 RGB image.
    unsigned char red[] = {255, 0, 0}; // RGB color for red.

    img.draw_point(320, 240, red, 1.0); // Draw a red point at the center of the image.

    CImgDisplay disp(640, 480, "Display Example"); // Create a display window.
    img.display(disp); // Display the image in the CImgDisplay window.

    while (!disp.is_closed()) {
        disp.wait(); // Keep the window open until it's closed.
    }

    return 0;
}
```

### .draw_line

**Description:**
The `draw_line()` method draws a 2D line on the current `CImg` instance. It takes the starting and ending coordinates, a pointer to the color array, and opacity.

| Parameter  | Type              | Description                                              |
|------------|------------------|----------------------------------------------------------|
| x0         | `int`             | X-coordinate of the starting point of the line.          |
| y0         | `int`             | Y-coordinate of the starting point of the line.          |
| x1         | `int`             | X-coordinate of the ending point of the line.            |
| y1         | `int`             | Y-coordinate of the ending point of the line.            |
| color      | `const tc*`       | Pointer to the color array.|
| opacity    | `float`           | Opacity of the line drawing. A value between 0 and 1.    |

**Return Type:**
A reference to the current `CImg<T>` instance, allowing method chaining.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(640, 480, 1, 3); // Create a 640x480 RGB image.
    unsigned char green[] = {0, 255, 0}; // RGB values for green.
    img.draw_line(10, 10, 630, 470, green, 0.8); // Draw a line with 80% opacity.
    img.display("Line Example"); // Display the image.
    
    return 0;
}
```

### .draw_arrow

**Description:**
The `draw_arrow()` method draws a 2D arrow on the current `CImg` instance. It takes the starting and ending coordinates, a pointer to the color array, and additional parameters for customizing the arrow head's angle and length.

| Parameter  | Type              | Description                                             |
|------------|------------------|---------------------------------------------------------|
| x0         | `int`             | X-coordinate of the starting point (tail) of the arrow. |
| y0         | `int`             | Y-coordinate of the starting point (tail) of the arrow. |
| x1         | `int`             | X-coordinate of the ending point (head) of the arrow.   |
| y1         | `int`             | Y-coordinate of the ending point (head) of the arrow.   |
| color      | `const tc*`       | Pointer to `spectrum()` consecutive values of type `T`, defining the arrow color. |
| opacity    | `float`           | Opacity of the arrow drawing (range 0-1).               |
| angle      | `float`           | Aperture angle of the arrow head (in degrees).          |
| length     | `float`           | Length of the arrow head. If negative, it's a percentage of the arrow length. |

**Return Type:**
A reference to the current `CImg<T>` instance, allowing method chaining.

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(640, 480, 1, 3); // Create a 640x480 RGB image.
    unsigned char red[] = {255, 0, 0}; // RGB values for red.
    img.draw_arrow(10, 10, 630, 470, red, 0.9, 30, -10); // Draw an arrow with specified parameters.
    img.display("Arrow Example"); // Display the image.
    
    return 0;
}
```

### .draw_spline

**Description:**
The `draw_spline()` method in CImg draws a 2D spline between two points with specified tangents at each end. The curvature of the spline is determined by these tangents.

| Parameter   | Type         | Description                                                                                   |
|-------------|--------------|-------------------------------------------------------------------------------------------------|
| x0          | `int`       | X-coordinate of the starting spline point.                                                      |
| y0          | `int`       | Y-coordinate of the starting spline point.                                                      |
| u0          | `float`     | X-component of the starting point tangent.                                                      |
| v0          | `float`     | Y-component of the starting point tangent.                                                      |
| x1          | `int`       | X-coordinate of the ending spline point.                                                        |
| y1          | `int`       | Y-coordinate of the ending spline point.                                                        |
| u1          | `float`     | X-component of the ending point tangent.                                                        |
| v1          | `float`     | Y-component of the ending point tangent.                                                        |
| color       | `const tc*` | Pointer to `spectrum()` consecutive values defining the drawing color.                          |
| opacity     | `float`     | Drawing opacity (default is 1 for full opacity).                                                  |
| precision   | `float`     | Precision of the spline curve (default is 0.25, lower means smoother curve).                      |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(400, 400, 1, 3, 0); // Creates a 400x400 image with 3 color channels.
    const unsigned char red[] = {255, 0, 0}; // Red color
    img.draw_spline(50, 50, 30, 40, 350, 350, -40, -30, red, 1); // Draws a red spline.
    img.display("2D Spline Example"); // Displays the image.
    return 0;
}
```

### .draw_triangle

**Description:**
The `draw_triangle()` method in CImg draws a filled triangle in a 2D image, given three vertices and a color.

| Parameter  | Type         | Description                                                                                   |
|------------|--------------|-------------------------------------------------------------------------------------------------|
| x0         | `int`        | X-coordinate of the first vertex.                                                                |
| y0         | `int`        | Y-coordinate of the first vertex.                                                                |
| x1         | `int`        | X-coordinate of the second vertex.                                                               |
| y1         | `int`        | Y-coordinate of the second vertex.                                                               |
| x2         | `int`        | X-coordinate of the third vertex.                                                                |
| y2         | `int`        | Y-coordinate of the third vertex.                                                                |
| color      | `const tc*`  | Pointer to the color array.                          |
| opacity    | `float`      | Drawing opacity (default is 1 for full opacity).                                                  |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(400, 400, 1, 3, 0); // Creates a 400x400 image with 3 color channels.
    const unsigned char blue[] = {0, 0, 255}; // Blue color
    img.draw_triangle(50, 50, 350, 50, 200, 350, blue, 1); // Draws a blue triangle.
    img.display("2D Triangle Example"); // Displays the image.
    return 0;
}
```

### .draw_rectangle

**Description:**
The `draw_rectangle()` method in CImg allows you to draw a filled rectangle on a 2D image, given two opposite corners and a color.

| Parameter | Type           | Description                                                                                     |
|-----------|----------------|---------------------------------------------------------------------------------------------------|
| x0        | `int`          | X-coordinate of the first corner.                                                                  |
| y0        | `int`          | Y-coordinate of the first corner.                                                                  |
| x1        | `int`          | X-coordinate of the opposite corner.                                                               |
| y1        | `int`          | Y-coordinate of the opposite corner.                                                               |
| color     | `const tc*`    | Pointer to the color array.                           |
| opacity   | `float`        | Drawing opacity (default is 1 for full opacity).                                                     |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main()
{
    CImg<unsigned char> img(400, 400, 1, 3, 0);         // Creates a 400x400 image with 3 color channels.
    const unsigned char red[] = {255, 0, 0};            // Red color
    img.draw_rectangle(50, 50, 350, 350, red, 0.5);     // Draws a semi-transparent red rectangle.
    CImgDisplay myDisplay(img, "2D Rectangle Example"); // Creates a display window for the image.
    while (!myDisplay.is_closed())                      // Display loop
    {
        myDisplay.wait(); // Wait for the user to close the window.
    }
    return 0;
}
```

### .draw_ellipse

**Description:**
The `draw_ellipse()` method in CImg allows you to draw an ellipse on a 2D image, given a center point, radii, rotation angle, and a color.

| Parameter | Type           | Description                                                               |
|-----------|----------------|---------------------------------------------------------------------------|
| x0        | `int`          | X-coordinate of the ellipse's center point.                                 |
| y0        | `int`          | Y-coordinate of the ellipse's center point.                                 |
| r1        | `float`        | Radius along the major axis.                                                |
| r2        | `float`        | Radius along the minor axis.                                                |
| angle     | `float`        | Rotation angle in degrees.                                                  |
| color     | `const tc*`    | Pointer to `spectrum()` consecutive values defining the drawing color.      |
| opacity   | `float`        | Drawing opacity (default is 1 for full opacity).                             |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(400, 400, 1, 3, 0); // Creates a 400x400 image with 3 color channels.
    const unsigned char blue[] = {0, 0, 255}; // Blue color
    img.draw_ellipse(200, 200, 150, 100, 45, blue, 0.8); // Draws a slightly transparent ellipse with rotation.
    img.display("2D Ellipse Example"); // Displays the image.
    return 0;
}
```

### .draw_circle

**Description:**
The `draw_circle()` method in CImg allows you to draw a circle on a 2D image, given a center point, a radius, and a color.

| Parameter | Type           | Description                                                               |
|-----------|----------------|---------------------------------------------------------------------------|
| x0        | `int`          | X-coordinate of the circle's center point.                                 |
| y0        | `int`          | Y-coordinate of the circle's center point.                                 |
| radius    | `int`          | Radius of the circle.                                                       |
| color     | `const tc*`    | Pointer to `spectrum()` consecutive values defining the drawing color.      |
| opacity   | `float`        | Drawing opacity (default is 1 for full opacity).                             |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(400, 400, 1, 3, 0); // Creates a 400x400 image with 3 color channels.
    const unsigned char red[] = {255, 0, 0}; // Red color
    img.draw_circle(200, 200, 100, red, 1.0); // Draws a red circle at (200, 200) with a radius of 100.
    img.display("2D Circle Example"); // Displays the image.
    return 0;
}
```

### .draw_image

**Description:**
The `draw_image()` method in CImg allows you to overlay or draw another image (a "sprite") onto the current image at a specified 3D location, with optional opacity.

| Parameter | Type              | Description                                                             |
|-----------|------------------|-------------------------------------------------------------------------|
| x0        | `int`             | X-coordinate where the sprite's top-left corner should be drawn.        |
| y0        | `int`             | Y-coordinate where the sprite's top-left corner should be drawn.        |
| z0        | `int`             | Z-coordinate where the sprite's top-left corner should be drawn.        |
| c0        | `int`             | The spectrum (color channel) where the sprite's top-left corner should be drawn.  |
| sprite    | `const CImg<t>&`  | The image to be drawn ("sprite").                                       |
| opacity   | `float`           | Drawing opacity (default is 1 for full opacity).                         |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> main_img(400, 400, 1, 3, 0); // Create a blank 400x400 image with 3 color channels.
    CImg<unsigned char> sprite(100, 100, 1, 3, 255); // Create a 100x100 sprite filled with white.

    main_img.draw_image(150, 150, 0, 0, sprite, 0.5); // Draws the sprite at (150, 150) on the main image with 50% opacity.
    main_img.display("Drawn Image Example"); // Displays the resulting image.
    return 0;
}
```

### .draw_text

**Description:**
The `draw_text()` method in CImg allows you to draw text on an image at a specified position, with given foreground and background colors, opacity, and optionally a custom font.

| Parameter            | Type                          | Description                                                                   |
|---------------------|------------------------------|-------------------------------------------------------------------------------|
| x0                   | `int`                         | X-coordinate where the text should be drawn.                                  |
| y0                   | `int`                         | Y-coordinate where the text should be drawn.                                  |
| text                 | `const char*`                  | The text string to draw.                                                      |
| foreground_color     | `const tc1*`                   | Pointer to an array defining the drawing color (foreground).                   |
| background_color     | `const tc2*`                   | Pointer to an array defining the background color of the text.                 |
| opacity              | `float`                        | Drawing opacity for the text.                                                  |
| font                 | `const CImgList<t>*`           | Pointer to a custom font (optional). If `nullptr`, the default font is used.  |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(400, 400, 1, 3, 255); // Create a white image.
    unsigned char black[] = { 0, 0, 0 }; // Black color.
    unsigned char white[] = { 255, 255, 255 }; // White color.

    img.draw_text(50, 200, "Hello, CImg!", black, white, 1.0); // Draws black text with white background at (50, 200).
    img.display("Drawn Text Example"); // Displays the resulting image.
    return 0;
}
```

### .draw_grid

**Description:**
The `draw_grid()` method in CImg allows you to draw grid lines on an image along specified x and y values. This is useful for visualizing data points or creating charts.

| Parameter           | Type                    | Description                                              |
|--------------------|-------------------------|----------------------------------------------------------|
| values_x           | `CImg<tx>`              | An image or list containing x-axis values for the grid.  |
| values_y           | `CImg<ty>`              | An image or list containing y-axis values for the grid.  |
| color              | `const tc*`              | Pointer to a color array (R, G, B)  |
| opacity            | `float`                  | Opacity for the drawn grid lines (0.0 to 1.0).           |

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImg<unsigned char> img(400, 400, 1, 3, 255); // Create a white image.
    unsigned char black[] = { 0, 0, 0 }; // Black color.

    // Create x and y grid values
    CImg<int> x_values(5); // Grid lines along x-axis at indices 50, 100, 150, 200, 250
    CImg<int> y_values(5); // Grid lines along y-axis at indices 50, 100, 150, 200, 250

    for (int i = 0; i < 5; i++) {
        x_values[i] = 50 + i * 50;
        y_values[i] = 50 + i * 50;
    }

    img.draw_grid(x_values, y_values, black, 0.8); // Draws grid lines with specified x and y values in black.
    img.display("Grid Example"); // Displays the resulting image with grid lines.
    return 0;
}
```