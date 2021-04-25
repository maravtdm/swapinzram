# swapinzram for Slackware

The package swapinzram is intended to extend the swap spaces available beyond
swap partitions and swap files, providing swap space in the form of a block
device in compressed RAM, using the zram kernel module. As the files in it are
compressed this results in an increase of the RAM size usable by the system at
the cost of a small overhead to compress and decompress the files. 

This can be useful to:
1. Avoid or at least delay swapping on a mass storage device when available
space in RAM decreases. This results in a performance gain because writing in
RAM is way faster that on a hard disk or even an SSD.
2. Less writing on a storage devices like flash drives, eMMC, USB flash drives
or SD card, if the swap partition or file is installed on such devices.
Beyond the performance gain this also minimizes wearing of the device.

zram can also be used to create block devices in RAM for other usages, like
to store the files in /tmp or the kernel log, but this is not in the scope
of this package. However as we pick an available zram device id there should
be no conflict when adding these features. 

Also in the TODO list, allow to write idle/incompressible pages to a backing
storage rather than keeping them in memory. The documentation states that the
backing storage should be a swap partition, not a swap file, but I will check
if it's still true.

The script /etc/rc.d/swapinzram allows to create or remove a swapinzram device
and check its status.

The default settings can be changed: edit as root the file /etc/swapinzram.conf,
which also describes them. If swapinzram is active, after having modified the
settings you can just type: "swapinzram restart" to put them into effect.

Didier Spaier, 25 November 2020
Edited on 22 December 2020

HOWTO:
https://slackbuilds.org/howto/
