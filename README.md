# OPNSense on the Cyberoam-CR15ing

This is an x64_64 based machine 3x gigabit LAN ports, a CF Card Slot, a SATA port and 2GB RAM. It looks like this inside:

![20210826_104322](https://user-images.githubusercontent.com/2738833/130890464-9527763a-c76c-461a-a10f-7d52f2ab1ae7.jpg)

Hooking up a Cisco-style console cable give access to the serial console (they are usually this light-blue color):

![20210826_110914](https://user-images.githubusercontent.com/2738833/130890603-eb123945-233d-42b3-b588-2785cc6381ee.jpg)

There is also a 4-pin power connector next to the SATA port:

![20210826_110806](https://user-images.githubusercontent.com/2738833/130891172-b883aa17-70d8-4aec-9ab1-66031dbd39ff.jpg)

The pinout appears to be 12v-GND-GND-5v. I had no trouble powering a 2.5" SSD or hard drive from the 5v rail.

Fire up your favorite console software (I'm using minicom) and set the baud rate to 9600. You'll see a prompt where you've got about a second to press DEL to get into the BIOS.

           Aptio Setup Utility - Copyright (C) 2011 American Megatrends, Inc.       
        Main  Advanced  Chipset  Boot  Security  Save & Exit                        
    /----------------------------------------------------+-------------------------\
    |  BIOS Information                                  |Set the Date. Use Tab    |
    |  BIOS Vendor             American Megatrends       |to switch between Data   |
    |  Core Version            4.6.4.1                   |elements.                |
    |  Compliancy              UEFI 2.0                  |                         |
    |  Project Version         C6979103                  |                         |
    |  Build Date and Time     02/06/2013 16:22:41       |                         |
    |                                                    |                         |
    |  Memory Information                                |                         |
    |  Total Memory             2048 MB (DDR3)           |                         |
    |                                                    |-------------------------|
    |                                                    |><: Select Screen        |
    |  System Date             [Thu 08/26/2021]          |^v: Select Item          |
    |  System Time             [02:10:26]                |Enter: Select            |
    |                                                    |+/-: Change Opt.         |
    |  Access Level            Administrator             |F1: General Help         |
    |                                                    |F2: Previous Values      |
    |                                                    |F3: Optimized Defaults   |
    |                                                    |F4: Save & Exit          |
    |                                                    |ESC: Exit                |
    \----------------------------------------------------+-------------------------/
            Version 2.11.1210. Copyright (C) 2011 American Megatrends, Inc.        

           Aptio Setup Utility - Copyright (C) 2011 American Megatrends, Inc.       
              Advanced                                                              
    /----------------------------------------------------+-------------------------\
    |  Node0: AMD G-T24L Processor                       |                         |
    |  Single Core Running @ 1010 MHz  1062 mV           |                         |
    |  Max Speed:1000 MHZ    Intended Speed:1000 MHZ     |                         |
    |  Min Speed:615 MHZ                                 |                         |
    |  Microcode Patch Level: 5000101                    |                         |
    |                                                    |                         |
    |  --------- Cache per Core ---------                |                         |
    |  L1 Instruction Cache: 32 KB/8-way                 |                         |
    |         L1 Data Cache: 32 KB/2-way                 |                         |
    |              L2 Cache: 512 KB/16-way               |-------------------------|
    |  No L3 Cache Present                               |><: Select Screen        |
    |                                                    |^v: Select Item          |
    |                                                    |Enter: Select            |
    |                                                    |+/-: Change Opt.         |
    |                                                    |F1: General Help         |
    |                                                    |F2: Previous Values      |
    |                                                    |F3: Optimized Defaults   |
    |                                                    |F4: Save & Exit          |
    |                                                    |ESC: Exit                |
    \----------------------------------------------------+-------------------------/
            Version 2.11.1210. Copyright (C) 2011 American Megatrends, Inc.        

The BIOS is unlocked and appears to be able to boot from USB however I couldn't get this to work (at least not with the OPNsense installer and got fed up trying different combinations, so instead I used a linux box, USB-SATA adaptor and qemu:

    sudo qemu-system-x86_64 -accel kvm -nographic -hda OPNsense-21.7.1-OpenSSL-serial-amd64.img -hdb /dev/<YOUR-DISK> -m 2048
    
The default OPNsense password is 'opnsense'.

To watch OPNsense boot on the Cyberoam you'll need to change the baud to 115200. There is a BIOS option to change the baud rate but I wan't game to try it.




