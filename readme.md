![image](https://github.com/user-attachments/assets/b445bee7-1fef-4fb7-956c-b6c24f962f0a)



# How to Create a Minecraft Server out of an Old Windows PC with Linux

## Prerequisites:

* Any old windows x86 computer from 2009 and newer, **THIS WILL BE WIPED.**

* Any USB flash drive 8GB+ **THIS WILL BE WIPED.**



## 1. Download Ubuntu Server/Rufus

1. go to [Ubuntu's website](https://ubuntu.com/download/server) and download the latest LTS version of Ubuntu Server.
   
   * Download an x86 image if you are running a 32-bit CPU
   
   * Download an x86-64 image if you are running a 64-bit CPU

2. download [Rufus](https://rufus.ie/en/). This will be used to flash Ubuntu to your USB drive.



## 2. Flash Ubuntu to your USB drive

1. Open Rufus and select the correct device from the drop-down menu. 

2. beside "boot selection" click "SELECT" to the right and choose your Ubuntu Server image. 

3. Click "START" at the bottom of the Rufus window, and proceed with flashing your USB drive.

4. Once flashing is finished, eject the USB drive from your PC. 



## Install Ubuntu Server on your old PC

1. Find the BOOT MENU key for your old PC by doing a Google search

2. Ensure your old PC is powered off.

3. Insert your USB stick into your old PC.

4. Spam the BOOT MENU key that you found in step 1 and turn the PC on while doing so.

5. A simple menu should appear on the screen -> choose your USB drive as the boot device by using the arrow keys and enter.

6. Wait for the setup to load, the screen might look weird but just wait.

7. Select your language and keyboard layout.

8. Under **"network connections"** write down the **DHCPv4** ip address **of your networking.** **Save this for later.**

9. Continue the setup, skip "proxy address" and "mirror address."

10. Once on the storage configuration, **select** "use entire disk" and **deselect** "set up this disk as an LVM group."

11. Hit done on the install summary

12. Confirm

13. Set up your:
    
    * name
    
    * server's name
    
    * username
    
    * password **(make it secure)**

14. confirm -> confirm

15. Select to:
    
    * install OpenSSH server
    
    * confirm
    
    * install the **Docker** "snap" package.
    
    

16. confirm.

17. Wait for the setup to complete.

18. Remove your flash drive **when prompted.**

19. wait for your server to reboot

## Configure SSH for Remote Access

1. Install OpenSSH on your main computer (not the one we just configured) by following [this](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui) guide from Microsoft.

2. Open PowerShell as administrator.

3. plug your server into your PC via direct ethernet or ensure it is accessible through your home network. **Make sure it has access to the internet for later.**

4. type "ssh YOUR_SERVER_USERNAME@YOUR_DHCPv4_IP"

## Using SSH to Configure the Server

1. type "sudo apt-get update" 
   
   -> type your password

2. type "sudo apt-get **upgrade**"
   
   -> type your password

3. type "clear"

4. type "sudo groupadd docker"

5. type "sudo gpasswd -a YOUR_SERVER_USERNAME docker"

6. restart your server with "sudo reboot"

7. type "docker ps"
   
   * we will be using docker to run the minecraft server

8. type "mkdir mc-docker"

9. type "ls" to confirm the folder was made in your home directory, you should see "mc-docker" in purple.

10. copy the contents of "docker-config.txt" in this repo into your SSH terminal. -> press enter.
    
Once the image is downloaded, open your minecraft app and add your server using your ip address and server name from before.

## Enjoy!

You have just created a minecraft server! It is currently only accessible from within your intranet, but if you want a more permanent solution accessible from anywhere, look into free services like [ngrok]((https://ngrok.com/download). 


