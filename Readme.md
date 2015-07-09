#i2c_tiny_usb on LittleWire

This is a cut&paste of [Till Harbaum's i2c_tiny_usb device for Linux]
(http://www.harbaum.org/till/i2c_tiny_usb/) into the [LittleWire]
(http://littlewire.cc) firmware tree, forked from
github.com/littlewire/Little-Wire . This port is useful because there
has been a Linux [i2c_tiny_usb kernel
driver](http://lxr.free-electrons.com/source/drivers/i2c/busses/i2c-tiny-usb.c?v=3.3)
since ~2006.

i2c_tiny_usb requires a 12MHz crystal not present in LittleWire. The
LW hardware uses an internal 16.5MHz system clock calibrated from USB
timing instead. (I would not use the LittleWire hardware in places
where temperature/clock drift was a concern.)

Note that you will need to edit usbconfig.h to set proper vendor/device IDs.

It's possible to build a kernel driver for LittleWire directly, but
the USB interrupt endpoint model complicates error handling.

See <https://github.com/nopdotcom/i2c_tiny_usb-on-Little-Wire/wiki/BuildingOnLinux> for an example of how to build.
