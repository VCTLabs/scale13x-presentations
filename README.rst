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

Notes on .svg slides
====================

* view in a modern browser with javascript enabled
  * for navigation, use left/right arrows to do the fade-in effects, or up/down arrows to skip them#
* edit using Inkscape with JessyInk extension installed
  * JessyInk extension homepage http://code.google.com/p/jessyink/
  * probably already installed with recent Inkscape versions (look for /usr/share/inkscape/extensions/jessyInk.js)
