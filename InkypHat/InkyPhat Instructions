# Starting your Raspberry Pi

Once you flash the SD card reinsert it into the device and create a file named **`config.toml`** on the SD card. The SD should now be labeled as `boot` after flashing.

> On Windows 11, I had to use Visual Studio code to create this file. Windows 10 may be different.

Paste the `config.toml` file from the InkypHat file into the `config.toml` file that you just created.

Once saved, eject the SD card, insert it into the Raspberry Pi, and plug it into a computer using a Micro USB data cable.

Wait for the notification sound that a device has been inserted and wait in Device Manager for a USB Serial Device (Com[number]) under Ports.

Whenever the device detects the Pi, install RNDIS drivers from this link: [https://modclouddownloadprod.blob.core.windows.net/shared/mod-rndis-driver-windows.zip](https://modclouddownloadprod.blob.core.windows.net/shared/mod-rndis-driver-windows.zip)

Extract the file into a location you can access.

Go back into Device Manager, select the USB Serial Device under ports, and update drivers manually with the RNDIS drivers you downloaded.

Once that is done, go into Control Panel > Network and Internet > Network Connections. From there you should see an Ethernet, Enabled, RNDIS device.
Open the properties from that device and open the Internet Protocol Version 4 (IPv4).

Designate your Pi IP. Most people will designate the pi to 10.0.0.1. For this lab, we will provide you with an IP to connect to.

Set the default gateway to 255.255.255.0.

## Booting and setting up your InkypHat Raspberry Pi

Once you set up the network settings, navigate to Windows PowerShell.
In the PowerShell, SSH into the pi by typing `ssh pi@[LocalPiIp +1]`. For instance, to ssh into 10.0.0.1 you would type `ssh pi@10.0.0.2`.

The default password is **`raspberry`**.

Navigate to `inky.py` on this GitHub page and copy the file.

In the Windows PowerShell type the following command:

sudoedit /usr/local/lib/python3.9/dist-packages/pwnagotchi/ui/hw/inky.py

Replace the old `inky.py` file with the one provided by pasting it in. **Do not forget to remove the old inky.py information.**

Control + S will save your edits. Then hit Control + X to exit editing the file.

Reboot your pwnagotchi by typing:

sudo systemctl restart pwnagotchi

### Important commands to know

You edit many settings in the config. This includes enabling or disabling plugins. The Pwnagotchi image provided includes many plugins for your Pwnagotchi.

You can navigate to a Web GUI by going to `https://[PwnagotchiIP]:8080`

sudoedit /etc/pwnagotchi/config.toml

