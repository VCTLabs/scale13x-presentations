USB on embedded systems: quirky but versatile
=============================================

Abstract
--------

Boot a beaglebone running XFCE with USB mouse and keyboard connected, and both
input devices will likely behave as expected. Venture away from this limited
use case (ubiquitous embedded board serving as mini-desktop-replacement), and
things start to get more interesting. In some corners of the embedded USB
world, There Be Dragons -- we'll discuss both common limitations of embedded
USB host controllers and examples of weird quirks encountered in the wild.
Moving on to the unique features of embedded USB, we'll cover playing the USB
device role with "gadget" drivers, and the further twist of OTG (On-the-Go)
support that enables host/device role swapping.

Slides
------

.svg format, produced in Inkscape with JessyInk extension (http://wiki.inkscape.org/wiki/index.php/Tools#JessyInk)

bin/usb_quirky_versatile_paths.svg - fonts converted to paths, for viewing not editing
usb/usb_quirky_versatile.svg - non-embedded fonts, for editing (need proper fonts installed)

A Tale of Two Build Systems: Buildroot and OpenEmbedded
=======================================================

Abstract
--------

The embedded Linux ecosystem offers a heathy diversity of build systems
tailored to different niches, unlike proprietary OSes that tend to present a
build system controlled by the owner as the One True build system. This
presentation will focus on two of the embedded Linux build systems that have
exhibited the most staying power, Buildroot and OpenEmbedded, being sure to
answer some burning questions about them along the way:

* Which build system is the more natural choice for MMU-less micros?
* Which build system is the foundation for many consumer-electronics distributions?
* Which build system has its own theme song??

Slides
------

.svg format, produced in Inkscape with JessyInk extension (http://wiki.inkscape.org/wiki/index.php/Tools#JessyInk)

bin/buildroot_oe_paths.svg - fonts converted to paths, for viewing not editing
buildroot_oe/buildroot_oe.svg - non-embedded fonts, for editing (need proper fonts installed)

Embedded Linux Development with Yocto/OpenEmbedded: Easily Build A Custom Linux OS for Your Favorite Device
===========================================================================================================

Updated SCaLE 13x 2015 Requirements:

Time-frame
----------

One hour for short-short version.  Approx. 20 minutes overview with slides (section 1 and 2 below) and 30 minutes demo (see section 4).  Handout covers sections 3 and 4 (with maybe a little merging/overlap between 2 and 3).

Facility / Setup
----------------

Use upstream poky (maybe open-embedded too, check sync status of upstream repos) and meta-raspberrypi.  Pre-clone and build one each:

1) qemux86 (poky only)
2) beaglebone (poky only)
3) rpi (with upstream BSP)

Build basic console and sato/QT5 demo images (check status of sato vs. weston as default demo image), and at least console variants with debug/other tools using image features.  Do select cleans/rebuilds and kernel rebuilds/deploys (using qemu, but talk about rebuilding images/kernels for other machines).

Recommend laptops (beaglebones/rpis optional) but not required.


Description
-----------

This is inteneded as a "bootcamp" course for embedded developers who have not used OpenEmbedded, as well as current Linux developers and users familiar with at least one common embedded Linux platform (eg, RaspberryPi, BeagleBone, Wandboard, etc).  The course will provide an in-depth overview of the Yocto Project, the core OpenEmbedded layers and what they are, supported hardware, available documentation and other resources, build requirements, and how to setup, customize, build, and deploy your own embedded Linux OS image, root filesystem, kernel and bootloader, etc.  Handout will include installing build host dependencies and Yocto, building and deploying target images/SDKs, and basic troubleshooting/debugging/WhatIfScenarios.   A laptop is recommended for either local builds (quad-core or better recommended) or local web interface (eg, Toaster).

Course Slides / Handout Outline
-------------------------------

+ Introduction

 * Introduction to Yocto / Poky / OpenEmbedded / OE-core
 * Documentation and Help
 * Build Host / Distro Requirements
 * Obtaining the Source and Preparing the Build Environment

+ Overview

 * Build Overview, Core Images
 * Building an Image, Config Options
 * Deploying and Using the Result
 * Potential Failures

+ Requirements

 * Build Host requirements / Potential Issues

  - Gentoo amd64, VMs, and chroots
  - Build errors "command not found..."

 * Inside the Yocto/OE Development Environment

  - User Configuration, Metadata, Machine Configuration

   + Distro Layer, BSP Layer, Software Layers
   + Kernel Recipes and Versions
   + Image / Package Configuration

  - Recipes and Sources

   + File Types (Recipes, BBClass, Includes)
   + Upstream Releases/Repos, Local Projects
   + Source Mirror(s)

  - Package Feeds

   + Ipk Feed Support

  - BitBake Tips and Tricks

   + Recipes and Tasks
   + Source Fetching, Patching, Configuration, and Compilation
   + Package Splitting, Image Generation, SDK Generation
   + Custom Recipes and Layers

  - SDKs, external tools (Eclipse TCF Agent, remote gdb)

+ Let's Build Stuff

 * Hands-On Poky

  - qemux86
  - beaglebone

 * Add Upstream BSP

  - RaspberryPi layer
  - BeagleBone / TI layers

 * Customizing Your Build

  - Kernel Version and Configuration
  - New Kernel Recipe
  - Modifying and Adding Packages

 * Deployment and Debugging

  - Deploy Tips and Hacks
  - SDK Tools
  - GDB Server and Image Build Options
  - Eclipse and TCF Agent

 * Graphical User Interfaces

  - Toaster
  - Hob

Slides
------

Slides and slides with notes (in PDF) are in the bin directory, as well as printable slides/notes in PDF handout formt (portrait).  Original .odp files are in their respective topic directories.


ARM Linux Kernels and Graphics Drivers on Popular "Open" Hardware: Bleeding Edge vs. Vendor Blobs and Kernel Forks - How much is in Mainline, and How Open is Open?
===================================================================================================================================================================

Abstract
--------

This talk/workshop will attempt to cover the current state of open source support on several popular ARM boards and their variants.  Primary components include accelerated support for graphics hardware, mainline kernel support (largely device tree files and their "completeness"), and upstream (DENX) u-boot support.  The current state of mainline kernel/u-boot support and associated patches, along with the current build/deploy process, will be covered in detail for several popular open source boards/variants, including:

* ARMv7 HardFloat VFP/NEON

  - wandboard / udoo / cubox-i - iMX.6 quad core, Vivante GPU
  - beaglebone black / white - AM335X single core, OMAP3 / SGX GPU, PRUs
  - Sunxi mk802-II 1GB TV stick - Allwinner A10 single core, Mali GPU
  - Samsung Chromebook - Exynos5 dual core, Mali GPU
  - Genesi SmartBook - Freescale iMX.5 single core,  AMD z430 GPU

* ARMv7 HardFloat VFP (no NEON)

  - Trimslice Diskless - NVIDIA Tegra 2 dual core CPU/GPU

* ARMv6 HardFloat VFP (no NEON)

  - Raspberry Pi - Broadcom SoC single core, VideoCore IV GPU

The same general build/deploy process is followed on several different machines, with minor differences in u-boot and/or SDCard partitions, while required kernel patches are unique to each machine.  Several distribution options are available for the rootfs deployment, including Gentoo, Debian, Ubuntu, Yocto/Openembedded, and more.  Custom builds and bootstrapping are also dicussed/demonstrated.

Current kernels:

* chromeos-K1-signed-3.10.18.tar.gz
* tegra124-jetson-tk1-3.19.0-rc6
* beagleboneblack-3.18.1-bone1.tar.gz
* cubox-i-3.14.14.tar.bz2
* efikamx-2.6.31.14.27.tar.bz2
* mk802-1G-3.4.75.sun4i+.tar.bz2
* chromeos-samsung-signed-3.8.11.tar.bz2
* udoo-3.18.0.tar.bz2
* wandboard-3.18.0.tar.bz2


Slides
------

Slides (in PDF) are in the bin directory.  Original .odp files are in their respective topic directories.


Notes on .svg slides
====================

* view in a modern browser with javascript enabled
  * for navigation, use left/right arrows to do the fade-in effects, or up/down arrows to skip them#
* edit using Inkscape with JessyInk extension installed
  * JessyInk extension homepage http://code.google.com/p/jessyink/
  * probably already installed with recent Inkscape versions (look for /usr/share/inkscape/extensions/jessyInk.js)

bin directory
=============

Contains PDF and SVG slides, plus printable handouts for Yocto crash course.
