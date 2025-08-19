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

------------------------------------------------------------------------

## 🔌 Step 2: Connect Raspberry Pi to Laptop

1.  Insert the flashed MicroSD into the Pi.\
2.  Connect Pi to your laptop using an **Ethernet cable**.\
3.  Power the Pi with its USB adapter.\
4.  Your laptop shares internet with the Pi through Ethernet.

------------------------------------------------------------------------

## 🌐 Step 3: Find Raspberry Pi on Network

On Windows PowerShell:

``` powershell
ping raspberrypi.local
```

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
