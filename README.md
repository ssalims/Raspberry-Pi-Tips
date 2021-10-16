====================================================================================================================================
# Collections of Raspberry-Pi-Tips
====================================================================================================================================

-----------------------------------------------------------------------------------------------------------------
^^ What to do when you get the warning message “REMOTE HOST IDENTIFICATION HAS CHANGED” from your Raspberry Pi ^^
-----------------------------------------------------------------------------------------------------------------
Reason: An OS security feature with the intent to avoid Man-in-the-Middle attacks.

---> ssh-keygen -R IP-address

************************************************************************************************************************************
************************************************************************************************************************************


-------------------------------
^^ Headless ssh & WiFi Setup ^^
-------------------------------
credit to: https://desertbot.io/blog/headless-raspberry-pi-4-ssh-wifi-setup
i. Enable ssh
-------------
--> mac
touch /Volumes/boot/ssh

--> windows
Run Notepad
In a new file put in one space and nothing more
Click File / Save As ...
Be sure to set Save as type to All Files (so the file is NOT saved with a .txt extension)
Call the file ssh and save it
Close the file

If you are comfortable with the Windows command line you could try this instead (untested!):

Open up a command line
Switch to the drive and root where boot is located:
Type: type NUL >> ssh
Verify that file ssh was created

ii. Adding WiFi info
--------------------
touch /Volumes/boot/wpa_supplicant.conf

--> mac & windows
country=MY
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}

iii. Remote Logging
-------------------

for mac:
ssh-keygen -R raspberrypi.local
ssh pi@raspberrypi.local

default password is raspberry

for windows:
-install bonjour
-install putty 64bit

iv. Login over WiFi using Putty
-------------------------------

This part assumes that ssh is enabled for your image and that the default user is pi with a password of raspberry.

Launch Putty
Set the Host Name (or IP address) field to **raspberrypi.local**
By default the Port should be set to **22** and Connection type should be set to **SSH**
Click **Open**
If you see a Security Alert select **Yes**
A new terminal window should appear prompting you for a user name
The default user name is: **pi**
The default password is: **raspberry**


************************************************************************************************************************************
************************************************************************************************************************************

  
  
