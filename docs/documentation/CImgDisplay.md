---
sidebar_position: 1
---

# CImgDisplay

The **CImgDisplay** class is part of the **CImg** library. It is a class used to display images or image lists into graphical display windows, as shown in **rectangle.cpp**. Below, we give a list of some of the most useful functions that can be used with a CImgDisplay object, how to construct one, and examples.

## Constructors

### Width and Height

**Description:**
This is the constructor for the ``CImgDisplay`` class when a certain height and width for the display is desired.

| Argument | Type | Description |
| -------- | ---- | ----------- |
| width     | const unsigned int  | The width of your display window. |
| height     | const unsigned int  | The height of your display window. |
| title     | string | The title of the display window. |

**Return Type:**
An object of the ```CImgDisplay``` class.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;

int main()
{
    int size_x = 640;
    int size_y = 480;
    int size_z = 1;

    CImgDisplay display(size_x, size_y, "My display");

    return 0;
}
```

### Singular Image

**Description:**
This is the constructor for the ``CImgDisplay`` class that creates a display window from an image, with additional options for customization.

| Argument | Type | Description |
| -------- | ---- | ----------- |
| image     | CImg | The **CImg** object used as a template to create the display window. |
| title     | string  | The text that appears in the title bar of the display window. |

**Return Type:**
An object of the ```CImgDisplay``` class.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;

int main()
{
    int size_x = 640;
    int size_y = 480;
    int size_z = 1;

    CImg<unsigned char> img(size_x, size_y, size_z);

    CImgDisplay display(img, "My display");

    return 0;
}
```

## Methods

### .is_closed

**Description:**
The `is_closed()` method checks whether the display window is closed (i.e., not visible on the screen). It returns `true` if the display is closed, and `false` otherwise. A closed display isn't destroyed and can be re-opened with a method like `show()`.

| Argument | Type | Description |
| -------- | ---- | ----------- |
| None     | N/A  | This method does not require any input arguments. |

**Return Type:**
A boolean value (`bool`). If `true`, the display is closed; if `false`, it's open.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    int size_x = 640;
    int size_y = 480;
    int size_z = 1;

    CImg<unsigned char> img(size_x, size_y, size_z);
    CImgDisplay display(img, "My display");

    if (display.is_closed()) {
        cout << "The display is closed." << endl;
    } else {
        cout << "The display is open." << endl;
    }

    return 0;
}
```

### .is_key

**Description:**
The `is_key()` method checks whether a specific key (identified by its keycode) is being pressed in the associated display window. It returns `true` if the specified key is being pressed, and `false` otherwise. The keycode should be passed using constants from the `CImg` class, accessed with the scoping operator `::`.

**If no keycode is passed, the method will return `true` if any key is pressed in the display window.**

| Argument | Type             | Description                                               |
| -------- | ----------------|-----------------------------------------------------------|
| Keycode (Optional)  | `unsigned int`   | The keycode to test, typically a constant from the `CImg` class. |

**Return Type:**
A boolean value (`bool`). If `true`, the specified key is being pressed; if `false`, it is not.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main()
{
    CImgDisplay disp(400, 400);
    while (!disp.is_closed())
    {
        if (disp.is_key(cimg::keyTAB))
        { // Checks if the TAB key is pressed, using a keycode from the cimg namespace.
            cout << "Tab key is being pressed." << endl;
        }
        // If no keycode is passed to is_key(), it will return true if any key is pressed.
        if (disp.is_key())
        {
            cout << "A key is being pressed." << endl;
        }
        disp.wait();
    }

    return 0;
}
```

### 

### .mouse_x

**Description:**
The `mouse_x()` method returns the X-coordinate of the mouse pointer relative to the associated display window. If the mouse pointer is outside the window area, the method returns `-1`. Otherwise, the returned value will be within the range of `[0, width() - 1]`.

| Argument | Type   | Description                    |
| -------- | ------ | ------------------------------|
| N/A      | N/A    | This method doesn't take arguments. |

**Return Type:**
An integer (`int`). The value represents the X-coordinate of the mouse pointer. If the pointer is outside the window, it will return `-1`.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    CImgDisplay disp(400, 400);

    while (!disp.is_closed()) {
        int x = disp.mouse_x(); // Gets the X-coordinate of the mouse pointer.
        if (x != -1) {
            cout << "Mouse X-coordinate is: " << x << endl;
        } else {
            cout << "Mouse pointer is outside the window." << endl;
        }
        disp.wait();
    }

    return 0;
}
```

### .mouse_y

**Description:**
The `mouse_y()` method returns the Y-coordinate of the mouse pointer relative to the associated display window. If the mouse pointer is outside the window area, the method returns `-1`. Otherwise, the returned value is in the range `[0, height() - 1]`.

| Argument | Type   | Description                    |
| -------- | ------ | ------------------------------|
| N/A      | N/A    | This method does not require arguments. |

**Return Type:**
An integer (`int`). It represents the Y-coordinate of the mouse pointer. If the pointer is outside the window, it returns `-1`.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    CImgDisplay disp(400, 400);

    while (!disp.is_closed()) {
        int y = disp.mouse_y(); // Gets the Y-coordinate of the mouse pointer.
        if (y != -1) {
            cout << "Mouse Y-coordinate is: " << y << endl;
        } else {
            cout << "Mouse pointer is outside the window." << endl;
        }
        disp.wait();
    }

    return 0;
}
```

### .button

**Description:**
The `button()` method returns the current state of the mouse buttons. It provides information about which mouse buttons are currently pressed. The return value uses a bitwise representation to indicate the state of the three standard mouse buttons.

- **Bit 0** (`0x1`): Represents the state of the left mouse button. If the bit is set, it means the left button is pressed.
- **Bit 1** (`0x2`): Represents the state of the right mouse button. If the bit is set, it means the right button is pressed.
- **Bit 2** (`0x4`): Represents the state of the middle mouse button. If the bit is set, it means the middle button is pressed.

Multiple bits can be set simultaneously, indicating that more than one button is pressed at once.

| Argument | Type   | Description                    |
| -------- | ------ | ------------------------------|
| N/A      | N/A    | This method does not require arguments. |

**Return Type:**
An unsigned integer (`unsigned int`). It represents the state of the mouse buttons using a bitwise approach.

**Example:**
```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    CImgDisplay disp(400, 400);

    while (!disp.is_closed()) {
        unsigned int mouse_state = disp.button(); // Gets the current mouse button state.

        if (mouse_state & 0x1) { // Left mouse button is pressed.
            cout << "Left mouse button clicked." << endl;
        }

        if (mouse_state & 0x2) { // Right mouse button is pressed.
            cout << "Right mouse button clicked." << endl;
        }

        if (mouse_state & 0x4) { // Middle mouse button is pressed.
            cout << "Middle mouse button clicked." << endl;
        }

        disp.wait(); // Wait before checking again.
    }

    return 0;
}
```

### .move

**Description:**
The `move()` method allows you to move the associated display window to a new location on the screen. You specify the new position with X and Y coordinates.

| Argument | Type   | Description                                    |
| -------- | ------ | ----------------------------------------------|
| pos_x    | `int`  | The X-coordinate of the new window location.  |
| pos_y    | `int`  | The Y-coordinate of the new window location.  |

**Return Type:**
A reference to the current `CImgDisplay` object (`CImgDisplay&`).

**Example:**
```cpp
#include <CImg.h>
using namespace cimg_library;

int main() {
    CImgDisplay display(640, 480);

    // Move the window to position (100, 150).
    display.move(100, 150);

    return 0;
}
```