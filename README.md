# ARIA (Modernized Fork)
**Adept MobileRobots Advanced Robotics Interface for Applications**

[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
[![C++](https://img.shields.io/badge/C++-Modernized-00599C.svg)]()

> **⚠️ FORK NOTICE: MODERNIZED FOR NEW COMPILERS**
> This repository is a modernized fork of the original ARIA v2.9.1 library by Adept MobileRobots. The original codebase contains legacy C/C++ patterns that fail to compile on modern Linux systems and newer versions of GCC/G++. 
> 
> This fork updates the source code to be compatible with modern development environments, specifically targeting the operation of the **Pioneer-3AT** robot and its integration with MATLAB (`aria-matlab`). All original copyrights and the GPLv2 license remain intact.

## 🛠️ Compatibility Matrix
| Component | Tested Version |
| :--- | :--- |
| **OS** | Ubuntu 22.04 LTS (or newer) |
| **Compiler** | GCC / G++ 11.4.0+ |
| **Build System** | GNU Make |
| **Hardware** | Pioneer-3AT |

## 🚀 Migration Guide & Changelog
The following critical updates were made to revive this library for modern systems:
* **`glibc` Compatibility:** Removed obsolete global arrays `sys_nerr` and `sys_errlist` in `src/ArLog.cpp`. Replaced with the thread-safe POSIX standard `strerror()` function.
* **Modern C++ Type Safety:** Fixed invalid pointer-to-integer comparisons (`> 0`) in `src/ArJoyHandler_LIN.cpp`. Updated `FILE*` validations to correctly check against `NULL`.

## ⚙️ Quickstart: Building on Modern Linux
Do not use the legacy instructions if you are on a modern Linux distribution. Use the following steps to build the library:

```bash
# 1. Clone this modernized fork
git clone https://github.com/filpsl/Aria.git
cd Aria

# 2. Clean any existing artifacts
make clean

# 3. Build the library
make

# 4. Install (Requires sudo)
sudo make install
```

---

# 📖 Original ARIA Documentation (v2.9.1)

**Copyrights:**
* Copyright 2002-2005 ActivMedia Robotics, LLC. All rights reserved.
* Copyright 2006-2009 MobileRobots Inc. All rights reserved.
* Copyright 2010-2015 Adept Technology. All rights reserved.
* Copyright 2016 Omron Adept Technologies, Inc. All rights reserved.

See `LICENSE.txt` for full license information about ARIA.

## Introduction
Welcome to the Adept MobileRobots Advanced Robotics Interface for Applications (ARIA). ARIA is an object-oriented, application programming interface (API) for the Adept MobileRobots (and ActivMedia) line of intelligent mobile robots, including Pioneer 2/3 DX and AT, PeopleBot, PowerBot, AmigoBot, PatrolBot/Guiabot, Seekur, SeekurJr and Pioneer LX mobile robots.

Written in the C++ language, ARIA provides access to and management of the robot controller, as well to many accessory robot sensors and effectors, as well as useful utilities and infrastructure for cross-platform robot application development.

ARIA is provided as open source software under the GNU General Public License. This allows you to view, modify and rebuild the ARIA library as desired, provided that software developed with ARIA comply with the requirements of the license. 

## Documentation and Help
Follow the `INSTALL.txt` instructions to install ARIA on your Linux or Windows workstation or robot computer.

ARIA includes a full API Reference Manual in HTML format. This manual, `Aria-Reference.html` (and in the `docs/` directory), includes documentation about each of the classes and methods in ARIA, as well as a comprehensive overview. 

If you have any problems or questions using ARIA or your robot, the MobileRobots support site provides:
* A FAQ (Frequently Asked Questions) list at http://robots.mobilerobots.com/FAQ.html
* A knowledge base at http://robots.mobilerobots.com
* The Aria-Users mailing list.

## Licenses and Sharing
ARIA is released under the **GNU Public License (GPL) v.2**, which means that if you distribute any work which uses ARIA, you must distribute the entire source code to that work under the GPL as well. Read the included `LICENSE.txt` for details. 

ARIA may instead be relicensed for proprietary, closed source applications. Contact `sales@mobilerobots.com` for details.

## The ARIA Package Structure
* `docs/` - The API Reference Manual.
* `examples/` - ARIA examples (start here, see `examples/README.txt`).
* `include/` - ARIA header (`*.h`) files.
* `src/` - ARIA source code (`*.cpp`) files.
* `lib/` or `lib64/` - Compiled libraries.
* `params/` - Robot parameter files (e.g., `p3dx.p`).
* `python/` & `java/` - Wrapper libraries.
* `matlab/` - Scripts for compiling the Matlab interface.

## Legacy Build Instructions (Original Reference)
> **Note:** For modern Linux systems, please refer to the Quickstart section at the top of this document.

### Setting variables for ARIA Makefiles (Linux)
You can add compile options to the following variables used in the ARIA Makefiles:

```bash
make CXX="g++-4.6"
```

* `CXXFLAGS`: Additional compile flags passed to the C++ compiler.
  * Example for optimization: `make clean; make CXXFLAGS="-mtune=atom -O2"`
* `CXX`: Specify the C++ compiler command to use (Default is `g++` or `c++`).

### Using ARIA from Matlab or Simulink
As of ARIA 2.8, it is possible to use a small but essential subset of ARIA features from Matlab and Simulink via MEX functions and a pure-C wrapper library called `ariac`. See `matlab/README.md` for details.

### MobileSim Simulator
SRIsim is no longer included with ARIA. There is now a separately downloadable MobileSim simulator at http://robots.mobilerobots.com.
