# How to Set Up a Pwnagotchi with an InkyPhat Display on Linux/macOS

## Step 1: Downloading the Pwnagotchi Image
1. Navigate to the Pwnagotchi releases page at [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9) and download the latest version of the Pwnagotchi image suitable for your device.

## Step 2: Flashing the microSD Card
1. Utilize a tool like Balena Etcher or the command line `dd` utility on Linux/macOS to flash the downloaded image onto a microSD card.
2. Once the flashing process is complete, re-insert the microSD card into your computer to mount the `boot` partition.

## Step 3: Configuring the Boot Partition
1. Before inserting the microSD card into your Raspberry Pi, mount it again on your computer.
2. Navigate to the "boot" partition of the card.
   - Open a terminal and enter: `cd /Volumes/boot` (in my case it was bootfs)
      - Enable SSH:
        - Create an empty ssh file by entering: `touch ssh`
        - Keep the SD plugged in
3. Create a file named `wpa_supplicant.conf` to configure your WiFi settings:
   - Enter: `nano wpa_supplicant.conf`
   -  Copy & paste the supplied `wpa_supplicant.txt` file
4. Create a new file named `config.toml` in the `boot` partition and insert the necessary configuration for your Pwnagotchi, including network settings and preferences for plugins. Specifically for the InkyPhat display, ensure you have the following lines:
   ```
   ui.display.enabled = true
   ui.display.type = "inky"
   ```
5. Safely eject the microSD card from your computer.

## Step 4: Initial Raspberry Pi Setup
1. Insert the microSD card into your Raspberry Pi and power it up.
2. Wait for a few minutes for the initial boot process to complete.
   - Ping the device: `ping [device name]` in my case it is `pi@raspberry`
   - Go to network settings and select RNDIS/Ethernet gadget
      - Select the interface you noted from Step 2 in the list on the left.
      - Click the "Advanced" button, then go to the TCP/IP tab.
      - Set "Configure IPv4" to "Manually".
      - Enter the IP address 10.0.0.1, subnet mask 255.255.255.0, router to 10.0.0.1, and if needed, DNS server 9.9.9.9.
      - Make sure to change the service order so WIFI is above the pwnagotchi.
      - Click "OK", then "Apply" to save your changes.
      - Verify it by: `ping pi@10.0.0.2`
3. Download the script from: https://github.com/evilsocket/pwnagotchi/blob/master/scripts/macos_connection_share.sh
      -	Cd to the where it’s downloaded.
      -	Run `chmod +x macos_connection_share.sh` to make it executable
      -	Run the script: ` sudo ./macos_connection_share.sh en0 10.0.0.1`
      -	Enter your password

## Step 5: SSH into the Pwnagotchi
1. By default, Pwnagotchi creates a network interface for SSH. You can SSH into your Pi using its IP address (which can be found on your router's admin page) and the default credentials (“pi” as the username and “raspberry” as the password) over your network.
   - Connect to the pi via: `ssh -4 [accountname]@[devicename]` (change to what the name is) my case is `pi@10.0.0.2`.
   - Enter the password. It should be raspberry
   - Enter yes and click enter.
   - Change your password so enter: `passwd`
   - Enter new password & re-enter it
   - NOTE IF ERROR: `mv ~/.ssh/known_hosts ~/.ssh/known_hosts.backup`
   - NOTE: logging in from now on, you will ssh `pi@[whatevername you have in config]`
  
## Step 7: Configuring the InkyPhat Display & pwnagotchi config file
1. After successfully logging in, you'll need to ensure the InkyPhat display is correctly set up in the `config.toml` located in `/etc/pwnagotchi/`. You can edit this file using `nano` or your preferred text editor:
   ```
   sudo nano /etc/pwnagotchi/config.toml
   ```
2. Make sure the configuration reflects the use of an InkyPhat display as shown in Step 3.
3. Change the login to the web UI
   - `ui.web.username = "my_new_username"`
   - `ui.web.password = "my_new_password"`
   - Once you save and exit head to `http://10.0.0.2:8080/` and use that login you just changed
3. Make directory `/etc/pwnagotchi/custom-plugins` for custom plugins to add to that directory 

## Step 7: Final Adjustments and Reboot
1. Complete any additional configurations required for your Pwnagotchi, including setting up any plugins or network settings.
2. Reboot your Pwnagotchi to apply the changes with `sudo reboot`.
3. After rebooting, you can connect to your Pwnagotchi's web interface, typically accessible through the device's IP address on port 8080 (e.g., `http://[PwnagotchiIP]:8080`).

## Step 8: Setting up PiSugar Battery
If using Pisugar2 go here: [https://github.com/PiSugar/PiSugar/wiki/PiSugar2#](https://github.com/PiSugar/PiSugar/wiki/PiSugar2#) 
1. Go to the home directory
   - `cd ~`
2. Install PiSugar Power Manager
   - `curl http://cdn.pisugar.com/release/Pisugar-power-manager.sh | sudo bash`
3. Download the plugin and support library
   - `git clone https://github.com/PiSugar/pisugar2py.git`
   - `git clone https://github.com/PiSugar/pwnagotchi-pisugar2-plugin.git`
4. This installs the pisugar2 package into your python library
   - `sudo ln -s ~/pisugar2py/ /usr/local/lib/python3.7/dist-packages/pisugar2`
5. Installs the user-plugin
   - `sudo ln -s ~/pwnagotchi-pisugar2-plugin/pisugar2.py /etc/pwnagotchi/custom-plugins/pisugar2.py`
