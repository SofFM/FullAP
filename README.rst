Introduction
============

*FullAP* is a package to create a wifi access point with different types of encription on linux. It depends on *hostapd* for AP provisioning and *dnsmasq* to assign IP addresses to devices. 

Dependencies
============

So, there 2 types of dependencies. 

System dependencies:
    - dnsmasq
    - hostapd 
    - python3

Python dependencies
    - wireless
    - netifaces
    - psutil

You can not install python dependencies manually, they will be installed while installing the package. 
If you want to do it manually, just type (or copy, it's better way :D)

::

    sudo apt install python3-dev python3-pip && sudo pip3 install wireless netifaces psutil

Installation
============

Easy way by using pip
::

    sudo apt update && sudo apt --yes --force-yes install dnsmasq hostapd python3-dev python3-pip && sudo pip3 install pyaccesspoint

Hard way

1. Install system dependencies
   ::

       sudo apt update && sudo apt --yes --force-yes install dnsmasq hostapd python3-dev unzip python3-pip

2. Download latest package
   ::

       cd ~ && wget --output-document=pyaccesspoint-master.zip https://github.com/Goblenus/pyaccesspoint/archive/master.zip

3. Unpack downloaded package
   ::

       unzip pyaccesspoint-master.zip && cd pyaccesspoint-master

4. Install it
   ::

       sudo python3 setup.py install

5. Remove files
   ::

       cd ~ && sudo rm -rf pyaccesspoint-master.zip pyaccesspoint-master

That is all. Now you can use PyAccessPoint.

One line install:

::

    sudo apt update && sudo apt --yes --force-yes install dnsmasq hostapd python3-dev unzip python3-pip && cd ~ && wget --output-document=pyaccesspoint-master.zip https://github.com/Goblenus/pyaccesspoint/archive/master.zip && unzip pyaccesspoint-master.zip && cd pyaccesspoint-master && sudo python3 setup.py install && cd ~ && sudo rm -rf pyaccesspoint-master.zip pyaccesspoint-master

Usage
=====

You can use it as standalone command line utility:
To start
::

    sudo pyaccesspoint start

It will create hotspot named "MyAccessPoint" on wlan0 with "1234567890" password.

All arguments you may obtain by typing:
::

    pyaccesspoint --help

To stop
::

    sudo pyaccesspoint stop

You can configure and save config file. This will save you time at them next start

::

    sudo pyaccesspoint configure

You config file file will be placed at /etc/accesspoint/accesspoint.json. 
To start it with config file just type:
::

    sudo pyaccesspoint --config start

Code usage
============

1. Import
   ::

       from PyAccessPoint import pyaccesspoint

2. Create AccessPoint class
   ::

        access_point = pyaccesspoint.AccessPoint()

3. Start it
   ::

        access_point.start()

4. Stop it
   ::

        access_point.stop()

To check is accesspoint started use is_running
   ::

        access_point.is_running()

You can change accesspoint parameters while creating AccessPoint class

Class parameters:
    - **wlan** - wlan interface
    - **inet** - wlan forward to interface (use None to off forwarding)
    - **ip** - just ip of your accesspoint wlan interface
    - **netmask** - so... -> (`wiki link <https://en.wikipedia.org/wiki/Subnetwork>`_)
    - **ssid** - name of your accesspoint
    - **password** - password of your accesspoint

Tested
======

-  OrangePi Plus with Armbian 5.23

Note
====

This project is python3 compatible only, python2 is not tested at all.

Idea
====

This project is fork of https://github.com/Goblenus/pyaccesspoint

