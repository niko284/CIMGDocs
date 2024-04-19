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

### macOS

- Install CImg by downloading [XQuartz](https://www.xquartz.org) which gives us access to XWindows.
- Download the latest .pkg file on the site and follow the prompts to install XQuartz.
- After the installation, go to where your CImg file was downloaded, ideally in your desktop.
- After accessing your CImg file, make sure to select the **"Make" type**, and select **dmacos**, which is debug Mac OS.

You are now done installing CImg! To compile a .cpp file like **hello.cpp**, for example, you would use the following command in your terminal:
#### Compiling a .cpp file in macOS:
```jsx title="hello.cpp"
g++ -o hello hello.cpp -O2 -lm -lpthread -I/usr/XR6/include -L/usr/X11R6/lib -lm -lpthread -lX11
```
