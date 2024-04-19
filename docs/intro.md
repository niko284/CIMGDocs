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

#### Compiling a .cpp file in Windows:
```jsx title="hello.cpp"
g++ hello.cpp -lX11
```

### macOS

- Install CImg by downloading [XQuartz](https://www.xquartz.org) which gives us access to XWindows.
- Download the latest .pkg file on the site and follow the prompts to install XQuartz.
- After the installation, go to where your CImg package folder was downloaded, ideally in your desktop. 
- Open your terminal and use the **cd** command to move your current directory to the CImg folder.
- Once you are in your CImg folder, use the **cd** command once more into your examples folder with the command `cd examples`.
    - **IMPORTANT:** After accessing your **examples** folder in the terminal, (you can verify this using the **pwd**) command, you need to install
    all of the necessary packages onto your Mac. To do this, type in `make dmacos` into your terminal, and wait for it to finish.

You are now done installing CImg! To compile a .cpp file like **hello.cpp**, for example, you would use the following command in your terminal:
#### Compiling a .cpp file in macOS:
```jsx title="hello.cpp"
g++ -o hello hello.cpp -O2 -lm -lpthread -I/usr/XR6/include -L/usr/X11R6/lib -lm -lpthread -lX11
```
