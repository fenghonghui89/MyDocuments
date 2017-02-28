
# < Setting up Appium >

## - Appium on real iOS devices -

### TESTING USING XCODE 8 (INCLUDING IOS 10) WITH XCUITEST
brew install libimobiledevice

### APPIUM ON REAL ANDROID DEVICES
Make sure that your device can connect to ADB and has Developer Mode enabled.
For testing Chrome on a real device, you’re responsible for ensuring that Chrome of an appropriate version is installed.
Also, you’ll want to make sure that “Verify Apps” in settings is disabled/unchecked.





## < Running Appium on Mac OS X >
### SYSTEM SETUP (IOS)
You need to authorize use of the iOS Simulator.
npm install -g authorize-ios
sudo authorize-ios

Make sure UI Automation is enabled on your device. Settings -> Developer -> Enable UI Automation


### TESTING USING XCODE 8 (INCLUDING IOS 10) WITH XCUITEST
In order to automate iOS devices with Xcode 8 (which includes all testing of iOS 10+), you need to install the Carthage dependency manager
brew install carthage
