linux-ibeacon
=============

This is a Python script that creates an Apple® [iBeacon®][IBEACON]-compatible
[Bluetooth LE beacon][BTBEACONS] using a computer running Linux and a Bluetooth LE adapter.

What You Need
-------------

You need a computer capable of running Linux.  It can be a desktop or notebook PC, or any
of the various single-board computers that are popular nowadays such as the [Raspberry Pi][PI]
or [Arduino YUN][YUN].  It must have Python 2.6 or 2.7 installed.  This script does not need
any special Python libraries or modules, just the ones that come standard with Python.

Your version of Linux must be compatible with the new [Bluetooth 4.0 Low Energy (LE)][BLE] standard.
Currently this requires version 3.5 or greater of the Linux kernel.  You will
also need version 5.0 or greater of [BlueZ][BLUEZ], the Linux Bluetooth stack and associated
tools.

On most Linux distributions, BlueZ can be easily installed from your distribution's package
manager.  E.g., for Debian and Debian derivatives (Ubuntu, etc.):

`sudo apt-get install bluetooth bluez-utils blueman`

Your computer must also have a Bluetooth adapter (either built-in or USB) that is compatible with
the [Bluetooth 4.0 LE][BLE] standard.  To test whether your adapter is LE-compatible, issue the
following command:

`sudo hcitool lescan`

If you see either nothing, or a list of MAC addresses (`aa:bb:cc:dd:ee:ff`) then your adapter
supports Bluetooth LE.  If, on the other hand, you see any error messages in the output, then
your adapter does not support LE.  (This command will continuously scan for devices, so to exit
it press `Control-C.)

If you don't have a LE-capable adapter, the [Plugable USB Bluetooth 4.0 Low Energy Micro Adapter][USB-BT-LE]
is an inexpensive, low-profile USB Bluetooth adapter that is known to work well with Linux.

How to use it
-------------

    Usage: sudo ibeacon [-u|--uuid=UUID or `random' (default=Beacon Toolkit app)]
                        [-M|--major=major (0-65535, default=0)]
                        [-m|--minor=minor (0-65535, default=0)]
                        [-p|--power=power (0-255, default=200)]
                        [-d|--device=BLE device to use (default=hci0)]
                        [-z|--down]
                        [-v|--verbose]
                        [-n|--simulate (implies -v)]
                        [-h|--help]

This script must be run with `root` privileges in order to configure Bluetooth adapters.  It is most convenient to run it using `sudo.`

By default, the script creates an iBeacon whose UUID matches that which is used by the [Beacon Toolkit iOS app][BEACON-APP-IOS],
with major and minor both set to `0`.  These can be changed using the `-u`, `-M` and `-m` flags respectively.  When specifying
the UUID, you can specify an explicit UUID, or by specifying `random` the script will randomly generate a UUID.

UUID, major and minor may also be specified by setting the `IBEACON_UUID,` `IBEACON_MAJOR` and `IBEACON_MINOR` environment
variables, respectively.  If a value(s) is specified both in the environment as well as a command line option, the command
line option takes precedence.

To test, you will need a [device compatible with Bluetooth LE][BLE-DEVICES].  In the Apple universe, that means the iPhone 4S
or later, iPad 3rd gen or later (including Mini and Air), and the iPod touch.  For Android, you'll have to
[check the list][BLE-DEVICES] (most phones made within the last 2 years or so should be BLE-compatible.)  Then download
either [Beacon Toolkit][BEACON-APP-IOS] (for iOS) or [iBeacon Scanner][BEACON-APP-ANDROID] (for Android.)  Fire up the app
and begin scanning.  Your newly-created iBeacon should appear in the list.  If not, check to make sure that you
specified the correct UUID, major and minor numbers.  (For iOS devices, if you used a non-default UUID, you will have to
enter it in the Beacon Toolkit app's settings screen.)

License
-------

This script is licensed under the [MIT license][MITLICENSE].

[IBEACON]: https://developer.apple.com/ibeacon/ "iBeacon info page"
[BTBEACONS]: http://www.infoworld.com/article/2608498/mobile-apps/what-you-need-to-know-about-using-bluetooth-beacons.html "Bluetooth Beacons"
[PI]: http://www.amazon.com/dp/B00LPESRUK/?tag=otakunocast-20 "Raspberry Pi"
[YUN]: http://www.amazon.com/dp/B00F6YJK3S/?tag=otakunocast-20 "Arduino YUN"
[BLE]: http://en.wikipedia.org/wiki/Bluetooth_low_energy "Bluetooth LE"
[USB-BT-LE]: http://www.amazon.com/dp/B009ZIILLI/?tag=otakunocast-20 "Plugable USB Bluetooth 4.0 Low Energy Micro Adapter"
[BLUEZ]: http://www.bluez.org "BlueZ - Linux Bluetooth stack"
[MITLICENSE]: http://opensource.org/licenses/MIT "MIT License"
[BLE-DEVICES]: http://www.bluetooth.com/Pages/Bluetooth-Smart-Devices-List.aspx "Bluetooth LE compatible devices"
[BEACON-APP-IOS]: https://itunes.apple.com/us/app/beacon-toolkit/id728479775?mt=8 "Beacon Toolkit iOS App"
[BEACON-APP-ANDROID]: https://play.google.com/store/apps/details?id=de.flurp.beaconscanner.app "iBeacon Scanner Android App"
