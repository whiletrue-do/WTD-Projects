---
layout: default
title: Local Network Setup
parent: pi config
grand_parent: Raspberry pi 
nav_order: 1
---

# Local Network Setup for Raspberry Pi

## Table of Contents

1. [Pre-requisites](#pre-requisites)
2. [Setting up your network for a static IP](#setting-up-your-network-for-a-static-ip)
   - [Finding your MAC Address](#finding-your-mac-address)
   - [Configuring dhcpcd.conf](#configuring-dhcpcdconf)
   - [Setting up your Router](#setting-up-your-router)

---

## Pre-requisites

Before diving into the guide, make sure you meet the following criteria:

- You are using a Linux or macOS system. (Windows instructions will be added later.)
- You have installed a desktop server like Raspios (Bullseye version at the time of writing) on your Raspberry Pi.
- You have completed the basic setup and connected your Raspberry Pi to the internet via WiFi or Ethernet.

## Setting up your network for a static IP

Assigning a static IP address to your Raspberry Pi is beneficial, especially if you frequently rebuild or reconfigure your device. A static IP ensures that your Pi's address remains constant, making network management easier.

### Finding your MAC Address

The first step in setting up a static IP is to find the MAC address of your Raspberry Pi. You can do this by running the `ifconfig` command followed by the network interface you're using:

- For Ethernet: `ifconfig eth0`
- For WiFi: `ifconfig wlan0`

Alternatively, you can run `ifconfig` and look for the `ether` address, which will look something like `ether rf:d9:7t:pj:42`.

### Configuring dhcpcd.conf

Open the `dhcpcd.conf` file using a text editor with superuser permissions:

```bash
sudo nano /etc/dhcpcd.conf
```

Scroll down to find the example static IP configuration. You can set up your own configuration as shown below:

#### For Ethernet

```bash
interface eth0
static ip_address=192.168.0.10/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```

#### For WiFi

```bash
interface wlan0
static ip_address=192.168.0.10/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```

Feel free to configure both if you switch between Ethernet and WiFi.

### Setting up your Router

1. Log into your router's admin panel.
2. Navigate to the `LAN` section.
3. Locate the `DHCP` or `DHCP Server` settings.
4. Find the section for manually assigning IPs, often labeled as `Manually Assigned IP around the DHCP list` or similar.

Here, you'll typically see fields for:

- Client Name (MAC Address)
- IP Address
- DNS Server (Optional)
- Host Name (Optional)

Fill in the MAC Address and IP Address fields:

- MAC Address: `rf:d9:7t:pj:42` (example)
- IP Address: `192.168.1.10`

#### Note on Choosing your IP

Your router may have limitations on the number of connections it can handle. Check the DHCP settings to find the IP address range supported by your router. Make sure the IP address you choose is within this range and not already in use by another device.

---

And there you have it! Your Raspberry Pi should now have a static IP address, making it easier to manage on your local network.