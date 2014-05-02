JGRUSBDeviceMonitoring
==========================

##JGRUSBDeviceMonitor
JGRUSBDeviceMonitor is a class that provides a block interface for when USB devices are connected and removed from your Mac.

### Usage

Create an instance of `JGRUSBDeviceMonitor` and setup the blocks by calling `monitorForUSBDevicesWithConnectedBlock:removedBlock`.


Set an `NSString` variable with the command that you would like to execute. Call `commandLineOutput` on that string to execute. The return value is a NSString with the terminal output.

```objc
JGRUSBDeviceMonitor *usbDeviceMonitor = [[JGRUSBDeviceMonitor alloc] init];
[usbDeviceMonitor monitorForUSBDevicesWithConnectedBlock:^(NSDictionary *device) {
	//USB device connected
	
} removedBlock:^(NSDictionary *device) {
	//USB device removed
	
}];
```

The returned dictionaries have two keys, `name` and `uuid`.


##JGRiOSDeviceMonitor
JGRiOSDeviceMonitor is a subclass of JGRUSBDeviceMonitor which filters all but iOS devices. Whilst we could filter by product id, this would cause this class to become outdated with every new iOS device that is released. Since my use case just needed to identify the device type and UUID we filter specifically with the following array:

`@[@"iPod", @"iPad", @"iPhone"];`

The class is otherwise identical to JGRUSBDeviceMonitor.
