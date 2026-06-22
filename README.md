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
