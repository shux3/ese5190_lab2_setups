# ese5190_lab2_setups
  Written by Shu Xu
  
  Email: shux@seas.upenn.edu
  
  |System     |               Windows 10 Home                   |
  |-----------|-------------------------------------------------|
  |System Type|   64-bit operating system, x64-based processor  |
  |Processor  |Intel(R) Core(TM) i5-9300H CPU @ 2.40GHz 2.40 GHz|
  
## Introduction
This is a guideline to help readers set up their laptops to be ready for flashing c code to QT PY 2040 board, from zero to the first "hello world" c file. Be aware that the whole set up will take a rather long time to run through. Please be patient not to miss the small notices during the installation process.

## Prelab: Terminal, Serial Console and Text Editor
In this prelab part, you will install and set up a terminal, serial console, and text editor for the rest of ESE 5190 course. The goal is to turn your own laptop into a powerful portable development environment that you can use anywhere.

### Part 1 Terminal
In this part, we choose **Ubuntu** as a reference to show you the process to install a terminal to your PC.

#### Step 1.1 Open the Ubuntu
If you don't yet have Ubuntu in your PC, simply open Microsoft Store and search for the latest version. It only takes minutes to finish downloading.
![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/ubuntu.PNG)
*Notice that if you have a older version of Ubuntu existed in your PC, you might run into an error: "The attempted operation is not supported for the type of object referenced". In this case, open up the cmd as admin and copy paste the following command:*

```
	netsh winsock reset
```
For the first timers, follow the first time Ubuntu instructions, set up new user name.

#### Step 1.2 Create File
Create a new '.txt' file named 'test.txt' under lab2 file. Using the following command:

```
	$ cd /mnt/c
	$ cd Users/your user name/Lab2/prelab_setup
	$ touch test.txt
	$ ls
```
You should now be able to see your 'test.txt' file listed below.

#### Step 1.3 Edit File
Edit 'test.txt' use cat command:

```
	$ cat test.txt
```		
Print "Hello World!" in your terminal screen. You should be able to see the changes in your 'test.txt' file.

### Part 2 Text Editor - Vim
Even though you can acess and edit files directly in terminal, Vim is one better option for this purpose. As Vim is a built-in part of Ubuntu, it is already available from your terminal!

Run vimtutor by input command:
```		
	$ vimtutor
```		
Start lesson 1, and follow the instructions to go through at least a few slides. Now you should be able to edit files in a more feasible way(after you get experienced)

### Part 3 Serial Console
Now we need a tool to be able to display the output. For windows users, open [this site](https://learn.adafruit.com/welcome-to-circuitpython/advanced-serial-console-on-windows) and follow instructions on how to install a serial console.

#### Step 3.1 Find the channel you are using.
Open the device manger. Then plug in board to a USB jack, you should be able to see a new list named **Port**. Under Port, confirm which COM# are you using. In the following steps, we will use **COM3** as an example.

#### Step 3.2 PuTTY
Download PuTTY of latest 64 bit version. Open it. Under Connection type on the left, choose Serial.Enter COM3(replace with your own COM#) under Serial line box. Set the speed to 115200. You may also use other serila console you preferred.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/PuTTY.PNG)

*Notice that this board does not require speed change. However, boards with a separate chip(No built in USB) such as ESP8266 requires the speed to be 115200 bits/sec.*

You may also use save/load function to save the setting for future usage. Hit open. A PuTTY window should pop up with a blank screen or with welcome messages.

## Lab 2A: SDK setup
In this part, you will set up your PC for RP2040 development using the official C/C++ SDK, and compile & run example code on your board. This part takes most of the time you will spend in this guideline, but it will be worth it.
This part will be based on section 9.2 of [A Raspberry Pi Pico guideline](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf). It is recommended to read through this document.

### Part 1 Tool Chains
Install the following tool chains:
- [Arm GNU Toolchain](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)
- [CMake](https://cmake.org/download/)
- [Build Tools for Visual Studio 2022](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022)
- [Python 3.10](https://www.python.org/downloads/windows/)
- [Git](https://git-scm.com/download/win)

It is recommended to install them one by one as you go through the following sections:
#### Step 1.1 [Arm GNU Toolchain](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)
- For Arm GNU Toolchain, making sure you choose the right file to download(the file ended with -arm-none-eabi.exe).

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/Arm%20GNU.PNG)

- Then click the box "Add pathto environment variable" at the end of installation.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/Arm%20GNU_after_install.PNG)

#### Step 1.2 [CMake](https://cmake.org/download/)
- For CMake, choose the right 64bit version for windows

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/CMake.PNG)

- Making sure that you select the add path for all users as shown below:

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/CMake_install_option.PNG)

#### Step 1.3 [Build Tools for Visual Studio 2022](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022)
- For vs studio, download the build tool for Visual Studio 2022.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/visual_studio.PNG)

- Then install the Desktop development with C++ only. Make sure to include a full "windows 10 sdk" package as well.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/vs_1.PNG)

#### Step 1.4 [Python 3.10](https://www.python.org/downloads/windows/)
- For python 3, you may want to choose the lastest version of 64 bits(3.10.7 by the time this guidline is published). 

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/Python_version.PNG)

- Also don't forget to select add python 3.10 to path before installing.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/python.PNG)

- Click disable the MAX_PATH length limit at the end of installation.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/python_end.PNG)

#### Step 1.5 [Git](https://git-scm.com/download/win)
- For Git, choose the 64-bit Git for Windows Setup. Unselect the bottom box "Only show new options" to make sure you don't miss the options.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/git.PNG)

- Use anything but vim as default editor

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/git_1.PNG)
- Allow to git from 3rd-party software

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/git_2.PNG)
- Select "Checkout as -is, commit as-is"

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/git_3.PNG)
- Select "Use Windows default console window"'

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/git_4.PNG)
- Select "Enable experimental support for pseudo consoles"

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/git_5.PNG)
		
You may leave any other unmentioned checkbox as it is.

### Part 2 Getting the SDK and examples on your pc.
#### Step 2.1 Download SDK
Open up the "Developer Command Prompt for VS 2022". You may search it from your windows menu. In this command prompt, create a directory named *pico* under your *User* directory, then create another directory named *Downloads* inside *pico*, using the following command:

```		
	$ cd Users
	$ md pico
	$ cd pico
	$ md Downloads
```

*Noticing that if you failed to make changes under user directory, try to reopen the "developer command prompt of vs 2020" with right click and select open as a admin.* 

Within the Downloads directory, run the following commands to install SDK:

```
	$ C:\Users\pico\Downloads> git clone -b master https://github.com/raspberrypi/pico-sdk.git
	$ C:\Users\pico\Downloads> cd pico-sdk
	$ C:\Users\pico\Downloads\pico-sdk> git submodule update --init
	$ C:\Users\pico\Downloads\pico-sdk> cd ..
	$ C:\Users\pico\Downloads> git clone -b master https://github.com/raspberrypi/pico-examples.git
```	

Now you are ready to make us of SDK

#### Step 2.2 Set up the path
Before you build your c file, set the path to the SDK using the following command:

```
	$ setx PICO_SDK_PATH "..\..\pico-sdk"
```

To make sure that this set up works properly. Close and reopen the command prompt for vs 2022. Use "cd" to Naviage into the "pico-examples" folder, then build the "Hello World" example as follows:

```
	$ cd pico-examples
	$ mkdir build
	$ cd build
	$ cmake -G "NMake Makefiles" ..
	$ nmake
```

This process may take some time.

#### Step 2.3 Flash your *hello world* to board
Finally, it's time to flash the code and run on your board. For RP 2040 board, including QT PY we are using, simply hold down the BOOTSEL button to force it into USB Mass Storage Mode. You should be able to see a new drive appeared. Find 'hello_usb.uf2' under pico-examples\build\hello_world\usb directory,  and drag it to the newly appeared drive. Then open the serial console using PuTTY, you should be able to see the output now.

![alt txt](https://github.com/shux3/ese5190_lab2_setups/blob/main/Image/hello_world.PNG)
