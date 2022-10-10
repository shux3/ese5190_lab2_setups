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

#### Step 1.1 Open the Ubuntu app already existed in my PC
If you don't yet have Ubuntu in your PC, simply open Microsoft Store and search for the latest version. It only takes minutes to finish downloading.

*Notice*
 open up the cmd as admin and copy paste the command:
	       netsh winsock reset. Which may be necessary for every time we open Ubuntu. Another solution would be
               downloading NoLSP.exe from the same website.
	
		Problem solved.
	
	Step4: Follow instructions, set up new user as Shu Xu (shux), then create a new '.txt' file named 'test.txt' under
	       lab2 file. Using the following command:

		$ cd /mnt/c
		$ cd Users/Xu199/Desktop/UPenn/2022Fall/ESE5190/Lab2/prelab_setup
		$ touch test.txt
		$ ls
		
		Successfully created a file named 'test.txt' in prelab folder.

	Step5: Print "Hello World!" in 'test.txt' use cat command to print it on terminal:

		$ cat test.txt
		
		Successfully printed the contents of the txt file.

P2.3 Vim
	Step1: Run vimtutor by input command:
		
		$ vimtutor
		
		Start lesson 1, and follow the instructions to go through at least a few slides.

P2.4 Serial Console
	(The guiding site: https://learn.adafruit.com/welcome-to-circuitpython/advanced-serial-console-on-windows)
	Step1: Open the device manger. Then plug in board to a USB jack, and confirm that COM3 is being used.

	Step2: Download PuTTY of latest 64 bit version. Open it.

	Step3: Under Connection type on the left, choose Serial.
	       Enter COM3(my board COM channel) under Serial line box.
	       Set the speed to 115200(baud rate, the speed in bits per second). Notice that this board does
	       not require this change. However, boards with a separate chip(No built in USB) such as ESP8266
	       requires the speed to be 115200 bits/sec.

	Step4: Use save/load for future usage. Hit open. A PuTTY window should pop up with a blank screen or
	       welcome messages.
