### Step to enable the boot screen on PC GPUs on cMP 

1. **Check the Detailed GPU List from this list**
https://forums.macrumors.com/threads/gpu-compatibility-list-for-cmp.2174600/

2. **Enable GOP**

   -    Refer detailed instruction "https://forums.macrumors.com/threads/enablegop-pre-opencore-gop-support-for-efi-era-imacs-and-mac-pros.2378942/post-32137842" 

    -   Refer this video, it should be self explanatory. I can not explain better than this. 
    "https://www.youtube.com/watch?v=o3mFlSQ1jJ8"


3.  **Process the flash the AMD GMP vBIOS**
    
    -   with reference to
    AMP GPU vBIOS flash (https://www.youtube.com/watch?v=eBuc_Nk05K8)

    3.1 **Installed windows 10 on cMP**

    -   created a USB drive with windows 10 using Windows Laptop and Microsoft built software "Media creation tool"
    -   removed all the hard drives except the one where windows was intended to be installed.
    -   simple but lenghty next-next wizard to install windows on one terabyte hard disk.(tempororily, not a windows fan as of now)

    3.2 **Check if the RX580 working on Windows**

        -   plugged to Windows and connected both of the GPUs (ATI Apple Built-in with DVI to HDMI connected) and RX580 with HDMI and DP also.
        -   windows came up with only from ATI Apple Built-in card nothing from old purchase RX580 which was working fine on MACOS as metal card
        -   RX580 was spinning but it was detected as Microsoft Generic thing, no output from any of the port.
        -   tried changing Monitors and Cable, same result.
        

    3.3 **Check the current config of RX580**

    -   Installed "Techpowerup GPU Z" tool (https://www.techpowerup.com/download/techpowerup-gpu-z/)
    -   It was easy and could save the current BIOS of both of the cards installed on MACPRO 5,1 (cMP) using this tool. There is scroll down button to select the current GPU config in the tool itself.
    -   could see there is some memory shown as "Zero" which created doubt in my mind that this card must have been used for some other purposes and some vBIOS has been installed into it. And we must restore the original vBIOS of this card.
    -   also from the "Techpowerup GPU Z" tool we could see the Graphics BIOS Version which is like "015.050.002.001.000000"

    3.4 **Finding currect and updated vBIOS for RX580**
    -   Again Techpowerup helped to find the correct vBIOS for my card i.e. MSI RX 580 ARMOR OC 8 GB "https://www.techpowerup.com/gpu-specs/msi-rx-580-armor-oc-8-gb.b4430", go to https://www.techpowerup.com/vgabios/ and filter it to your Card Version. I did for this card as "https://www.techpowerup.com/vgabios/?architecture=AMD&manufacturer=MSI&model=RX+580&version=&interface=&memType=&memSize=8192&since="
        -   it listed as 10 vBIOS versions, I downloaded and tried all but you must choose the latest and the greatest, for me it was "https://www.techpowerup.com/vgabios/191946/MSI.RX580.8192.170314.rom", this is the new vBIOS we are going to install in our RX580.

    3.5 **Downloading and running the "AMDVBFlash / ATI ATIFlash" tool**

    -   use the version 3.31 for RX580 since the newer version is not for RX580.
    -   unzip and there are two main folders one is installer(AMDBFlshDriverInstaller) and another one is winflash tool "amdbflashwin". both of the tools must be run as administrator one by one.
    -   firstly installer toold install this and make pc ready for running the other tool.
    -   amdbflashwin tool has the option to save the existing GPU ROM and also to flash the newer ROM in the selected GPU. It is easy and only take 1 minute to compelte and will ask to reboot the PC. Once that is done, check the new vBIOS using "Techpowerup GPU Z" tool, it should have the newer ROM version we downloaded earlier.

    3.6 **Verify with MACOS Mojave**

    -   now remove all the hard drive and plug the MACOS installed hard drive, and keep both card installed with current DVI and HDMI/DP connection intact. Power on Machine and see if there is any change.
    -   Yes, this time I could see the bootscreen with ALT-button pressed and it shown the option to choose the hard drive to boot from.
    -   now shutdown the machine and remove the ATI GPU and keep RX580 plugged in with HDMI or DP connection, keeping ALT button pressed. Then we see the boot screen again. 

That is what we wanted.

