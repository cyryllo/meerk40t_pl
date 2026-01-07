To communicate with devices connected via USB and serial ports in Linux, you need to add the user to the `dialout` group in Linux
```bash
sudo usermod -a -G dialout $USER
```
Next, we need to create a udev rule for our laser. We will need the Vendor ID and Product ID. We can obtain this by entering the command
```bash
lsusb
```
Next, create the rule as superuser
```bash
sudo nano /etc/udev/rules.d/97-ctc-lasercutter.rules
```
Enter the following text into the file and replace [VENDOR ID] and [PRODUCT ID] with the information obtained from lsusb:
```bash
SUBSYSTEM==“usb”, ATTRS{idVendor}==“1a86”, ATTRS{idProduct}==‘5512’, ENV{DEVTYPE}==“usb_device”, MODE="0664", GROUP="dialout"
```
Save the file with Ctrl+o and exit with Ctrl+x

Then restart the system for the changes to take effect.