# ZXCC Debian Packaging

Debian/Ubuntu packaging for ZXCC - CP/M 2/3 emulator for cross-compiling and running CP/M tools.

## Overview

ZXCC is John Elliott's CP/M 2/3 emulator that allows cross-compiling and running CP/M tools under Linux/Unix/macOS. This repository contains the Debian packaging files, with the upstream ZXCC source included as a git submodule.

### Included Utilities

- **zxcc** - CP/M program executor
- **zxc** - C compiler front-end for HI-TECH C
- **zxas** - Assembler front-end
- **zxlibr** - Library manager front-end
- **zxlink** - Linker front-end
- **zxobjtohex** - Object to HEX converter

## Clone Repository

```bash
# Clone with submodule
git clone --recursive https://github.com/onionmixer/zxcc-debian.git

# Or clone and init submodule separately
git clone https://github.com/onionmixer/zxcc-debian.git
cd zxcc-debian
git submodule update --init --recursive
```

## Build Dependencies

Install required packages on Ubuntu/Debian:

```bash
sudo apt install build-essential devscripts debhelper \
    automake libtool libncurses-dev libreadline-dev lynx
```

## Build Package

```bash
cd zxcc-debian/ZXCC

# Build .deb package (unsigned)
dpkg-buildpackage -us -uc -b

# Generated files will be in parent directory
ls ../*.deb
```

## Install Package

```bash
sudo dpkg -i ../zxcc_0.5.7-1_amd64.deb
```

## Usage

After installation, you need CP/M binaries (.COM files) to run. For example, to use with HI-TECH Z80 C compiler:

```bash
# Set CP/M binary directory (optional, if not using default paths)
export BINDIR80=/path/to/hitech-c/bin

# Run a CP/M program
zxcc program.com [arguments]
```

### Default CP/M Directory Structure

The package creates the following directories:

- `/usr/lib/x86_64-linux-gnu/cpm/bin80/` - CP/M executables (.COM)
- `/usr/lib/x86_64-linux-gnu/cpm/lib80/` - CP/M libraries
- `/usr/lib/x86_64-linux-gnu/cpm/include80/` - CP/M header files

## Upstream

- **ZXCC**: https://github.com/agn453/ZXCC
- **Original Author**: John Elliott
- **Maintainer**: Tony Nicholson

## License

- ZXCC: GPL-2.0+
- cpmio/cpmredir libraries: LGPL-2.1+
