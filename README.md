# systeminfo

## Overview
`systeminfo` is a Bash script designed to provide a comprehensive overview of essential system information on Linux systems. This tool is particularly useful for system administrators and users who frequently connect to systems via SSH, as it presents all key information in a single, easy-to-read report. The script has been optimized for compatibility across a wide range of Linux distributions and is structured with modular functions for easy maintenance and customization.

## Features
The script reports the following system information:

* **DATE**: Current date and time.
* **CPU**: CPU model.
* **#CPU**: Number of CPU cores.
* **LA**: System load averages for the past 1, 5, and 15 minutes.
* **TEMP**: CPU temperature (if available).
* **MEM**: Memory usage, including total, free, cached, and available memory.
* **SWP**: Swap usage, including total and free swap space.
* **ARCH**: CPU architecture (machine hardware name).
* **KERN**: Kernel release.
* **OS**: LSB (Linux Standard Base) and distribution-specific information.
* **HOST**: System's host name.
* **UP**: Uptime of the system, showing how long the system has been running.
* **DF**: Disk space usage on mounted filesystems.
* **NET**: Network interfaces and their IP addresses.
* **WHO**: Users currently logged on to the system.

## Example
```
  DATE | Thu Jan 12 21:17:34 EET 2017

  CPU  | ARMv7 Processor rev 4 (v7l) 
  #CPU | 4 
  LA   | 0.50  0.30  0.10  

  TEMP | cpu    44.5'C 

  MEM  | tot     925.5M | free     691.6M | cache     175.3M | avail     843.1M 
  SWP  | tot      99.9M | free      99.9M 

  ARCH | armv7l 
  KERN | 4.4.38-v7+ 
  OS   | Raspbian GNU/Linux 8.0 (jessie) 
  HOST | raspberrypi 

  UP   | 2 days, 3 hours, 58 minutes, 52 seconds 

  DF   | /dev/root      7364M 1020M 6016M 13.9 [##.........] /          
  DF   | /dev/mmcblk0p1   63M   21M   42M 33.1 [####.......] /boot      

  NET  | eth0     192.168.120.111 
  NET  | lo       127.0.0.1 
  NET  | wlan0     

  WHO  | rt       pts/0        2017-01-12 20:36 (192.168.120.100) 
```

## Installation

Follow these steps to install and set up `systeminfo` on your system.

### Prerequisites

Depending on your Linux distribution, you may need to install certain packages to ensure full functionality of `systeminfo`.

#### Debian/Ubuntu

> Install `bc`, a required package for some calculations:
```bash
sudo apt-get install bc
```

> For displaying the CPU temperature, install `lm-sensors`:
```bash
sudo apt-get install lm-sensors
```

#### Raspbian

> For Raspbian users, add your user to the **audio** and **video** groups to enable temperature readings:
```bash
sudo adduser <user> audio && sudo adduser <user> video 
```
Replace <user> with your actual username.

### Installing systeminfo

Copy the Script to `/bin`: This makes the script globally accessible as a command.

You can either copy a local version of `systeminfo`:
```bash
sudo cp ./systeminfo /bin/systeminfo
```
or download it directly from the repository:
```bash
sudo wget -O /bin/systeminfo https://raw.githubusercontent.com/kutsy/systeminfo/master/systeminfo
```

Make the Script Executable:
```bash
sudo chmod +x /bin/systeminfo
```

### Auto-run on Login
To have `systeminfo` automatically display information upon login:

Append the script execution command to the end of your `~/.profile` file:
```bash
echo "/bin/systeminfo" >> ~/.profile
```

Now, `systeminfo` should run each time you log in, providing a quick overview of your system's status.


## Customization
The script is designed with modularity in mind, making it easy to customize or extend. Each section of the script (e.g., CPU information, memory usage) is encapsulated in a function. You can modify these functions or add new ones to extend the script's capabilities as per your requirements.

## Compatibility
`systeminfo` is compatible with most Linux distributions. It has been tested on popular distributions like Ubuntu, CentOS, Fedora, and Debian. The script gracefully handles variations in system commands and utilities across these distributions.

## Contributions
Contributions to `systeminfo` are welcome. 
You can contribute by:

* Reporting issues.
* Suggesting new features or enhancements.
* Submitting pull requests with bug fixes or new functionalities.

## License
`systeminfo` is open-source software, available under the MIT License.
