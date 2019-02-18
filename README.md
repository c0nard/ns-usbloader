# NS-USBloader

NS-USBloader is a PC-side TinFoil/GoldLeaf NSP USB uploader. Replacement for default usb_install_pc.py and GoldTree.

With GUI and cookies.

Read more: https://developersu.blogspot.com/2019/02/ns-usbloader-en.html

Here is the version of 'not perfect but anyway' [tinfoil I use](https://cloud.mail.ru/public/DwbX/H8d2p3aYR). 
Ok, I'm almost sure that this version has bugs. I don't remember where I downloaded it. But it works for me somehow.. 
Let's rephrase, if you have working version of TinFoil DO NOT use this one.  

## License

Source code spreads under the GNU General Public License v.3. You can find it in LICENSE file.

## Requirements

JRE 8 or higher. See below.

## Used libraries
* [OpenJFX](https://wiki.openjdk.java.net/display/OpenJFX/Main)
* [usb4java](https://mvnrepository.com/artifact/org.usb4java/usb4java)
* Few icons taken from: [materialdesignicons](http://materialdesignicons.com/)

## Usage
### Linux:

Install JRE/JDK 8 or higher (openJDK is good. Oracle's one is also good). JavaFX not needed, if you're interested (it's embedded).

`root # java -jar /path/to/NS-USBloader.jar`

### macOS

See 'Linux' section.

Set 'Security & Privacy' settings if needed.

### Windows: 

* Download Zadig: https://zadig.akeo.ie/
* Open tinfoil. Set 'Title Managment' -> 'Usb install NSP'
* Connect NS to pc
* Open Zadig, select NS in dropdown, select 'libusbK (v3.0.7.0)' (version may vary), click 'Install WCID Driver'
* Check that in device list of you system you have 'libusbK USB Devices' folder and your NS inside of it
* Download and install Java JRE (8+)
* Get this application (JAR file) double-click on on it (alternatively open 'cmd', go to place where jar located and execute via 'java -jar thisAppName.jar')
* Remember to have fun!

## Tips&tricks
### Add user to udev rules to use NS non-root (Linux):
`root # vim /etc/udev/rules.d/99-NS.rules`

`SUBSYSTEM=="usb", ATTRS{idVendor}=="057e", ATTRS{idProduct}=="3000", GROUP="plugdev"`

`root # udevadm control --reload-rules && udevadm trigger`

## Known bugs
* Unable to interrupt transmission when libusb awaiting for read event (when user sent NSP list but didn't selected anything on NS).

## NOTES
Table 'Status' = 'Uploaded' does not means that file installed. It means that it has been sent to NS without any issues! That's what this app about. 
Handling successful/failed installation is a purpose of the other side application (TinFoil/GoldLeaf). (And they don't provide any feedback interfaces so I can't detect success/failure.)

## TODO:
- [x] macOS QA v0.1
- [ ] macOS QA v0.2 (partly)
- [x] Windows support
- [ ] code refactoring (almost. todo: printLog() )
- [x] GoldLeaf support
- [ ] XCI support
- [ ] File order sort (non-critical)

## Thanks
Appreciate assistance and support of both Vitaliy and Konstantin. Without you all this magic would not have happened.

[Konstanin Kelemen](https://github.com/konstantin-kelemen)
 
[Vitaliy Natarov](https://github.com/SebastianUA) 