# milkv-duo_sandbox

This repo is just meant as a collection of quickstart material for easy use of the milkv duo board. Basic instructions for quick start below.

Folders

- **mlkv-duo-img-zip/** - Initial image to flash to board
- **RNDIS/** - Windows driver to talk to duo

## Setup 

https://milkv.io/docs/duo/getting-started

1. [Install image](https://milkv.io/docs/duo/getting-started/boot) onto SD card using something like balena etcher  
2. Plug in device, should show up as "other" RNDIS device, [install the drivers](https://milkv.io/docs/duo/getting-started/windows-rndis-dirver), after successful install the device should be a USB Ethernet/RNDIS Gadget
3. Attempt to ssh into device `ssh root@192.168.42.1`, and then use pw `milkv`, successful SSH!

## Example Usage

1. SSH into milkv, type this command and reboot to turn off blinking LED: `mv /mnt/system/blink.sh /mnt/system/blink.sh_backup && sync`
2. Turn turn back on, SSH in milk and type this command and reboot: `mv /mnt/system/blink.sh_backup /mnt/system/blink.sh && sync`
