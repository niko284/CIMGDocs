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

To install CImg on a Mac device which does not utilize Storm, you must:
- 

## Generate a new site

Generate a new Docusaurus site using the **classic template**.

The classic template will automatically be added to your project after you run the command:

```bash
npm init docusaurus@latest my-website classic
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Docusaurus.

## Start your site

Run the development server:

```bash
cd my-website
npm run start
```

The `cd` command changes the directory you're working with. In order to work with your newly created Docusaurus site, you'll need to navigate the terminal there.

The `npm run start` command builds your website locally and serves it through a development server, ready for you to view at http://localhost:3000/.

Open `docs/intro.md` (this page) and edit some lines: the site **reloads automatically** and displays your changes.
