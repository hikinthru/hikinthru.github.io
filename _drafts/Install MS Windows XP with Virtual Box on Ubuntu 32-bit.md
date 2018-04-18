
## Install XP on VirtualBox

1. Download and install Oracle VM [VirtualBox Manager](https://www.virtualbox.org/wiki/Downloads) at this link, these instructions are for VirtualBox 5.1, 32-bit, on Ubuntu, and click on the *Linux Distributions*, choose your distribution and architecture (i386 for 32-bit or AMD64 for 64-bit). Follow the instructions to install VirtualBox.
1. Insert your XP CD. In this case I am using the manufacturer's CD which is only Service Pack 1.
1. Open VirtualBox and in the top right click **New**.
1. In **Name and operating system** enter your information. Any name is fine. **Select **Windows XP (32-bit)** for the **Version**.
1. Change the **Memory size** to 512 MB if you have 3 GB of RAM, or more depending on your resources. You can can adjust this later.
1. **Create a virtual hard disk now** should be selected. Click **Create**. 
1. Adjust the file size to no larger than your greatest need. I am just going to be running WoW and iTunes, so I am selecting 20 GB. For simple needs like mine in this case, **VDI** is fine.
1. You'll come back to the VirtualBox Manager. With your virtual machine highlighted, click **Start**.
1. The next window is **Select start-up disk**. It will default to your CDROM drive. If you wish to use an ISO in a different location click the folder icon to the right of the entry field and navigate to your installation image.
1. Windows Setup begins. If not, go back through the steps.
1. At the Welcome to Setup window, hit **Enter** to "set up Windows XP now".
1. At the License window, hit F8.
1. Setup should find a partition of the site you set a few steps back. If not, start over with these instructions. If so, click **Enter**.
1. Assuming the location of the VDI is on your local drive and you have not been having any problems in your host OS, click **Format the partition using the NTFS file system (Quick)**. Choosing the alternative (missing "Quick") is much longer because it inspects the disk space for any physically damaged blocks. Oh, and we don't want FAT these days. Use the up and down arrows on your keyboard for the selection, and then **Enter**.
1. Setup will run for several minutes. Then it reboots. Do not hit any keys to "Boot from the CD" if the prompt comes up.
1. We're now at the GUI, or Graphical User Interface. Enter the information that Setup asks for, you can leave the Administrator password blank if you wish.
1. Unless you have a special network setup, accept the defaults for network settings, including Workgroup.
1. Setup will run on for a bit.
1. You are now at the rest of the GUI setup.
1. After the setup, Power Off the Machine.
1. Select the machine and go to Settings | Network. These settings work on my Dell Latitude D620: select **NAT** and ****
1. Start the machine
1. Click **Devices** at the top
1. Select **Insert Guest Additions CD Image** and accept all default. Choose **Continue Anyway** any time it pops up. Click **Finish** to reboot.