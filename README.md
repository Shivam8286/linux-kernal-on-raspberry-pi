# linux-kernal-on-raspberry-pi
# 🚀 Raspberry Pi 3B Setup & Running Linux (Full Guide)

This README explains step-by-step how we set up and connected to a
**Raspberry Pi 3B**, installed Raspberry Pi OS, and accessed the Linux
kernel using only a laptop and Ethernet connection.

------------------------------------------------------------------------

## 📦 Materials Required

-   Raspberry Pi 3B board\
-   MicroSD card (16GB or more recommended)\
-   Laptop/PC (Windows used here)\
-   Ethernet cable (to connect Pi directly to laptop)\
-   USB power supply for Pi\
-   (Optional) Wi-Fi network for later use

------------------------------------------------------------------------

## 🖥️ Step 1: Flash Raspberry Pi OS to SD Card

1.  Download and install **Raspberry Pi Imager** from
    [raspberrypi.com/software](https://www.raspberrypi.com/software/).\
2.  Insert the MicroSD card into your laptop (via card reader).\
3.  Open Raspberry Pi Imager:
    -   **Choose OS → Raspberry Pi OS (Lite, 64-bit)** (no desktop,
        minimal).\
    -   **Choose Storage → your SD card.**\
    -   Under ⚙️ (settings), enable:
        -   **Set hostname** → `raspberrypi`
        -   **Enable SSH** (use password authentication)
        -   **Set username/password** (example:
            `shiva / your_password`)\
        -   (Optional) configure Wi-Fi if you want wireless.\
    -   Click **Write**.\
4.  Safely eject the SD card and insert it into the Raspberry Pi.
5.  click "ctrl +shift +x" to open these advance settings to configure and also enable ssh in services.
   <img width="700" height="475" alt="Image" src="https://github.com/user-attachments/assets/1c3f652b-e696-4859-9457-340927ed040a" />
   <img width="589" height="416" alt="Image" src="https://github.com/user-attachments/assets/a47dbab7-0858-4dbe-b9d3-07b61257435e" />

------------------------------------------------------------------------

## 🔌 Step 2: Connect Raspberry Pi to Laptop

1.  Insert the flashed MicroSD into the Pi.\
2.  Connect Pi to your laptop using an **Ethernet cable**.\
3.  Power the Pi with its USB adapter.\
4.  Your laptop shares internet with the Pi through Ethernet.
5.  go to network connections -> wifi -> right click -> sharing tab -> Allow other network users to connect… enable it.
   this will allow your pi to access and connect to your laptop using the network... 

------------------------------------------------------------------------

## 🌐 Step 3: Find Raspberry Pi on Network

On Windows PowerShell:

``` powershell
ping raspberrypi.local
```
<img width="1308" height="446" alt="Image" src="https://github.com/user-attachments/assets/bd8fd7c2-f205-481b-9fbc-5b0e3ccae5ba" />

If it replies → the Pi is alive.

If not, list connected devices:

``` powershell
arp -a
```

Look for an IP like `192.168.x.x` or `169.254.x.x`.

------------------------------------------------------------------------

## 🔑 Step 4: SSH into Raspberry Pi

Connect using the hostname:

``` powershell
ssh shiva@raspberrypi.local
```

If `.local` doesn't resolve, use the IP directly:

``` powershell
ssh shiva@192.168.x.x
```

👉 First time, you'll get a warning about authenticity. Type `yes` to
continue.\
👉 Enter your password (set in Imager).

Now you're inside your Pi's **Linux terminal** 🎉

------------------------------------------------------------------------

## 🛠️ Step 5: Initial Setup Inside Raspberry Pi

Run updates:

``` bash
sudo apt update
sudo apt upgrade -y
```

Check the Linux kernel version:

``` bash
uname -a
```

Output looks like:

    Linux raspberrypi 6.1.0-rpi7-rpi-v8 #1 SMP ...

------------------------------------------------------------------------

## 📂 Step 6: Basic Linux Commands

Some commands to try:

``` bash
whoami        # current user
hostname      # device name
uptime        # how long it's running
ls            # list files
pwd           # show current directory
free -h       # memory usage
df -h         # disk usage
```

------------------------------------------------------------------------

## 📡 Step 7: (Optional) Connect to Wi-Fi

``` bash
sudo raspi-config
```

-   Go to **System Options → Wireless LAN**\
-   <img width="929" height="652" alt="Image" src="https://github.com/user-attachments/assets/c4bdafa8-5f96-478f-9a42-e9f95ef0c622" />


-   Enter Wi-Fi SSID and password\

-   Reboot:

    ``` bash
    sudo reboot
    ```

------------------------------------------------------------------------

## 🔌 Step 8: Shutdown & Reboot Safely

Always use commands, never unplug directly:

``` bash
sudo reboot        # restart
sudo shutdown now  # power off
```

<img width="934" height="538" alt="Image" src="https://github.com/user-attachments/assets/a8ec262a-076c-440a-834a-8b44aa8027bb" />
<img width="944" height="656" alt="Image" src="https://github.com/user-attachments/assets/40a4eaba-a07c-4b14-84ad-64621afd6053" />

------------------------------------------------------------------------

## ✅ Final Notes

-   Raspberry Pi OS is a Linux distribution, so by default you're
    already **running Linux kernel** on your Pi.\
-   You can install software, write Python code, or even turn it into a
    small server.\
-   SSH lets you control the Pi from your laptop without needing a
    monitor/keyboard.

------------------------------------------------------------------------

👉 This README can serve as your **step-by-step reference** and as a
**presentation document** for introducing Raspberry Pi to friends.
share and learn togethar

