# Introduction
*PyAccessPoint* is a package to create a wifi access point on linux. It depends on *hostapd* for AP provisioning and *dnsmasq* to assign IP addresses to devices.

# Dependencies
So, there 2 types of dependencies:
* system dependencies
    * dnsmasq
    * hostapd
    * python3
* python dependencies
    * wireless
    * netifaces
    * psutil

You can not install python dependencies manually, they will be installed while installing the package.
If you want to do it manually, just type (or copy, it's better way :D)
```
sudo apt install python3-dev python3-pip && sudo pip3 install wireless netifaces psutil
```

# Installation
1. Install system dependencies
    ```
    sudo apt update && sudo apt --yes --force-yes install dnsmasq hostapd python3-dev unzip python3-pip
    ```

2. Download latest package
    ```
    cd ~ && wget --output-document=pyaccesspoint-master.zip https://github.com/Goblenus/pyaccesspoint/archive/master.zip
    ```

3. Unpack downloaded package
    ```
    unzip pyaccesspoint-master.zip && cd pyaccesspoint-master
    ```

4. Install it
    ```
    sudo python3 setup.py install
    ```

5. Remove files
    ```
    cd ~ && sudo rm -rf pyaccesspoint-master.zip pyaccesspoint-master
    ```

That is all. Now you can use PyAccessPoint.

One line install:
```
sudo apt update && sudo apt --yes --force-yes install dnsmasq hostapd python3-dev unzip python3-pip && cd ~ && wget --output-document=pyaccesspoint-master.zip https://github.com/Goblenus/pyaccesspoint/archive/master.zip && unzip pyaccesspoint-master.zip && cd pyaccesspoint-master && sudo python3 setup.py install && cd ~ && sudo rm -rf pyaccesspoint-master.zip pyaccesspoint-master
```

# Usage
You can use it as standalone command line utility:
To start
```
sudo pyaccesspoint start
```

It will create hotspot named "MyAccessPoint" on wlan0 with "1234567890" password.
All arguments you may obtain by typing:
```
pyaccesspoint --help
```

To stop
```
sudo pyaccesspoint stop
```

You can configure and save config file. This will save you time at the next start
```
sudo pyaccesspoint -config configure
```
You config file file will be placed at /etc/accesspoint/accesspoint.json.
To start it with config file just type:
```
sudo pyaccesspoint -config start
```

# Tested
* OrangePi Plus with Armbian 5.23

# Note
This project is python3 compatible only, python2 is not tested at all.

# Idea
This project is fork of https://github.com/prahladyeri/hotspotd (Prahlad Yeri - prahladyeri@yahoo.com)