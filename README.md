# OPNSense on the Cyberoam-CR15ing

This is an x64_64 based machine 3x gigabit LAN ports, a CF Card Slot, a SATA port and 2GB RAM. It looks like this inside:

![20210826_104322](https://user-images.githubusercontent.com/2738833/130890464-9527763a-c76c-461a-a10f-7d52f2ab1ae7.jpg)

Hooking up a Cisco-style console cable give access to the serial console (they are usually this light-blue color):
![20210826_110914](https://user-images.githubusercontent.com/2738833/130890603-eb123945-233d-42b3-b588-2785cc6381ee.jpg)

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





