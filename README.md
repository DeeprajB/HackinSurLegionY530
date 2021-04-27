# HackinSurLegionY530

A start to finish Hackintosh Big Sur guide for Lenovo Legion Y530.

**Note** :

* _This guide will be using macOS Catalina to upgrade to macOS Big Sur._
* _This guide will be using Windows to create the **Installation Media (USB).**._  

Lets start with the System Configuration.

### Lenovo Legion Y530

* CPU : Intel i5 8300H (Coffee Lake)
* RAM : 16 GB 2666mhz DDR4 Dual Channel (8+8)
* GPU : Nvidia GTX 1050 4 GB (Disabled for macOS) + Intel UHD Graphics 630 (used for macOS)
* Storage : 2.5 TB (500 GB Nvme SSD + 1 TB inbuilt + 1 TB Western Digital Hard Drive)
* Realtek ALC236 Audio Controller
* Synaptics Precision Trackpad -> ELAN061B

## Guide 

1. **BIOS** 
* **Booting into Advanced BIOS Menu** Go into BIOS by pressing `F2` while booting up, Press `FN + D + O` after getting into the BIOS and restart.
* Once a blue box appears press `F2` to boot into the Advanced BIOS Menu.
* **Edit the following BIOS Options.**
* * **Boot Mode** : UEFI
* * **Storage Mode** : AHCI
* * **Secure Boot** : Disabled
* * **Kernel Debug Serial Port** : Legacy UART
`Advanced -> Debug settings -> Legacy UART`
* * **Force unlock on all GPIO pads** : Enabled | _without this Trackpad will not work on macOS._
`Advanced -> PCH-IO Configuration -> Security Configuration -> Force unlock on all GPIO pads`
* * **CFG Lock (MSR_E2)** : Disabled
`Advanced -> Power & Performance -> CPU - Power Management -> View/Configure CPU Lock Options -> CFG Lock`
* * **DVMT Pre-Allocated Memory** : 64MB
`Advanced -> System Agent (SA) Configuration -> Graphics Configuration -> DVMT Pre-Allocated Memory`

2. **USB Creation (Catalina)**
* 

3. **Booting into the USB (Catalina)and Installing macOS Catalina**
* Shut down the laptop, press the power button and press `F12` to go into the Boot Menu.
* In the Boot Menu select the USB EFI.
* If the USB is succesful in booting up an recovery screen will appear. 
* Click on **Disk Utility** and erase the required drive to **Mac OS Extended (Journaled)**.
* After erasing the drive, we quit the **Disk Utility**.
* Click on Install/Reintsall macOS Catalina to install Catalina on the drive we just erased.
* The system may reboot several times while installing macOS Catalina.
* Once the installation has been completed, an macOS Setup Assistant should appear.
* Complete the setup to enter into macOS Catalina.
* **Congrats !** we have booted into a succesful Hackintosh, if you feel comfortable with Catalina please directly proceed to **POST-INSTALLATION**.

4. **Upgrading macOS Catalina to macOS Big Sur**
* Once booted into macOS Catalina, open Settings and go to Update.
* Disable Beta Updates and download the latest version of macOS Big Sur.
* Once the update downloads, run the update and it will restart after sometime.
* Once it restarts, in the OpenCore boot menu, select **install macOS Big Sur** and not the drive in which Catalina is installed.
* If the update is successful in booting up, an recovery screen will appear.
* Click on **Disk Utility** and make a seperate partition in the same drive as Catalina.
* After making a new partition, we quit the **Disk Utility**.
* Click on Install/Reintsall macOS Big Sur to install Big Sur on the new partition we just created.
* While the installation is going on, the system will reboot several times, each time boot into **install macOS Big Sur** until the option disappears.
* When the option disappears select the new partition we created earlier in **Disk Utility**.
* This should succesfully boot into **macOS Big Sur**.
* **Congrats !**

5. **POST-INSTALLATION**
* Go to Settings and under Trackpad **Disable -> "Force Click and haptic feedback"**.
* To fix the Audio run the following command in **Terminal** 
``sudo sh -c "$(curl -fsSL https://raw.githubusercontent.com/chilledHamza/Hackintosh_Legion_Y530/main/AudioFix.sh)"``
* Ensure everything is working. 
* Download and Run [MountEFI](www.mountefilink.com)
* Select the partition or drive in which macOS Big Sur is installed and mount the EFI. 
* Once the EFI is mounted copy the contents of EFi from the repository and paste it into the mounted EFI.
* Yay! hopefully everything has been correctly installed :') 