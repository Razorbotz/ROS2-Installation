# Razorbotz ROS2 Installation Page
This page is intended to house the installation instructions for ROS2 and the VirtualBox VM file.  **The easiest option is to use the prebuilt virtual machine that is located in this repository.**  To create a new virtual machine and install ROS2, refer to the Installing VirtualBox and the Installing ROS2 sections.  To install this project on Linux, disregard the VirtualBox instructions and follow the Installing ROS2 instructions.  To install ROS2 natively on Windows, please refer to the Installing ROS2 on Windows section.

## Overview
* [Installing the Prebuild VM](https://github.com/Razorbotz/Installing-ROS2/tree/master#download-and-install-the-prebuilt-vm)
* [Installing VirtualBox](https://github.com/Razorbotz/Installing-ROS2/tree/master#installing-virtualbox)
* [Installing ROS2](https://github.com/Razorbotz/Installing-ROS2/tree/master#installing-ros2)
* [Installing on Windows](https://github.com/Razorbotz/Installing-ROS2/tree/master#installing-on-windows)

## Download and Install the Prebuilt VM
To begin the project, download and install VirtualBox](https://www.virtualbox.org/wiki/Downloads).  After installing VirtualBox, download the [prebuilt VM](https://github.com/Razorbotz/ROS2-Installation/blob/master/RazorbotzLinuxVM.vdi) from the Github.  After downloading the VM, open VirtualBox.  To create a new virtual machine, press the New button.

![New Button](https://github.com/Razorbotz/ROS2-Installation/blob/pictures/pictures/Installation_1.PNG)

After pressing New, name your virtual machine and select the Linux and 64-bit options, as shown in the following picture.  After selecting the correct options and the name, click Next.

![Create Dialog Box](https://github.com/Razorbotz/ROS2-Installation/blob/pictures/pictures/Installation_2.PNG)

After setting the name and type of the virtual machine, select the amount of allocated RAM and then press Next.

![RAM Dialog Box](https://github.com/Razorbotz/ROS2-Installation/blob/pictures/pictures/Installation_3.PNG)

On the Create Virtual Machine dialog box, select the Use an existing hard disk file option.  Press the browse files button to the right of the drop down menu.

![Create Virtual Machine Dialog Box](https://github.com/Razorbotz/ROS2-Installation/blob/pictures/pictures/Installation_4.PNG)

On the Hard Disk Selector dialog box, click Add and navigate to the file location RazorbotzLinuxVM.vdi downloaded to.  Select the Razorbotz file and click Choose.

![Hard Disk Selector Dialog Box](https://github.com/Razorbotz/ROS2-Installation/blob/pictures/pictures/Installation_5.PNG)

The Create Virtual Machine dialog box should now show the RazorbotzLinuxVM.vdi file being selected.  Click the Create button to create the virtual machine.

![Create Virtual Machine Dialob Box With Correct File](https://github.com/Razorbotz/ROS2-Installation/blob/pictures/pictures/Installation_6.PNG)

The virtual machine should now be created.  To start the virtual machine, select it from the menu on the left and click the Start button.

## Installing VirtualBox
To install VirtualBox, first download the software [here](https://www.virtualbox.org/wiki/Downloads).  After downloading and installing VirtualBox, download an image of [Ubuntu 20.04](http://releases.ubuntu.com/20.04/) and install Ubuntu.  A tutorial on how to do so is located [here](https://linuxhint.com/install_ubuntu_virtualbox_2004/).  To allows the virtual machine to be able to be full screen, enter the following commands in the terminal:

```
sudo apt update

sudo apt install virtualbox-guest-dkms virtualbox-guest-x11 virtualbox-guest-utils
```

After executing the commands, click on the Devices drop down menu at the top of the virtual machine.  Click on Insert Guest Additions Image, then click Run and enter the password when prompted.  For any issues, please consult this [installation guide](https://linuxhint.com/install_ubuntu_virtualbox_2004/#:~:text=Installing%20VirtualBox%20Guest%20Additions%20on%20Ubuntu%2020.04%20LTS).

## Installing ROS2
The project uses the Foxy distribution of ROS2.  To build from source or install on other operating systems, refer to the [Installation Page](https://docs.ros.org/en/foxy/Installation.html).  **To install the Foxy distribution of ROS2 using Debian packages, run the following Linux terminal commands inside the virtual machine or on a native Linux machine.**

### Set locale
```
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

### Setup Sources
```
sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo sed -i -e 's/ubuntu .* main/ubuntu focal main/g' /etc/apt/sources.list.d/ros2.list

```

### Install ROS2 Packages
```
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

sudo apt update

sudo apt install ros-foxy-desktop
```

## Installing on Windows
There are two options available to develop with ROS2 natively on Windows.  To install ROS2 using the Binary distribution of ROS2, please refer to the [documentation](https://docs.ros.org/en/foxy/Installation/Windows-Install-Binary.html).  The second option is to [build the ROS2 files from source](https://docs.ros.org/en/foxy/Installation/Windows-Development-Setup.html), which allows for more control over the compilation process.  
