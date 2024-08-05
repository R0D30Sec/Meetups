![Hack The Box Calgary](images/hack-the-box-calgary.png)
# 1-Welcome
Welcome to the first Meetup for Hack The Box Meetup: Calgary, CA!
Scheduled for September xx, 2024.

Opening presentation slides can be [found here](https://drive.google.com/file/d/1f_9qlvNIv0u6zQlfcMMGBMZHWtPUbztk/view?usp=sharing).
# Meetup agenda
1. Opening presentation and icebreakers (~30 minutes)
2. Hack The Box Lab walkthrough (~30 minutes)
3. Prizes? (~5 minutes - TBD by Hack The Box staff)
4. Socialization (As long as anyone would like to stay afterwards)
# Walkthrough
To help those who are new to Hack The Box, we will be walking through how to connect the the platform and how to [pwn](https://www.merriam-webster.com/dictionary/pwn) the simplest box named "Meow", which is the first machine in Starting Point.
## Setting up a Virtual Machine
The recommended and most cost effective way to connect to Hack The Box is by using a Virtual Machine. If you have never heard of the term "Virtual Machine" before, think of it as a full computer and operating system that you can interact with inside of another windowed application on your computer. There is much more to understand about Virtual Machines, but that is enough of an understanding to get up and running with Hack The Box.
You may be wondering *why* we need this Virtual Machine. In our case we will be installing the Linux operating system within the virtual machine. Specifically a distribution of Linux named Kali Linux, which is designed for digital forensics, penetration testing, and ethical hacking. Kali Linux will be the operating system and toolkit we will use to play Hack The Box. Follow the steps below to install Kali Linux. Once you are finished, you may want to explore the [Linux Fundamentals]([Linux Fundamentals Course | HTB Academy (hackthebox.com)](https://academy.hackthebox.com/course/preview/linux-fundamentals))module on Hack The Box Academy if you are brand new to Linux. There are also countless resources available online to help you learn all about Linux and how to use it.
1. Visit [virutalbox.org]([Oracle VM VirtualBox](https://www.virtualbox.org/))and download the latest version of Virtual Box. This will allow you to run Virtual Machines on your computer. Follow either this [Windows Installation](https://youtu.be/8mns5yqMfZk?si=cWbudluStBmWh-Xy) or [Mac Installation](https://youtu.be/_Kz1hHT3pq4?si=jVnbTUBlx7ZO1Xuq).
2. Visit [this page]([Get Kali | Kali Linux](https://www.kali.org/get-kali/#kali-virtual-machines))to download a pre-built Kali Linux virtual machine. Make sure to pick the 64-bit Virtual Box. Follow [this video](https://youtu.be/vnX1NaF4K-Q?si=CaBKJJGIF3HaEePo)to install Kali Linux using Virtual Box.
3. After you install both Virtual Box and Kali Linux, you will be ready to play Hack The Box.
## Connect to Hack The Box (HTB) Lab Machine
Using the Kali Linux virtual machine (VM), Visit https://www.hackthebox.com/ using your preferred web browser.

Navigate to HTB Labs
![Hack The Box Calgary](images/htb-labs.png)
In the left side navigation, choose "Starting Point".
![Starting Point navigation](images/starting-point-navigation.png)
On the Starting Point landing page, you will see the machine named "Meow". This is the simplest machine on Hack The Box, and the perfect place to begin learning how to use Hack The Box Labs. In this case you can see the machine has been Pwned. By the end of this walkthrough, you will have Pwned the machine as well!
![Starting Point landing page](images/starting-point-landing-page.png)
In the top right corner click "CONNECT TO HTB", and then click "Starting Point".
![Connect to HTB](images/connect-to-htb.png)
You will then be presented with the option to connect to the Starting Point server using either OpenVPN or Pwnbox. It is recommended that you choose OpenVPN if this is your first time using the platform. In the case that you are already a paid HTB VIP or VIP+ subscriber, choose Pwnbox. These subscriptions either a generous or unlimited amount of Pwnbox in-browser experience.
![Connect to Starting Point](images/connect-to-starting-point.png)
Leave the default "VPN Access" and "VPN Server" selections, and choose "TCP 443". I have found this more reliable than the UDP option for connecting. Then click "DOWNLOAD VPN" You should see an .ovpn file within your downloads folder. This file will allow us to use OpenVPN to connect to the Hack The Box server.

Open the terminal application. By default you will be in the user's root directory, otherwise known as `/home/kali/`. Type the following command to navigate to the downloads folder. `cd downloads`. `cd` stands for change directory, and it is a way to traverse the file system. Remember this command as it is one of the most commonly used.

To view all of the files in a directory, type `ls` into the terminal. You should see a file named something like `starting_point_R0D30.ovpn`. You should see your own Hack The Box username in the filename instead of `R0D30`.

To connect to Hack The Box server enter the command `sudo openvpn starting_point_R0D30.ovpn`. Make sure to replace the name of the `.ovpn` file will the name of the file you downloaded. You will be asked to provide the password for kali which is also `kali`.

After the configuration script has run, you should see a line `Initialization Sequence Completed` printed out into the terminal. Refresh the Hack The Box webpage in your browser, and should "STARTING POINT" change from the colour red to green. You are now connected to a Hack The Box server and ready to hack the target machine.
![Connection established](images/connection-established.png)
## Hacking your first box
We will begin with the simplest Lab machine in named "Meow", which has been designed specifically for beginners. Within the Hack The Box Starting Point webpage, expand the Meow machine and click the green button "SPAWN MACHINE". This will tell Hack The Box to initialize a temporary machine that we can practice our hacking skills on.
![Expand Meow](images/expand-meow.png)

Wait for one or two minutes while Hack The Box creates the machine. If this takes longer than five minutes, try refreshing the webpage.
![Creating instance](images/creating-instance.png)

Once the temporary machine instance has been created, you will be provided with it's IP address. This is not a public IP address that you can visit within your web browser, but instead a network location within the Virtual Private Network (VPN) we connected to earlier using the terminal application. It is now time to evaluate and attack this target machine.
![Machine online](images/machine-online.png)
## Enumeration
One of the most common first steps when approaching a box is what's known as `Enumeration`. This is the process of evaluating and documenting the current state of our target machine to learn as much as we can about it, including potential vulnerabilities.