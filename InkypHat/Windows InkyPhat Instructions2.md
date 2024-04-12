# How to Set Up a Pwnagotchi on Windows

## Step 1: Flashing the SD Card
1. Download the Pwnagotchi image from the release page: [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9).
2. Use Balena Etcher or Raspberry Pi Imager to write the image to your microSD card.
3. Once the image is written, remove and reinsert the microSD card into your computer. The SD card should be labeled as `boot`.

## Step 2: Preparing the Config File
1. On the `boot` partition of your microSD card, create a new file named `config.toml`.
   - You might need to use a text editor like Visual Studio Code to create this file on Windows.
2. Copy the contents of the `config.toml` file from the InkypHat file and paste it into the new `config.toml` file on your SD card.
3. Safely eject the microSD card from your computer.

## Step 3: Initial Raspberry Pi Setup
1. Insert the microSD card into your Raspberry Pi.
2. Connect the Raspberry Pi to your computer using a Micro USB data cable.
3. Wait for Windows to play the notification sound indicating a new device has been connected.
4. In the Device Manager, wait for a "USB Serial Device (Com[number])" to appear under Ports.

## Step 4: Installing RNDIS Drivers
1. When the device is detected, download and install RNDIS drivers from this link: [https://modclouddownloadprod.blob.core.windows.net/shared/mod-rndis-driver-windows.zip](https://modclouddownloadprod.blob.core.windows.net/shared/mod-rndis-driver-windows.zip).
2. Extract the downloaded file to a known location.
3. Back in the Device Manager, right-click the USB Serial Device under ports and update the driver manually with the RNDIS drivers you just downloaded.

## Step 5: Configuring Network Settings
1. Go to Control Panel > Network and Internet > Network Connections.
2. Locate the Ethernet, Enabled, RNDIS device.
3. Open its properties and select Internet Protocol Version 4 (IPv4).
4. Set the IP address as provided (e.g., 10.0.0.1) and the default gateway to 255.255.255.0.

## Step 6: Connecting via SSH
1. Open Windows PowerShell.
2. SSH into the Pi by typing `ssh pi@[AssignedPiIp +1]`. For example, for IP 10.0.0.1, type `ssh pi@10.0.0.2`.
3. The default password is `raspberry`.

## Step 7: Updating InkypHat Display File
1. Navigate to the `inky.py` file on the mentioned GitHub page and copy its contents.
2. In PowerShell, type: `sudoedit /usr/local/lib/python3.9/dist-packages/pwnagotchi/ui/hw/inky.py` to edit the inky.py file.
3. Replace the content with the copied `inky.py` file content, save, and exit.

## Step 8: Reboot and Additional Configurations
1. To reboot your Pwnagotchi, type: `sudo systemctl restart pwnagotchi`.
2. Edit other settings in the `config.toml` as needed to enable or disable plugins.
3. Access the Web GUI by navigating to `https://[PwnagotchiIP]:8080`.
