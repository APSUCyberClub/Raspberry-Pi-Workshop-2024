# Software Instructions for Pi Workshop

This file is for projects using the displays or installing Kali Linux on your Pi0

## Installing Images onto MicroSD

For Pi Imager, head here: [https://www.raspberrypi.com/software/](https://www.raspberrypi.com/software/)
1. Install to your machine.
2. Open it up.
3. Choose Device: In this case, choose Raspberry Pi Zero. If using a different model, adjust accordingly.
4. Operating System:
   - Kali: Other specific-purpose OS > Kali Linux > Raspberry Pi Zero W
   - Fun pHAT displays & Waveshare: Raspberry Pi OS (Legacy, 32-bit)
   - Pwnagotchi: Image from [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9)
5. Click next & configure the settings to what you prefer.

For Balena Etcher, install here: [https://etcher.balena.io/#download-etcher](https://etcher.balena.io/#download-etcher)
1. Install to your machine.
2. Open it up.
3. Flash from File:
   - Pwnagotchi: Image from [https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9](https://github.com/jayofelony/pwnagotchi/releases/tag/v2.8.9)
4. Select the microSD.
5. Flash!

## Configuring pHAT display

Instructions: [https://learn.pimoroni.com/article/getting-started-with-inky-phat](https://learn.pimoroni.com/article/getting-started-with-inky-phat)

1. Open a terminal and enter: `curl https://get.pimoroni.com/inky | bash`
2. Enter: `cd /home/pi/Pimoroni/inky/examples` or navigate to the pimoroni > inky > examples.
3. Name badge example: `python3 name-badge.py --type "phat" --colour "black" --name "insert name"`
4. If receiving the error: “failed to detect an inky board,” visit [https://forums.pimoroni.com/t/brand-new-inky-phat-yellow-not-working/15317/5](https://forums.pimoroni.com/t/brand-new-inky-phat-yellow-not-working/15317/5)
   a. Run the command `sudo raspi-config`
   b. Select “3. Interface Options”
   c. Select “I4 SPI” / “I5 I2C” and set to enabled; Finish
   d. Run step 3 again.

## Configuring Waveshare Display

Instructions: [https://www.waveshare.com/wiki/Libraries_Installation_for_RPi](https://www.waveshare.com/wiki/Libraries_Installation_for_RPi)

1. Open a terminal and enter: `sudo raspi-config`
2. Choose Interfacing Options -> SPI -> Yes to enable SPI interface.
3. Enter the command: `sudo reboot`
4. Install lg library: open the Raspberry Pi terminal and run the following commands:
   a. `wget https://github.com/joan2937/lg/archive/master.zip`
   b. `unzip master.zip`
   c. `cd lg-master`
   d. `make`
   e. `sudo make install`
5. Install BCM2835: open the Raspberry Pi terminal and run the following command:
   a. `wget http://www.airspayce.com/mikem/bcm2835/bcm2835-1.71.tar.gz`
   b. `tar zxvf bcm2835-1.71.tar.gz`
   c. `cd bcm2835-1.71/`
   d. `sudo ./configure && sudo make && sudo make check && sudo make install`
6. Demo install
   a. `git clone https://github.com/waveshare/e-Paper.git`
   b. `cd e-Paper/RaspberryPi_JetsonNano/`
7. Download the demo
   a. `wget https://files.waveshare.com/upload/7/71/E-Paper_code.zip`
   b. `unzip E-Paper_code.zip -d e-Paper`
   c. `cd e-Paper/RaspberryPi_JetsonNano/`
8. Compile the demo:
   a. `cd c`
   b. `sudo make clean`
   c. `sudo make -j4 EPD=epd2in13V3`
9. Run the demo:
   a. `sudo ./epd`

## KALI LINUX IN TTY MODE

- [YouTube Video Tutorial](https://youtu.be/N9lEDIg3CWA)
- [Enable WiFi on Kali Linux](https://operavps.com/docs/enable-wifi-on-kali-linux/)
- [How to enable the GUI in Kali Linux](https://www.quora.com/How-do-I-enable-the-GUI-in-Kali-Linux)

