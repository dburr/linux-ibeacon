linux-ibeacon
=============

This is a Python script that creates an iBeacon-compatible Bluetooth LE
beacon using Linux and a Bluetooth LE adapter



What You Need
-------------

You need a 

`sudo apt-get install bluetooth bluez-utils blueman`


How to use it
-------------


    Usage: sudo ibeacon [-u|--uuid UUID or `random' (default=Beacon Toolkit app)]
                        [-M|--major major (0-65535, default=0)]
                        [-m|--minor minor (0-65535, default=0)]
                        [-p|--power power (0-65535, default=200)]
                        [-d|--device (default=hci0)]
                        [-z|--down]
                        [-v|--verbose]
                        [-n|--simulate (implies -v)]
                        [-h|--help]

[IBEACON]: https://developer.apple.com/ibeacon/ "iBeacon info page"
[USB-BT-LE]: http://www.amazon.com/dp/B009ZIILLI/?tag=otakunocast-20 "Plugable USB Bluetooth 4.0 Low Energy Micro Adapter"
[BLUEZ]: http://www.bluez.org "BlueZ - Linux Bluetooth stack"
[MITLICENSE]: http://opensource.org/licenses/MIT "MIT License"