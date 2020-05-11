#How to connect a Raspberry Pi to a WPA2 Enterprise Network

#How to connect raspberry pi to BITS-STUDENT wifi

#How to connect raspberry pi to college wifi


Did you wish to connect to Raspberry pi via your University intranet?
Want to access it from anywhere campus-wide?
Well Here's how its done.

This tutorial ilustrates to add a (WPA2 Enterprise Network) WiFi to a 'headless raspberry pi' using terminal (on command prompt or any ssh client like putty). I assume you are already connected to raspberry pi using : ethernet( older versions without microUSB port ), Micro USB cable, or other physical connections.
( Connecting for the first time? )
	{
		
		After esablishing a physical connection with pi, type in the login command mentioned in 'step 6'.
		Enter the password (default is raspberry) and you'll be in. 
		
	}

Step 1:

Edit the wpa_supplicant.conf file present at the below mentioned location. Use your favorite editor such as nano or vi. I'll be using nano

	sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

Step 2:

Append the below mentioned details at the end of file.
Add your credentials for identity and password.


network={

         ssid="BITS-STUDENT"
         scan_ssid=1
         mode=0
         key_mgmt=WPA-EAP
         pairwise=CCMP TKIP
         eap=PEAP
         identity="XXXXXXXXX"
         password="XXXXXXXXXXXXX"
         phase1="peaplabel=0"
         phase2="auth=MSCHAPV2"
}

Step 3:

Save the buffer and exit.

	press Ctrl+X -> y -> enter

Step 4:

Reboot your raspberry pi-

	sudo reboot -h now

Step 5:

Now after pi gets rebooted it will automatically get connected to your university wifi if within range.
By that time you can find your raspi's IP address on your local network.
You can use 'fing' app for android as well as for windows and scan your network.
https://www.fing.com/products/fing-desktop
Otherwise 'Advanced IP scanner', a freeware is available for windows.

Step 6:

Type in the login command line while connected to the wifi

	ssh pi@raspberrypi.local

type the username of your device in place of 'pi' if you have changed it to something else.
