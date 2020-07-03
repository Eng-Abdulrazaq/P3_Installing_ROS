# Installing ROS Noetic
You can download a pdf version of this tutorial [here](https://github.com/Eng-Abdulrazaq/P3_Installing_ROS/blob/master/ROS%20intallation.pdf)



## 1. Configure repositories:
Software programs consist of small parts called packages, and some of these packages are common
between programs. If you intend to install a program in Ubuntu, the operating system will gather
these packages from sources, but it will check first that if common packages are already installed by
another software, then it will download missing packages. This is how Ubuntu works, in order to
reduce download time and storage space on the computer.

Ubuntu is configured to download packages from certain sources, called repositories. They are of
four types:
- a) Main: Canonical-supported free and open-source software.
- b) Universe: Community-maintained free and open-source software.
- c) Restricted: Proprietary drivers for devices.
- d) Multiverse: Software restricted by copyright or legal issues.

ROS needs “restricted”, “universe” and “multiverse” repositories. They should be enabled by
default, but to make sure that the installation process goes smoothly, open the terminal and write the
following commands one by one. If If the terminal asks for your password, write it and press
“Enter” or “Return” on your keyboard. You will not see anything being written, but your input is
actually recorded.

```
sudo add-apt-repository universe
sudo add-apt-repository restricted
sudo add-apt-repository multiverse
```
![IMAGE ALT TEXT HERE](/Screenshots/1.png)

If the commands return errors consult the official Ubuntu guide here.
https://help.ubuntu.com/community/Repositories/Ubuntu

## 2. Setup your source list to accept ROS packages
In the first step, Ubuntu was set to look for software packages in certain repositories. Now it is
needed to configure Ubuntu to look for and accept packages from “packages.ros.org”. It is easier to
do that in terminal with the following command
``` 
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' 
```
![IMAGE ALT TEXT HERE](/Screenshots/2.png)

Terminal will not give back any response, but to check that the source was set, go to “Software &
Update”, and from “Other Software” tab you should find “packages.ros.org” listed and checked.
![IMAGE ALT TEXT HERE](/Screenshots/3.png)

## 3. Add authentication key
When you command Ubuntu to install a software, it searches for needed packages and download
them. But before it installs any, it authenticates their integrity with preconfigured keys. So, before
you start installing ROS, you should add the key to your list by the following command
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key
C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
![IMAGE ALT TEXT HERE](/Screenshots/4.png)

Terminal output should indicate that the key as imported.


## 4. Installation
Now, update the list of available packages, so that terminal can download and install ROS, using the
following command
```
sudo apt update
```
Enter your password and wait for terminal to finish

![IMAGE ALT TEXT HERE](/Screenshots/5.png)

Now ROS can be installed with the following command, which will install additional packages
beside ROS. If you do not need all packages, refer to http://wiki.ros.org/noetic/Installation/Ubuntu
for more options
```
sudo apt install ros-noetic-desktop-full
```
![IMAGE ALT TEXT HERE](/Screenshots/6.png)

Terminal will list all packages that will be downloaded or updated for installation, and it will ask
your permission to proceed. Type “y” to continue or “n” to abort. 

![IMAGE ALT TEXT HERE](/Screenshots/7.png)

After you permit, terminal will
download and install packages. You will find progress percentage at the bottom.

![IMAGE ALT TEXT HERE](/Screenshots/8.png)

When installation process is completed, you can check that with the following command
```
apt list --installed | grep ros-noetic
```
This command will list all installed packages of ROS Noetic

![IMAGE ALT TEXT HERE](/Screenshots/9.png)

## 5. Setting up the environment
At this point, you must source a script every time you want to use ROS. So, it is convenient to
make terminal sources this script once it is launched. It is performed by this commands one by one
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```
```
source ~/.bashrc
```
![IMAGE ALT TEXT HERE](/Screenshots/10.png)


## 6. Confirming installation
Finally, close all terminal windows and start a fresh one. Write the following command in terminal.
```
rosversion -d
```
If terminal responds with “noetic”, then you are all set

![IMAGE ALT TEXT HERE](/Screenshots/11.png)


## 7. Reference and credit
The following links are credited for instructions mentioned above. Refer to them for much detailed
instructions

http://wiki.ros.org/noetic/Installation/Ubuntu

https://help.ubuntu.com/community/Repositories/Ubuntu

https://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository

https://help.ubuntu.com/community/Repositories/CommandLine

https://github.com/qboticslabs/ros_install_noetic

https://www.cyberciti.biz/faq/apt-get-list-packages-are-installed-on-ubuntu-linux/
