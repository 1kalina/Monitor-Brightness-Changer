# Monitor-brightness-changer
After transitioning to Linux, I encountered difficulties with adjusting brightness on my dual-monitor setup using existing solutions. This script is a straightforward tool designed to manage monitor brightness effortlessly, using `ddcutil`. It's tailored for personal use but might be helpful for others facing similar challenges

## Running
Open new Terminal window and run `brightness`.

For version with flags run `brightness -b BRIGHTNESS`

```
└─[$] python brightness-with-flags.py -h
usage: brightness-with-flags.py [-h] -b BRIGHTNESS [-m MONITOR]

Set monitor brightness using ddcutil.

options:
  -h, --help            show this help message and exit
  -b, --brightness BRIGHTNESS
                        Brightness level (0-100)
  -m, --monitor MONITOR
                        Monitor ID (optional, applies to all if not specified)

```


## Installation

### Pre-Install Step
Proof Python installation
`python3 --version`

if no: `sudo <package manager> install Python3.12.3`

Check
`python3 --version`

### Step 1
`sudo <package manager> install ddcutil`

### Step 2
- Download choosen file `brightness` or `brightness-with-flags` from the repository

- Rename to `brightness`

- Open download directory in terminal \
`cd /home/<username>/Downloads`

### Step 3
- Make the file executable \
`chmod +x brightness`

- Move to directory which is part of PATH \
`sudo mv brightness /usr/local/bin/`

- Verifying PATH `echo $PATH`

if no `/usr/local/bin/` in $PATH: \
`export PATH=$PATH:/usr/local/bin && source ~/.bashrc`




## Building `ddcutil` from Source
Skip Step 1
### Install Build Tools and Dependencies
Debian based: \
`sudo apt install build-essential libusb-1.0-0-dev libdrm-dev pkg-config i2c-tools`

Fedora based: \
`sudo dnf install make gcc libusb1-devel libdrm-devel pkgconfig i2c-tools`

Arch: \
`sudo pacman -S base-devel libusb libdrm i2c-tools`

### Clone the `ddcutil` repository
`git clone https://github.com/rockowitz/ddcutil.git` \
`cd ddcutil`

### Configure and Build
`./configure` \
`make` \
`sudo make install`

### Verify installation
`ddcutil --version`

### Post-Installation Setup
Load Kernel Modules: \
`sudo modprobe i2c-dev` \
`sudo modprobe drm`

Ensure I2C Access \
`ls /dev/i2c-*` \
`sudo chmod a+rw /dev/i2c-*`

### Test
`sudo ddcutil detect`

Return to Step 2
