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

#### Step 3.2 Download PuTTY of latest 64 bit version. Open it.

	Step3: Under Connection type on the left, choose Serial.
	       Enter COM3(my board COM channel) under Serial line box.
	       Set the speed to 115200(baud rate, the speed in bits per second). Notice that this board does
	       not require this change. However, boards with a separate chip(No built in USB) such as ESP8266
	       requires the speed to be 115200 bits/sec.

	Step4: Use save/load for future usage. Hit open. A PuTTY window should pop up with a blank screen or
	       welcome messages.
