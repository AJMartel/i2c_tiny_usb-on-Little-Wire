
Aside: Why isn't this project more active? Other than RC calibration stuff under investigation in 
[#1](https://github.com/nopdotcom/i2c_tiny_usb-on-Little-Wire/issue/1), 
this software is feature-complete and has no other documented bugs. If you find 
problems, try to make fixes into a pull request, but in any case **please** document 
your frustration and/or what happened—or you'll be maintaining your fork forever.

# i2c_tiny_usb on LittleWire

This is a cut&paste of 
[Till Harbaum's i2c_tiny_usb device for Linux](http://www.harbaum.org/till/i2c_tiny_usb/) 
into the [LittleWire](http://littlewire.cc) firmware tree, forked from
[littlewire/Little-Wire](https://github.com/littlewire/Little-Wire). 
This port is useful because there has been a Linux 
[i2c_tiny_usb kernel driver](http://lxr.free-electrons.com/source/drivers/i2c/busses/i2c-tiny-usb.c?v=3.3)
since ~2006.

i2c_tiny_usb requires a 12MHz crystal not present in LittleWire. The
LW hardware uses an internal 16.5MHz system clock calibrated from USB
timing instead. (I would not use the LittleWire hardware in places
where temperature/clock drift was a concern. If you see timing problems,
please add to your issue (and/or write PRs) to
[#1](https://github.com/nopdotcom/i2c_tiny_usb-on-Little-Wire/issue/1).)

Note that you will probably need to edit
[```usbconfig.h```](https://github.com/nopdotcom/i2c_tiny_usb-on-Little-Wire/blob/master/firmware/usbconfig.h#L157)
to set proper vendor/device IDs. (I've received no response from Till 
Harbaum as to whether a compatible project could use the i2c_tiny_usb IDs. Take that fact as you will.)

It's possible to build a kernel driver for LittleWire directly, but
the USB interrupt endpoint model complicates error handling.

See <https://github.com/nopdotcom/i2c_tiny_usb-on-Little-Wire/wiki/BuildingOnLinux> 
for an example of how to build this firmware.
