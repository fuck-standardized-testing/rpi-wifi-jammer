# rpi-wifi-jammer
Build your own wifi-jammer with raspberry pi!

# Materials

- [ ] Raspberry Pi (any model of the 1, 2, or 3 should work), I used a 1.
- [ ] Ethernet (wired) connection for the Pi to use
- [ ] Cheap USB Wifi dongle. I used [this](http://www.canakit.com/raspberry-pi-wifi.html).

# Instructions

1. Install [Arch Linux for ARM](https://archlinuxarm.org/platforms) on an SD card
    
    Choose your Raspberry Pi model from the list and follow the provided instructions. I believe you will need a Linux or Mac computer to do this. **I promise this is the hardest step**. For following steps you will need to be SSHed into the Pi.
    
2. Install required packages
    
    TODO: Check if this is right

        sudo pacman -S git python2 scapy libpcap
        
3. Clone https://github.com/DanMcInerney/wifijammer from the home directory (/home/alarm)
    
        git clone https://github.com/DanMcInerney/wifijammer.git

4. Install systemd scripts

        git clone https://github.com/fuck-standardized-testing/rpi-wifi-jammer.git
        sudo cp rpi-wifi-jammer/jammer.service /etc/systemd/system/
        sudo cp rpi-wifi-jammer/jammer.timer /etc/systemd/system/
        sudo systemctl enable jammer.timer
        
By default, the timer is setup to wait exactly 90 minutes before activating the jammer. This was optimal given the testing schedule used by my school, but this can be changed by modifying this line in jammer.timer:

    OnBootSec=90min
