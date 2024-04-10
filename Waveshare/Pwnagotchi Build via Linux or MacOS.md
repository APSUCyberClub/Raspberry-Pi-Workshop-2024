# How to Build a Pwnagotchi via Image
This is if you are using a Linux or MacOS machine, if you're not, **GET OUT!** cheers!

## Step 1: Download the Image

1. Visit the specific GitHub releases page: [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9).
2. Download the latest image for Pwnagotchi v2.8.9.

## Step 2: Flash the microSD Card

1. Use a tool like Balena Etcher or Raspberry Pi Imager to flash the downloaded image onto a microSD card.
   - For Pi Imager head here: https://www.raspberrypi.com/software/
   - For Balena etcher install here: https://etcher.balena.io/#download-etcher 
3. Insert the microSD card into your computer, open the imaging tool, select the downloaded image, select the target microSD card, and start the flashing process.
4. Once the flashing is complete, eject the microSD card safely.

## Step 3: Initial Configuration

1. Before inserting the microSD card into your Raspberry Pi, mount it again on your computer.
2. Navigate to the "boot" partition of the card.
    - Open a terminal and enter: `cd /Volumes/boot` [in my case it was bootfs]
3. Enable SSH:
    - Create an empty ssh file by entering: `touch ssh`
    - Keep the SD plugged in
4. Create a file named `wpa_supplicant.conf` to configure your WiFi settings:
    - Enter: `nano wpa_supplicant.conf`
    - Copy & paste the supplied `wpa_supplicant.txt` file
5. Eject the SD card safely.

## Step 4: Boot Up and SSH

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
3. By default, Pwnagotchi creates a network interface for SSH. You can SSH into your Pi using its IP address (which can be found on your router's admin page) and the default credentials (“pi” as the username and “raspberry” as the password) over your network.
    - Connect to the pi via: `ssh -4 [accountname]@[devicename]` [change to what the name is] my case is `pi@10.0.0.2`.
    - Enter the password. It should be `raspberry`
    - Enter `yes` and click enter.
    - Change your password so enter: `passwd`
    - Enter new password & re-enter it
    - NOTE IF ERROR: `mv ~/.ssh/known_hosts ~/.ssh/known_hosts.backup`

## Step 5: Set up the config.toml file

1. Enter the command: `sudo touch /etc/pwnagotchi/config.toml`
2. Enter the command: `sudo nano /etc/pwnagotchi/config.toml`
3. Copy and paste the supplied `config.toml` file 
    - Note if using waveshare: 
        - `ui.display.enabled = true`
        - `ui.display.type = "waveshare_4"`
    - Note: if you want to change color.
        - `ui.display.color = "black"`
        - `ui.display.color = "auto"`
        - `ui.display.color = "white"`
4. Make directory `/etc/pwnagotchi/custom-plugins` for custom plugins to add to that directory later.
    - Enter the command: `sudo touch /etc/pwnagotchi/custom-plugins`
    - Enter the command if you want to edit or add plugins: `sudo nano /etc/pwnagotchi/custom-plugins`
5. Enter the command: `sudo reboot now`
6. SSH back into it to change/adjust anything

## Step 6: Setting up PiSugar Battery

1. Go to the home directory
    - `cd ~`
2. Install PiSugar Power Manager 
    - `curl http://cdn.pisugar.com/release/Pisugar-power-manager.sh | sudo bash`
3. Download the plugin and support library
    - `git clone https://github.com/PiSugar/pisugar2
