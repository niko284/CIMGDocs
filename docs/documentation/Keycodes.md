---
sidebar_position: 3
---

# Keycodes

**Description:**
Keycodes are unique identifiers for keys on a keyboard or input device. They are used to determine which key is pressed or released within the `CImg` environment. These keycodes are defined as constants in the `cimg` namespace, accessed using the scoping operator `::`. This makes code more portable across different systems.

## List of Keycodes

Here is a list of keycodes with their names as used in code:

| Key        | Keycode Name         |
|------------|---------------------|
| ESC        | `cimg::keyESC`       |
| F1         | `cimg::keyF1`        |
| F2         | `cimg::keyF2`        |
| F3         | `cimg::keyF3`        |
| F4         | `cimg::keyF4`        |
| F5         | `cimg::keyF5`        |
| F6         | `cimg::keyF6`        |
| F7         | `cimg::keyF7`        |
| F8         | `cimg::keyF8`        |
| F9         | `cimg::keyF9`        |
| F10        | `cimg::keyF10`       |
| F11        | `cimg::keyF11`       |
| F12        | `cimg::keyF12`       |
| PAUSE      | `cimg::keyPAUSE`     |
| 1          | `cimg::key1`         |
| 2          | `cimg::key2`         |
| 3          | `cimg::key3`         |
| 4          | `cimg::key4`         |
| 5          | `cimg::key5`         |
| 6          | `cimg::key6`         |
| 7          | `cimg::key7`         |
| 8          | `cimg::key8`         |
| 9          | `cimg::key9`         |
| 0          | `cimg::key0`         |
| BACKSPACE  | `cimg::keyBACKSPACE` |
| INSERT     | `cimg::keyINSERT`    |
| HOME       | `cimg::keyHOME`      |
| PAGEUP     | `cimg::keyPAGEUP`    |
| TAB        | `cimg::keyTAB`       |
| Q          | `cimg::keyQ`         |
| W          | `cimg::keyW`         |
| E          | `cimg::keyE`         |
| R          | `cimg::keyR`         |
| T          | `cimg::keyT`         |
| Y          | `cimg::keyY`         |
| U          | `cimg::keyU`         |
| I          | `cimg::keyI`         |
| O          | `cimg::keyO`         |
| P          | `cimg::keyP`         |
| DELETE     | `cimg::keyDELETE`    |
| END        | `cimg::keyEND`       |
| PAGEDOWN   | `cimg::keyPAGEDOWN`  |
| CAPSLOCK   | `cimg::keyCAPSLOCK`  |
| A          | `cimg::keyA`         |
| S          | `cimg::keyS`         |
| D          | `cimg::keyD`         |
| F          | `cimg::keyF`         |
| G          | `cimg::keyG`         |
| H          | `cimg::keyH`         |
| J          | `cimg::keyJ`         |
| K          | `cimg::keyK`         |
| L          | `cimg::keyL`         |
| ENTER      | `cimg::keyENTER`     |
| SHIFTLEFT  | `cimg::keySHIFTLEFT` |
| Z          | `cimg::keyZ`         |
| X          | `cimg::keyX`         |
| C          | `cimg::keyC`         |
| V          | `cimg::keyV`         |
| B          | `cimg::keyB`         |
| N          | `cimg::keyN`         |
| M          | `cimg::keyM`         |
| SHIFTRIGHT | `cimg::keySHIFTRIGHT`|
| ARROWUP    | `cimg::keyARROWUP`   |

## Example Usage

Here's an example of how you can use these keycodes in code:

```cpp
#include <iostream>
#include <CImg.h>
using namespace cimg_library;
using namespace std;

int main() {
    CImgDisplay disp(400, 400);
    while (!disp.is_closed()) {
        if (disp.is_key(cimg::keyESC)) {
            cout << "ESC key is being pressed." << endl;
        }
        disp.wait();
    }
    return 0;
}
