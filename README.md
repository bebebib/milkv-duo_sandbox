# milkv-duo_sandbox

This repo is just meant as a collection of quickstart material for easy use of the milkv duo board. Basic instructions for quick start below.

Folders

- **mlkv-duo-img-zip/** - Initial image to flash to board
- **RNDIS/** - Windows driver to talk to duo
- **test-project/** - Source code for testing project

## Setup 

https://milkv.io/docs/duo/getting-started

1. [Install image](https://milkv.io/docs/duo/getting-started/boot) onto SD card using something like balena etcher  
2. Plug in device, should show up as "other" RNDIS device, [install the drivers](https://milkv.io/docs/duo/getting-started/windows-rndis-dirver), after successful install the device should be a USB Ethernet/RNDIS Gadget
3. Attempt to ssh into device `ssh root@192.168.42.1`, and then use pw `milkv`, successful SSH!

## Example Usage

1. SSH into milkv, type this command and reboot to turn off blinking LED: `mv /mnt/system/blink.sh /mnt/system/blink.sh_backup && sync`
2. Turn turn back on, SSH in milk and type this command and reboot: `mv /mnt/system/blink.sh_backup /mnt/system/blink.sh && sync`

## Development

### Linux (orginally done in WSL2)

Required installations
- [Duo SDK](https://github.com/milkv-duo/duo-app-sdk/releases/download/duo-app-sdk-v1.2.0/duo-sdk-v1.2.0.tar.gz)

1. Do a wget of the Duo SDK tar ball, then unzip into `/opt/` with the following command: `tar -xf duo-sdk-v1.2.0.tar.gz -C /opt/`
2. Installation of Linux packages `scp`, `sshpass`, `cmake`, and `ninja`
3. Configure CMake with 
```
$ cmake --build build --config Debug --target clean --
```
4. Execute the `load-project-exe` target with
```
$ cmake --build build --config Debug --target load-project-exe --
```
5. The file `test_project` should be on target on your home directory on the milkv duo
6. While in a SSH session on the milkv duo, run the executable with the command
```
[root@milkv-duo]~# ./test_project
```

## TODO

This is a dual core processor, Linux on one, FreeRTOS on the other, how to get FreeRTOS apps built and loaded?
