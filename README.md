# AxeDoctor

AxeDoctor is a (hardware) monitoring device for skot's ESP-Miner software
(https://github.com/skot/ESP-Miner).

The project uses LILYGO T-Display-S3 ESP32-S3 1.9 inch LCD display development board 
with built-in Wi-Fi and Bluetooth capabilities. The board is equipped with an LX7 
dual-core microprocessor, 16MB of flash memory, 8MB of PSRAM and runs on a 3.3V 
power supply.

# Main features:

* Monitoring of up to 6 ESP-Miner based devices (bitaxe, luckyminer,...);
* The monitored working parameters are:
	 1) Temperature
	 2) Voltage
	 3) Fan speed
	 4) Hashrate
	 5) Shared accepted
	 6) Shared rejected
	 7) Uptime
	 8) Best difficulty
* Simple and intuitive graphical interface:
	 1) Synthetic panel with green/red icons
	 2) Panel with work parameters
	 3) Panel with detected problems
	 4) Screen saver (matrix)
	 5) Automatic display shutdown
* IP detection system of the devices to be monitored:
	 1) Automatic
	 2) Fixed
* Configuration WIFI interface:
	 1) IP devices
	 2) Operating parameters
	 3) Email
	 4) User license
* Sending emails:
	 1) IP configuration and operating parameters
	 2) Periodic report of the operating status of the monitored devices
	 3) List of problems detected by monitoring
* Automatic reboot of blocked devices:
	 1) When low hashrate
* Initial demo version:
	 1) Works up to 4 hours
	 2) It only works 5 times
* Upgrade to fully functional version (without time and power-on limitations):
	 1) By purchasing a regular license


# Preparation

1) Recover the following files:
	
	 1) 0x0000_AxeDoctor_Bootloader_V1.bin
	 2) 0x8000_AxeDoctor_Partitions_V1.bin
	 3) 0x10000_AxeDoctor_Firmware_V1.bin
	
2) Go to https://espressif.github.io/esptool-js/

3) Connect the AxeDoctor to the PC and put it in update mode:
	 1) Connect USB to PC
	 2) Hold down the BOOT button and press the RESET button
	 3) Release the RESET button
	 4) The display must remain off
4) Go to "Program", select Baudrate "115200" and click on CONNECT
5) Select/Add the files from the previous point indicating the corresponding memory address
6) Click on Program
5) Click on DISCONNECT
6) Press the RESET side button


# Configuration

1) Turn on the AxeDoctor and place it near the same router that all the
    ESP-Miner devices to monitor
2) Access the configuration page via WIFI by connecting to the AP called "AxeDoctor_XXXXXXXX"
3) Press the "WIFI config" button
4) Fill out the form:

	 1) AXEIP1/6 field: Enter a fixed IP (ex. 192.168.0.100) of an ESP-Miner device, or
		  AXEIP1: Enter the code "RESCAN" to activate the automatic IP scanning mode
			  every time the AxeDoctor is turned on
		  AXEIP1: Enter the code "AUTO" to scan only the first time and record
			  the IPs found as fixed the next time AxeDoctor is turned on
		  AXEIP2: (experimental) enter an IP address (ex. 192.168.0.100) to be used as a reference on which
			  apply "RESCAN" mode
		  AXEIP6: Enter the code "DELAY" to activate a delay of 10 minutes on start

		  ACTIVATION KEY: enter the license key

		  Enter the desired operating parameters:
		 	 Refresh minutes: Enter how many minutes all monitoring is performed
					  configured ESP-Miner devices
			 Check voltage: Enter 1=YES, 0=NO if you want to enable voltage monitoring
					  power supply of the configured ESP-Miner devices
			 Max temperature: Enter the maximum temperature threshold (C)

		  SMTP Server / Email Port / Email User / Email Password: enter the email configuration

5) Press SAVE and wait for AxeDoctor to restart
6) AxeDoctor will automatically connect to the previously configured WIFI
    ATTENTION: it is very important that at this stage the AxeDoctor recognizes your WIFI router
    (appears at the top above user/password, refresh if necessary)


# Keys

1) During normal operation
	 1) UP key: press once to stop the pause, twice to resume testing ESP-Miner devices
	 2) DOWN button: press several times to turn the display on and off
	 3) Together: Factory Reset (format)

2) While scanning IPs
	 1) Together: Reset the WIFI configuration

3) When the license has expired
	 1) Together: Factory Reset (format)

4) Side button: RESET

# Recommendations and use cases

AxeDoctor is indicated in the following use cases:
  1) All ESP-Minier devices are in the same subnet as the AxeDoctor
  2) All ESP-Miner devices are always turned on 24 hours a day:
  	2A) You can use the FIXED IP configuration if you know them;
 	    usually even if you turn off a device your router
  	    will always assign the same IP address if possible.
  	2B) You can use automatic IP configuration (RESCAN) every time
 	    It will take approximately 20 minutes for you to turn on your AxeDoctor
  	    to scan its entire subnetwork for
 	    ESP-Miner devices (example 192.168.0.X with X>1)
  	   In these cases you can also turn on your AxeDoctor in time slots
 	   so that an IP scan is performed again each time
  	2C) You can use automatic IP configuration only the first time (AUTO),
 	    a RESCAN will be performed only once whose result will be
  	    stored as fixed IPs
  3) All ESP-Miner devices turn on only in certain time slots
     of the day by means of smart switches (for example to take advantage of the
     your photovoltaic system):
  	3A) In these cases it is better to always use the configuration
  	    automatic IP selection (RESCAN) and your AxeDoctor will have to turn on
  	    together with your ESP-Miner devices. The scan function
            automatic IP address will take approximately 20 minutes to allow
            devices to start up regularly.


# License

Shareware


# Registration 

Work in progress

# Hardware

https://a.aliexpress.com/_Ew7XsML
https://a.aliexpress.com/_EJlkuTp

# Support

axedoctorb10@gmail.com

