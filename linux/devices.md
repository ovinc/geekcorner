# Devices and peripherals


## All devices

They are present in `/dev` and appear in yellow when doing `ls`.
To see all input/output devices (TTY), do e.g.
```bash
ls /dev/tty*
```

To have information about a specific device, including vendor and product IDs, etc. (which can be useful for udev rules, see below)
```bash
udevadm info -a -n ttyACM0
```

## USB devices

List all devices connected via USB
```bash
lsusb
```
which outputs a list of items like
`Bus 002 Device 004: ID 0bda:0328 Realtek Semiconductor Corp. USB3.0-CRW`
where
- `002` is the *bus* number (integer),
- `004` is the *device* (devnum) number (integer),
- `0bda` is the *vendor* ID (hexadecimal),
- `0328` is the *product* ID (hexadecimal).

To have more information, use the verbose option (useful to make udev rules, see below)
```bash
lsusb -v
```
which is typically more useful if filtered by bus/devnum (option `-s`) or by vendor/product (option `-d`), e.g.
```bash
lsusb -v -s 002:004
lsusb -v -s 2:4
lsusb -v -d 0bda:0328
lsusb -v -d bda:328
```
(all give the same output).


## udev rules

udev is the device manager of Linux. It can accept rules, which can be useful e.g. for giving always the same name to the COM port when a specific device is connected.

Rules can be written in the folder `/etc/udev/rules.d/`, either in separate files or in a single file (with `.rules` extension).
The file names follow a pattern like
`33-perso.rules`
where the initial number gives the order in which rules are processed (lower numbers are processed first).

In order to identify a device to apply a rule to it, one can use the device node name, e.g. `ttyACM0` as input of the `--name` option in `udevadm info`, using the `-a` option (`--attribute-walk`, which walks through the chain of parent devices), e.g.
```bash
udevadm info -a -n ttyACM0
```
which will output a list of devices and their attributes that can be used to identify them in udev rules.
One can only use attributes from one of the devices in the list, not mixing them.
Typically, the most useful information will be within one of the listed parent devices, e.g.
```
looking at device '/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/tty/ttyACM0':
    KERNEL=="ttyACM0"
    SUBSYSTEM=="tty"
    DRIVER==""

looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0':
    KERNELS=="1-8:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="cdc_acm"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{authorized}=="1"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bInterfaceClass}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceSubClass}=="02"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bmCapabilities}=="6"
    ATTRS{bInterfaceProtocol}=="01"

looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1/1-8':
    KERNELS=="1-8"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{quirks}=="0x0"
    ATTRS{bcdDevice}=="0001"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{serial}=="758333137333517002A2"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{authorized}=="1"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{version}==" 1.10"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{urbnum}=="34"
    ATTRS{manufacturer}=="Arduino (www.arduino.cc)"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{devpath}=="8"
    ATTRS{removable}=="removable"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{idVendor}=="2341"
    ATTRS{ltm_capable}=="no"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="5"
    ATTRS{maxchild}=="0"
    ATTRS{configuration}==""
    ATTRS{tx_lanes}=="1"
    ATTRS{idProduct}=="0043"
    ATTRS{rx_lanes}=="1"
```
(only the third parent contains the actual arduino information)

Then, to identify the arduino as e.g. `tty_arduino` instead of `ttyACM0`, write *in one line* in a udev rules file something like
```
KERNELS=="1-8", ATTRS{idVendor}=="2341", ATTRS{idProduct}=="0043"`
```
(all equalities must be verified for the device to be identified)
followed immediately on the same line (after a comma) with the info about the alias (it's better to add a symlink with += rather than assign one with =, incase one already exists)
```
SYMLINK+="tty_arduino"
```
i.e. the full line is
```
KERNELS=="1-8", ATTRS{idVendor}=="2341", ATTRS{idProduct}=="0043", SYMLINK+="tty_arduino"
```

In order to make the udev rules apply (with sudo rights):
```bash
udevadm control --reload
udevadm trigger
```

Troubleshooting can be done knowing the full device path, e.g.
```bash
udevadm test /dev/ttyACM0
```
which simulates how udev applies its rules.

- Video resource: https://www.youtube.com/watch?v=BOxWrMNXKpU

- Text resource (French): https://doc.ubuntu-fr.org/udev


## Python

One can have some information about devices connected to COM ports using the `serial` module:
```python
from serial.tools import list_ports
ports = list_ports.comports()
```
which gives a list of ports, which have various attributes including `.manufacturer` and `.name`, which seems to give the device node name (e.g. `ttyACMO`), and `.usb_interface_path` which can be useful for `udevadm test` (see above).


## Troubleshooting

If there are errors when trying to access the port (e.g. permission problems etc.), after defining udev rules, it might be that the symlink created with udev does not point to the correct device. This can be checked with
```bash
ls -l /dev
```
If the custom device points to e.g. `/usb/bus...` instead of `ttyACM0`, one solution is to add the *SUBSYSTEM* or *KERNEL* attribute specification in the udev rules if not present.

If the problem persists, it may be that the user does not have the correct permissions, see e.g.
https://askubuntu.com/questions/210177/serial-port-terminal-cannot-open-dev-ttys0-permission-denied
(user must be in the `dialout` permission group in order to use tty devices).
This can be checked with
```bash
groups username
```
(which must list `dialout` ; replace username by actual user name)

If dialout is not listed, it can be added with either
```bash
sudo gpasswd --add username dialout
```
or
```bash
sudo adduser username dialout
```
