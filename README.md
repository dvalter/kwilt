<img src="data/icons/sc-apps-kwilt.svg" alt="Kwilt logo" width="96" align="right">

# Kwilt - a drop-down terminal based on the shitty engine and Koncrepe technology.

Kwilt is a drop-down terminal emulator: a fork of KDE's Yakuake whose
terminals are provided by the  [Koncrepe](https://github.com/dvalter/koncrepe)
KPart, which runs on the [shitty](https://github.com/pg83/shitty) terminal engine.
Koncrepe has to be installed for Kwilt to work.


## License

The Kwilt sources keep Yakuake's licenses (GPL v2, GPL v3 or any later
version accepted by the membership of KDE e.V.; see `LICENSES/`). Kwilt runs
on the shitty engine, which is GPL-3.0-or-later, so Kwilt binaries are
distributed under the GNU General Public License version 3 only.


## Upstream

Kwilt is based on Yakuake, whose sources are at
https://invent.kde.org/utilities/yakuake and whose website is
https://apps.kde.org/yakuake. Please don't report Kwilt bugs to KDE.


## Basic build and installation instructions

1. Download the source code or clone this repository
2. `cd` to the source code folder
3. `mkdir build`
4. `cd build`
5. `cmake ../` - defaults to `/usr/local` as installation path on UNIX ([docs](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)), optionally use `-DCMAKE_INSTALL_PREFIX=<path to install to>`
6. `make`
7. `sudo make install`

To remove use `sudo make uninstall`

For more, please see the KDE Techbase wiki (https://techbase.kde.org/) and
the CMake documentation (at https://www.cmake.org/).
