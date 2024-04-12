# Raspberry Pi Workshop 2024

Welcome to the Raspberry Pi Workshop 2024 hosted by the Austin Peay Cybersecurity Club! This repository contains all the instructions and necessary documentation to set up a Pwnagotchi with a Raspberry Pi Zero.

# Notes

A good guide to follow: [https://github.com/Xyl0se/Pwnagotchi-new-guerilla-guide?tab=readme-ov-file](https://github.com/Xyl0se/Pwnagotchi-new-guerilla-guide?tab=readme-ov-file)

Some other important pages or places I used:
  1. [https://pwnagotchi.org/getting-started/index.html](https://pwnagotchi.org/getting-started/index.html)
  2. [https://pwnagotchi.ai/intro/](https://pwnagotchi.ai/intro/)
  3. [https://discord.gg/M6mWyyrqYm](https://discord.gg/M6mWyyrqYm)
  4. [https://docs.google.com/spreadsheets/d/1os8TRM3Pc9Tpkqzwu548QsDFHNXGuRBiRDYEsF3-w_A/edit?pli=1#gid=0](https://docs.google.com/spreadsheets/d/1os8TRM3Pc9Tpkqzwu548QsDFHNXGuRBiRDYEsF3-w_A/edit?pli=1#gid=0) 

## Some cool plugins to add:

[https://github.com/jayofelony/pwnagotchi-torch-plugins/tree/main](https://github.com/jayofelony/pwnagotchi-torch-plugins/tree/main)

[https://github.com/c-nagy/pwnagotchi-display-password-plugin](https://github.com/c-nagy/pwnagotchi-display-password-plugin) 

1. **Hcxtools**: a requirement if you want to be able to make use of the hashie.py plugin, which can convert .pcap-files to crackable hashes.
2. **OnlineHashCrack**: This plugin integrates with the OnlineHashCrack service, automatically sending new handshakes to the service for cracking. It's a handy tool for testing the security of your own Wi-Fi networks by checking the strength of your Wi-Fi passwords against a real-world attack scenario.
3. **GPS**: If you have a GPS module connected to your Pwnagotchi, the GPS plugin can log the geographical location of each Wi-Fi handshake you capture. This is great for creating maps of your Wi-Fi hunting adventures or for adding context to your handshakes.
4. **PwnMAIL**: Allows your Pwnagotchi to send you emails with updates about its status, including the number of new handshakes, system health, and other notifications. It's an excellent way for keeping informed about your device's activities, especially if you don't check it frequently.
