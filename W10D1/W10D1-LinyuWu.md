# VirtIO

VirtIO is a standardized interface which allows virtual machines access to simplified "virtual" devices, such as block devices, network adapters and consoles. Accessing devices through VirtIO on a guest VM improves performance over more traditional "emulated" devices, as VirtIO devices require only the bare minimum setup and configuration needed to send and receive data, while the host machine handles the majority of the setup and maintenance of the actual physical hardware.

## Tech Details
VirtIO devices appear, to the guest VM, to be normal PCI devices with a specific VendorID and DeviceID. All VirtIO devices have a Vendor ID of 0x1AF4, and have a DeviceID between 0x1000 and 0x103F. The type of VirtIO device (Network Adapter, Block Device, etc.) can be determined by the Subsystem ID field in the PCI Configuration Space for the device.

## IO Registers
Based on the PCI subsystem ID, the I/O mapped registers for the device can be determined. All devices have a common "header" block of registers:

```
Offset (Hex)	Name
00	Device Features
04	Guest Features
08	Queue Address
0C	Queue Size
0E	Queue Select
10	Queue Notify
12	Device Status
13	ISR Status
```

The Device Features register is pre-configured by the device, and includes flags to notify the guest VM what features are supported by the device. The Guest Features register is used by the guest VM to communicate the features that the guest VM driver supports. This allows both the host and the guest to maintain both backward and forward compatibility.
The Device Status field is used by the guest VM to communicate the current state of the guest VM driver. The flags in this register designate when the driver has found the device, when the driver has determined that the device is supported, and when the all of the necessary registers have been configured by the guest driver, and communication between the guest and host may begin.

```
Flags	Description
01	Device Acknowledged
02	Driver Loaded
04	Driver Ready
40	Device Error
80	Driver Failed
```