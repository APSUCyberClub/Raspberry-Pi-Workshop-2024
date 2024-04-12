# How to Set Up a Pwnagotchi with a Waveshare Display on Windows

## Step 1: Flashing the SD Card
1. Visit the Pwnagotchi release page at [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9) and download the latest Pwnagotchi image.
2. Utilize Balena Etcher or Raspberry Pi Imager to write the image to your microSD card.
3. After the image is successfully written, remove and then reinsert the microSD card into your computer. It should appear as a drive labeled `boot`.

## Step 2: Configuring the Boot Partition
1. In the `boot` partition of your microSD card, create a new file named `config.toml` using a text editor like Notepad++ or Visual Studio Code.
2. Transfer the configuration settings from the provided `config.toml` file into the new file on your SD card. Make sure to customize the settings according to your network and display preferences.
3. Eject the microSD card safely from your computer.

## Step 3: Setting Up the Raspberry Pi
1. Insert the prepared microSD card into your Raspberry Pi.
2. Connect the Raspberry Pi to your computer using a Micro USB data cable.
3. Await the notification sound from Windows indicating a new device connection. Then, in Device Manager, look for a "USB Serial Device (Com[number])" under Ports to confirm the connection.

## Step 4: Installing RNDIS Drivers
1. Download the RNDIS drivers from [https://modclouddownloadprod.blob.core.windows.net/shared/mod-rndis-driver-windows.zip](https://modclouddownloadprod.blob.core.windows.net/shared/mod-rndis-driver-windows.zip) and extract the files.
2. In Device Manager, right-click the detected USB Serial Device and manually update the driver using the extracted RNDIS drivers.

## Step 5: Configuring Network Settings
1. Navigate to Control Panel > Network and Internet > Network Connections.
2. Identify and select the Ethernet or RNDIS device, then open its properties.
3. Choose Internet Protocol Version 4 (IPv4) and assign the IP address as specified (e.g., 10.0.0.1) with the subnet mask set to 255.255.255.0.

## Step 6: Establishing an SSH Connection
1. Launch Windows PowerShell.
2. Execute the SSH command: `ssh pi@[AssignedPiIp +1]` (if your IP is 10.0.0.1, use `ssh pi@10.0.0.2`). The default password is `raspberry`.

## Step 7: Updating the Display Configuration for Waveshare
1. Access the Pwnagotchi device via SSH as described in Step 6.
2. Navigate to the `config.toml` file by typing: `sudo nano /etc/pwnagotchi/config.toml`.
3. Modify the display settings to use a Waveshare display. For instance:
   ```
   ui.display.enabled = true
   ui.display.type = "waveshare_2"
   ui.display.color = "black"  # You can change this to "white" or "auto" if your model supports it.
   ```
4. Save your changes and exit the editor.

## Step 8: Final Configurations and Reboot
1. Apply any additional configurations to the `config.toml` file as needed, including network settings, plugin configurations, and display preferences.
2. Reboot your Pwnagotchi to apply the changes: `sudo systemctl restart pwnagotchi`.
3. After rebooting, you can access the Web GUI by navigating to `https://[PwnagotchiIP]:8080` using the login credentials you set up in the `config.toml` file.

## Additional Steps: Custom Plugins and PiSugar Battery (Optional)
- For users intending to use custom plugins or a PiSugar battery with their Pwnagotchi, refer to the detailed instructions provided in your macOS guide, adapting them as necessary for your Windows environment.
