# Use the Arduino IDE in WSL (Windows 11 or 10)
## WSL Installation
> Enable **Windows Subsystem for Linux** in optional features

![](/images/optional_features.png)

> Run these commands in powershell as Administrator\
> This will install wsl and 
> **you will have to restart your computer and after the restart is complete an Ubuntu linux distribution will installed**

>List avalaible Linux distribution

```cmd
wsl -l -o
```
>Install Ubuntu 24.04

```cmd
wsl --install --Ubuntu-24.04
```
>Open a terminal Window and select the Ubuntu installed to start it
>You will be asked to create an account with a password

![](/images/select_ubuntu_terminal.png)



## Arduino IDE installation in WSL
>Download **AppImage 64 bits (X86-64)** from the [arduino web site](https://www.arduino.cc/en/software/)

>Open the Linux file distribution with this command in the Windows Search Bar: `\\wsl$`

>Copy the **AppImage 64 bits (X86-64)** in the home folder of your distribution

>In the Ubuntu terminal windows, type this command to give execute permission to the arduino application image

```shell
sudo chmod +x arduino-ide_2.3.6_Linux_64bit.AppImage 
```

>Install the Arduino IDE dependencies

```shell
sudo add-apt-repository universe
sudo apt install libfuse2
```

>Install the nemo Linux file manager

```shell
sudo apt install nemo
```

>You can open the Arduino IDE with a double-click on the Arduino Image icon in the nemo file manager or launch it with this command
```shell
./arduino-ide_2.3.6_Linux_64bit.AppImage
```
## usbipd installation and use
>In a Windows terminal, type this command to install usbipd to share usb ports with WSL (you may have to restart your computer)
```cmd
winget install usbipd
```
>In the Ubuntu terminal windows, type this command to give your linux account access to USB ports
```shell
sudo usermod -aG dialout (your user login)
```
>Connect your development board to a USB port and in a Windows terminal, type this command to list ports
```cmd
usbipd list
```
>Bind the port where you development board is connected with this command (replace 1-7 with the actual number of your port in the list)
```cmd
usbipd bind --busid=1-7
```
>Share your port with WSL with this command (replace 1-7 with the actual number of your port in the list).  You will have to re-exectute this command if you unplug and replug your development board from the USB port.
```cmd
usbipd attach --wsl --busid=1-7
```

## Troubleshooting
### Enable virtualization in the BIOS
> If you get an error message like this saying that you have to enable virtualization in the BIOS when you start the Linux distribution

![](/images/ensure_virtualization.png)
> Restart your computer and go the bios to enable virtualization (check your manufacturer’s bios documentation)

### failed to create dri2 screen
> If you get a "failed to create dri2 screen" or somehting similar in Ubunto when starting the nemo file manager or the arduino IDE, type this command in the Ubuntu terminal

```shell
export LIBGL_ALWAYS_SOFTWARE=1
```

### usbpid 'warning: USB filter 'TsUsbFlt' is known to be incompatible'
> If usbpid warn you that USB filter is in place, open the registry editor in Windows and locate this ressource and delete "Upper Filters"\

`
Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\{36fc9e60-c465-11cf-8056-444553540000}
`
>Reboot your computer for the change to take effect

### Arduino IDE : permission denied to use the USB port
>If you get a permission denied to use the port in the Arduino IDE, in the Ubunto terminal, type this command

```shell
sudo usermod -aG dialout (your user login)
```

> Shutdown wsl for the change to take effect, in the powershell terminal, type

```cmd
wsl --shutdown
```

> Reopen your Ubuntu termial and launch the Arduino IDE
