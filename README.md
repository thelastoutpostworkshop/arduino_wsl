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

![](/images/select_ubuntu_terminal.png)

> If you get an error message like this saying that you have to enable virtualization in the BIOS

![](/images/ensure_virtualization.png)
> Restart your computer and go the bios to enable virtualization (check your manufacturer’s bios documentation)


## Arduino IDE installation in WSL
>Using the Windows file manager
