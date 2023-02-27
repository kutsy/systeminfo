# systeminfo

Prints system information in one report-screen.
It would be very useful to display at login via SSH

Reports:
-------------
* **DATE**: Current date and time
* **CPU**: CPU model
* **#CPU**: CPU cores count
* **LA**: System load averages for the past 1, 5, and 15 minutes
* **TEMP**: CPU temterature
* **MEM**: Memory usage: total, free, cache, available
* **SWP**: Swap usage: total, free
* **ARCH**: CPU architecture (machine hardware name)
* **KERN**: Kernel release
* **OS**: LSB (Linux Standard Base) and distribution-specific information
* **HOST**: System's host name
* **UP**: How long the system has been running
* **DF**: Displays the amount of disk space available on the mounted filesystems
* **NET**: Displays all interfaces which are currently available and IP addresses
* **WHO**: Displays users who is logged on

Example:
-------------
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

Installation:
-------------
Install required packages (Debian/Ubuntu):
```bash
sudo apt-get install bc
```
> For displaying temperature for Debian/Ubuntu also you need to install package **lm-sensors**:
```bash
sudo apt-get install lm-sensors
```
> For Raspbian you need to add your user to groups **audio** and **video**
```bash
sudo adduser <user> audio && sudo adduser <user> video 
```

Copy main file **systeminfo** to **/bin** folder
```bash
sudo cp ./systeminfo /bin/systeminfo
```
or
```bash
sudo wget -O /bin/systeminfo https://raw.githubusercontent.com/kutsy/systeminfo/master/systeminfo
```
And make it executable
```bash
sudo chmod +x /bin/systeminfo
```

Add to the end of **~/.profile** file
```bash
echo "/bin/systeminfo" >> ~/.profile
```
