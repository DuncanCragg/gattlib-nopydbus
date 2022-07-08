
Now Python- and DBus-free!
=========================

This is GattLib without Python ("why am I seeing libpython in my ldd? why is it
complaining about a global lock?") and without DBus ("why? just why?").


Original README - edited appropriately...
=========================================

GattLib is a library used to access Generic Attribute Profile (GATT) protocol of BLE (Bluetooth Low Energy) devices.
It has been introduced to allow to build applications that could easily communicate with BLE devices.

It supports Bluez v5 only.

Latest GattLib Release packages
===============================

X86 [deb package here](/gattlib_0.3-dev_x86_64.deb)

ARM64 [deb package, untested but here](/gattlib_0.3-dev_arm64.deb)


Build GattLib
=============

* Gattlib requires the following packages: `libbluetooth-dev`, `libreadline-dev`.  
If you don't know how to install them, then I'd suggest you're a little out of your depth!

```
cd <gattlib-src-root>
mkdir build && cd build
cmake ..
make
```

* Gattlib can also be built for a specific version of Bluez by specifying its version at build time:

```
mkdir build && cd build
cmake -DBLUEZ_VERSION=5.50 ..
make
```


### Cross-Compilation

To cross-compile GattLib, you must provide the following environment variables:

- `CROSS_COMPILE`: prefix of your cross-compile toolchain
- `SYSROOT`: an existing system root that contains the libraries and include files required by your application

Example:

```
cd <gattlib-src-root>
mkdir build && cd build
export CROSS_COMPILE=~/Toolchains/gcc-linaro-4.9-2015.05-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-
export SYSROOT=~/Distributions/debian-wheezy
cmake ..
make
```

Package GattLib
===============

From the build directory: `cpack ..`

**Note:** It generates DEB, RPM and ZIP packages. Ensure you have the expected dependencies
 installed on your system (eg: to generate RPM package on Debian-based Linux distribution
  you must have `rpm` package installed).

Default install directory is defined as /usr by CPack variable `CPACK_PACKAGE_INSTALL_DIRECTORY`.  
To change the install directory to `/usr/local` run: `cpack -DCPACK_PACKAGE_INSTALL_DIRECTORY=/usr/local ..`


Examples
========

* [Demonstrate discovering of primary services and characteristics](/examples/discover/discover.c):

        ./examples/discover/discover 78:A5:04:22:45:4F

* [Demonstrate BLE scanning and connection](/examples/ble_scan/ble_scan.c):

        ./examples/ble_scan/ble_scan

* [Demonstrate GATT notification using GATT Battery service](/examples/notification/notification.c):

        ./examples/notification/notification

* [Demonstrate use with Nordic NUS](/examples/nordic_uart/nordic_uart.c):

        ./examples/nordic_uart/nordic_uart



Known limitations
-----------------

* **gattlib and BLE**: this repo will only support BLE, if Classic breaks, then no-one will notice. You need Bluez v5.


TODO List
=========

- ARM64 build and deb packages coming soon...

License
=======

Gattlib for recent version of Bluez (v5.40+) has a BSD-3-Clause license.

Support
=======

Lab A Part are, of course, beyond awesome for delivering us GattLib. Support them, not me.

Commercial Support can be obtained through [Lab A Part](https://labapart.com). Please contact us: [https://labapart.com/about/](https://labapart.com/about/).


