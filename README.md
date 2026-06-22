# BCM43142-Ubuntu
Driver wifi network and bluetooth Broadcom BCM43142 for Ubuntu
The Broadcom BCM43142 chip combines both Wi-Fi and Bluetooth on a single PCIe card. In Ubuntu, the Wi-Fi usually requires the bcmwl-kernel-source package, while the Bluetooth side requires specific firmware to be pushed during initialization.
# Step 1: Connect to the Internet
Because you have no Wi-Fi, you will first need an internet connection to download the packages, you will need a temporary working internet connection. Connect via an Ethernet cable or use USB Tethering from your smartphone.
# Step 2: Purge Old and Conflicting Drivers
Sometimes, Ubuntu tries to load conflicting packages or older configurations that break modern kernels. Clean them out by opening your Terminal (Ctrl + Alt + T) and running:
sudo apt update
sudo apt-get purge bcmwl-kernel-source
# Step 3: Install the Broadcom STA Driver
Install the dynamic kernel module support (dkms) version of the driver. This ensures the driver automatically rebuilds itself whenever Ubuntu updates your Linux system kernel.
sudo apt install broadcom-sta-common broadcom-sta-dkms
# Step 4: Unblock and Load the Driver
If the installation finishes successfully but your Wi-Fi icon still does not appear, you need to manually tell Linux to unload the bad open-source modules and load the new proprietary one:
sudo modprobe -rv bcma
sudo modprobe -v wl
# Step 5: Reboot
reboot for wifi

# Step 6: Install firmware bluetooth B43
Open your Terminal (Ctrl + Alt + T) and run the following commands to get the required firmware downloader and compilation tools:
sudo apt update
sudo apt install git build-essential bluez firmware-b43-installer


# Step 7: Install driver bluetooth
Download all BCM41342A0-trusty-binary files, then right click file install-bcm43142a0 choice "Run as the Program" to install bluetooth.

# Step 8: Restart the Bluetooth Module
Once the file is in place, you need to tell Ubuntu to reload the Bluetooth driver
sudo modprobe -r btusb
sudo modprobe btusb

# Step 9: Reboot
reboot for bluetooth

(Lenovo G40, Ubuntu 26.04 LTS, 22 June, 2026)
