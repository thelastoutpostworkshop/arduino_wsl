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

>Install the nemo Linux file manager (optional)

```shell
sudo apt install nemo
```

>You can open the Arduino IDE with a double-click on the Arduino Image icon in the nemo file manager or launch it with this command
```shell
./arduino-ide_2.3.6_Linux_64bit.AppImage
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