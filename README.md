# PiZeroW-Rubber-Ducky
A self driven project to make a modified version of a rubber ducky. 
```
      _      _      _       _      _      _          _      _      _       _      _      _  
   __(.)< __(.)> __(.)=   >(.)__ <(.)__ =(.)__    __(.)< __(.)> __(.)=   >(.)__ <(.)__ =(.)__
   \___)  \___)  \___)     (___/  (___/  (___/    \___)  \___)  \___)     (___/  (___/  (___/ 
```
## Steps
1. GATHER [PARTS](##Materials) AND ASSEMBLE 
      * Attatch USB stem to Pi Zero by soldering
      * (OPTIONAL) Print case 
2. GETTING THE ENVIRONMENT SETUP
      * (SIDENOTE) Use balenaEtcher for Mac or Rufus for Windows
      * [Download](https://www.raspberrypi.org/downloads/raspbian/) Raspbian Jessie Lite image and flash it to the SD card
      * Open the SD card from your Mac or Windows
      * Create a new file called ssh (The file will be left blank, it just needs to exist in the /boot folder(just the main               folder with other junk in it))
      * Create a new file called wpa_supplicant.conf 
            
            country=us
            update_config=1
            ctrl_interface=/var/run/wpa_supplicant

            network={
            scan_ssid=1
            ssid="MyNetworkSSID"
            psk="Pa55w0rd1234"
            }
            
      * At this point you should plug the pi into your computer. The green light should be lighting up confirming that                    everything is connected and working properly. 
      * From your terminal run 
      
            ssh-keygen -R raspberrypi.local
            ssh pi@raspberrypi.local
            
      *   (SIDENOTE) The default password is raspberry
      * run the following commands (in the pi terminal)
      
            sudo apt update
            sudo apt install git
            git clone https://github.com/arrase/Raspiducky.git
            cd Raspiducky
            sudo chmod 777 install.sh
            sudo ./install.sh
            cd ..
            sudo rm -rf Raspiducky
            sudo reboot
      * A prompt should indicate that the pi is now being recognized as a keyboard. I was completing this on MAC and a prompt             to setup a new keyboard appeard
3. CREATING THE PAYLOAD
      * Remove the micro SD from the pi, plug into SD reader, and open it from your desktop
      * Create a new file in onboot_payload called payload.dd
      * This is the file where you can place the payload you would like to execute when the pi gets plugged in
4. INSERT
      * Plug the pi into the USB port of target machine and watch the payload execute
      * Vwola!

## Materials
- 1x Pi Zero W
- 1x Micro USB card (16GB)
- 1x Pi Zero USB Stem
- 1x USB Connector
- 2x Nylon Bolt
- 2x Nylon Screw

## Resouces

List of already created scripts
- https://github.com/hak5darren/USB-Rubber-Ducky/wiki/Payloads

Script Generator
- https://ducktoolkit.com/

Duckberry Pi 
- https://github.com/arrase/Raspiducky

SetUp
- https://zerostem.io/

SSH
- https://www.thepolyglotdeveloper.com/2016/06/connect-raspberry-pi-zero-usb-cable-ssh/

## Hotfixes
1. Not turning on?
      * On the stem usb attatchment, make sure to solder the 4 usb contact points. I left these unsoldered and the pi zero would not turn on upon plugging in. 
      * Also try installing another OS onto the SD. An incorrect image can cause the pi not to boot.


