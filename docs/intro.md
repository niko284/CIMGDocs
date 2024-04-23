---
sidebar_position: 1
---

# Installation

Let's cover how to install **CImg**, a compact, lightweight C++ graphics library!

## Operating Systems

To get started with the installation, find your appropriate operating system installation instructions below:

### Windows

For Windows machines, there is no need to install anything on your machines as you will be working with Storm, which already has the **CImg** library built in.

To use CImg, include the following lines of code at the top of your *.cpp* files:
```cpp
#include <CImg.h>;
using namespace cimg_library;
```

We can create a program to draw rectangles of different colors wherever your mouse is clicked, named **rectangle.cpp**, and compile it based on device as specified below:
```cpp jsx title="rectangle.cpp"
#include <CImg.h>
using namespace cimg_library;

int main() 
{

    int size_x = 640;
    int size_y = 480;
    int size_z = 1;
    int numberOfColorChannels = 3; // R G B
    unsigned char initialValue = 0;

    CImg<unsigned char> image(size_x, size_y, size_z, numberOfColorChannels, initialValue);

    CImgDisplay display(image, "Click a point");

    unsigned char randomColor[3]; // declare once for optimization.

    const int RECTANGLE_SIZE = 10;

    while (!display.is_closed())
    {
        display.wait(); // Wait for any user event to occur on the display before continuing our code.
        if (display.button() && display.mouse_y() >= 0 && display.mouse_x() >= 0)
        {
            const int y = display.mouse_y();
            const int x = display.mouse_x();

            randomColor[0] = rand() % 256;
            randomColor[1] = rand() % 256;
            randomColor[2] = rand() % 256;

            // draw a rectangle centered at the clicked point
            image.draw_rectangle(x - RECTANGLE_SIZE, y - RECTANGLE_SIZE, x + RECTANGLE_SIZE, y + RECTANGLE_SIZE, randomColor);
        }
        image.display(display);
    }
    return 0;
}
```

#### Compiling a .cpp file in Windows:

```cpp
g++ rectangle.cpp -lX11
```

### macOS

- Install CImg by downloading [XQuartz](https://www.xquartz.org) which gives us access to XWindows.
- Download the latest .pkg file on the site and follow the prompts to install XQuartz.
- After the installation, go to where your CImg package folder was downloaded, ideally in your desktop. 
- Open your terminal and use the **cd** command to move your current directory to the CImg folder.
- Once you are in your CImg folder, use the **cd** command once more into your examples folder with the command `cd examples`.
    - **IMPORTANT:** After accessing your **examples** folder in the terminal, (you can verify this using the **pwd**) command, you need to install
    all of the necessary packages onto your Mac. To do this, type in `make dmacos` into your terminal, and wait for it to finish.

You are now done installing CImg! To compile a .cpp file like **rectangle.cpp**, for example, you would use the following command in your terminal:
#### Compiling a .cpp file in macOS:
```jsx title="rectangle.cpp"
g++ -o rectangle rectangle.cpp -O2 -lm -lpthread -I/usr/XR6/include -L/usr/X11R6/lib -lm -lpthread -lX11
```
