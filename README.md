# Monitor-Brightness-Changer
After transitioning to Linux, I encountered difficulties adjusting the brightness on my dual-monitor setup using existing solutions. This script is a straightforward tool designed to manage monitor brightness effortlessly using `ddcutil`. While tailored for personal use, it might also be helpful for others facing similar challenges.

## Installation

### Pre-Install Step
Verify Python installation:  
`python3 --version`  

If Python is not installed:  
`sudo <package manager> install python3.12.3`  

Verify the installation:  
`python3 --version`  

### Step 1
Install `ddcutil`:  
`sudo <package manager> install ddcutil`  

### Step 2
- Download the `brightness` file from the repository.  
- Open the download directory in the terminal:  
  `cd /home/<username>/Downloads`  

### Step 3
- Make the file executable:  
  `chmod +x brightness`  
- Move it to a directory included in `PATH`:  
  `sudo mv brightness /usr/local/bin/`  
- Verify `PATH`:  
  `echo $PATH`  

If `/usr/local/bin/` is not in `$PATH`:  
`export PATH=$PATH:/usr/local/bin`  
`source ~/.bashrc`  

### Run
Open a new terminal window and run `brightness`.  

---

### Building `ddcutil` from Source
Skip Step 1.  

#### Install Build Tools and Dependencies
For Debian-based systems:  
`sudo apt install build-essential libusb-1.0-0-dev libdrm-dev pkg-config i2c-tools`  

For Fedora-based systems:  
`sudo dnf install make gcc libusb1-devel libdrm-devel pkgconfig i2c-tools`  

For Arch-based systems:  
`sudo pacman -S base-devel libusb libdrm i2c-tools`  

#### Clone the `ddcutil` Repository
`git clone https://github.com/rockowitz/ddcutil.git`  
`cd ddcutil`  

#### Configure and Build
`./configure`  
`make`  
`sudo make install`  

#### Verify Installation
`ddcutil --version`  

#### Post-Installation Setup
Load kernel modules:  
`sudo modprobe i2c-dev`  
`sudo modprobe drm`  

Ensure I2C access:  
`ls /dev/i2c-*`  
`sudo chmod a+rw /dev/i2c-*`  

#### Test
`sudo ddcutil detect`  

Return to Step 2.  
