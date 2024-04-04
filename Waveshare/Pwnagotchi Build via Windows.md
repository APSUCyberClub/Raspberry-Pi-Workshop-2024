# How to Build a Pwnagotchi via Image
This is if you are using a windows machine, if you're not, **GET OUT!** cheers!

## Step 1: Download the Image

1. Visit the specific GitHub releases page: [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9).
2. Download the latest image for Pwnagotchi v2.8.9.

## Step 2: Flash the microSD Card

1. Use a tool like Balena Etcher or Raspberry Pi Imager to flash the downloaded image onto a microSD card.
   - For Pi Imager head here: https://www.raspberrypi.com/software/
   - For Balena etcher install here: https://etcher.balena.io/#download-etcher 
2. Insert the microSD card into your computer, open the imaging tool, select the downloaded image, select the target microSD card, and start the flashing process.
3. Once the flashing is complete, eject the microSD card safely.

## Step 3: Initial Configuration

1. Before inserting the microSD card into your Raspberry Pi, insert it back into your computer.
2. Open File Explorer and navigate to the "boot" partition of the card. 
   - You should see this as a new drive under "This PC" in File Explorer.
3. Enable SSH:
   - Right-click within the boot partition in File Explorer and select "New > Text Document". Rename this new document to `ssh` with no extension. If you're warned about changing the file extension, click "Yes".
   - Make sure you have enabled viewing of file extensions in File Explorer to do this.
4. Create a file named `wpa_supplicant.conf` to configure your WiFi settings:
   - Right-click in the same boot partition and choose "New > Text Document". Open this new document, then rename it to `wpa_supplicant.conf`.
   - Open `wpa_supplicant.conf` with Notepad. Copy and paste the contents of the supplied `wpa_supplicant.txt` file into this document.
5. Safely eject the SD card by right-clicking on its drive in File Explorer and selecting "Eject".

## Step 4: Boot Up and SSH

1. Insert the microSD card into your Raspberry Pi and power it up.
2. Wait a few minutes for the initial boot process to complete.
   - To ping the device, open Command Prompt and enter: `ping [device name]`. Replace `[device name]` with the actual name of your device, e.g., `pi@raspberrypi`.
3. To SSH into your Pi, you'll need an SSH client. Windows 10 and later include one natively; otherwise, download and use PuTTY.
   - Open PowerShell or Command Prompt and type: `ssh pi@[device IP address]`. Replace `[device IP address]` with your Raspberry Pi's IP address. You can find this address from your router's admin page.
   - When prompted, type `yes` to continue connecting.
   - Enter the default password (`raspberry`), then press Enter.
   - It's recommended to change your default password immediately. After logging in, type `passwd` and follow the prompts to enter and confirm your new password.
   - If you encounter an error regarding known hosts, navigate to the `.ssh` directory in your user folder (`C:\Users\[YourUserName]\.ssh\`) and rename the `known_hosts` file to `known_hosts.backup`. This step might require enabling hidden files and folders in File Explorer.

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
    - Enter the command: `sudo touch etc/pwnagotchi/custom-plugins`
    - Enter the command: `sudo nano /etc/pwnagotchi/custom-plugins`
5. Enter the command: `sudo reboot now`
6. SSH back into it to change/adjust anything

## Step 6: Setting up PiSugar Battery

1. Go to the home directory
    - `cd ~`
2. Install PiSugar Power Manager 
    - `curl http://cdn.pisugar.com/release/Pisugar-power-manager.sh | sudo bash`
3. Download the plugin and support library
    - `git clone https://github.com/PiSugar/pisugar2
