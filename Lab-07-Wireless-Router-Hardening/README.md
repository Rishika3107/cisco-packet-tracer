# Lab 07 — Wireless Router Hardening and Network Segmentation

---

## Objectives  

**Part 1:** Configure Basic Security Settings for a Wireless Router  

**Part 2:** Configure Wireless Router Network Security  

**Part 3:** Configure Wireless Clients Network Security  

**Part 4:** Verify Connectivity and Security Settings  

---

## Background  

In this lab, I secured a partially configured home wireless router by applying basic hardening techniques. The router initially contained multiple security weaknesses such as default credentials, enabled remote management, and unsecured wireless networks.

My task was to strengthen router authentication, configure encrypted wireless networks, separate guest traffic from internal devices, and validate secure connectivity for laptops and IoT devices.

This activity demonstrates practical wireless security hardening and network segmentation used in real environments.

---

# Part 1 — Configure Basic Router Security  

## Step 1 — Change Default Router Credentials  

From **Home Office PC**:

1. Opened **Web Browser**
2. Navigated to:
192.168.0.1
3. Logged in using default credentials:Username: admin
Password: admin
4. Opened **Administration tab**
5. Changed router password to:
cisconetacadrocks!
6. Saved settings and re-authenticated using the new password.

---

## Step 2 — Disable Remote Management  

1. From **Administration**, disabled **Remote Management**
2. Saved settings

After router reboot, I refreshed IP configuration on Home Office PC and reconnected to the router for further configuration.

---

# Part 2 — Configure Wireless Router Network Security  

## Step 1 — Configure SSID Broadcast  

From **Wireless tab**:

- Enabled SSID broadcast on all radios
- Renamed all wireless networks to: HomeNet

6. Saved settings and re-authenticated using the new password.

---

## Step 2 — Disable Remote Management  

1. From **Administration**, disabled **Remote Management**
2. Saved settings

After router reboot, I refreshed IP configuration on Home Office PC and reconnected to the router for further configuration.

---

# Part 2 — Configure Wireless Router Network Security  

## Step 1 — Configure SSID Broadcast  

From **Wireless tab**:

- Enabled SSID broadcast on all radios
- Renamed all wireless networks to:

Saved settings.

---

## Step 2 — Secure HomeNet  

Configured on all radios:Security Mode: WPA2 Personal
Encryption: AES
Passphrase: ciscorocks
Saved settings.

---

## Step 3 — Configure Guest Network  

From **Guest Network submenu**:

Enabled Guest Profile and configured:
SSID: GuestNet
Broadcast SSID: Enabled
Security Mode: WPA2 Personal
Encryption: AES
Passphrase: guestpass
Saved settings.

---

# Part 3 — Configure Wireless Clients  

## Step 1 — Connect Laptops  

### Home Laptop 1:

- Connected to **HomeNet**
- Entered passphrase:
ciscorocks
Verified successful connection and DHCP address assignment.

---

### Home Laptop 2:

- Connected to **GuestNet**
- Entered passphrase:
guestpass
Verified DHCP assignment.

---

## Step 2 — Configure IoT Devices  

Configured following devices:

- Home Webcam  
- Home Siren  
- Home Doors  

Each device was set to:
SSID: HomeNet
Authentication: WPA2-PSK
Passphrase: ciscorocks
IP Assignment: DHCP
All devices successfully obtained IP addresses from the 192.168.0.0/24 network.

---

# Part 4 — Verify Connectivity and Security  

## Step 1 — Internet Connectivity  

From both laptops:

Visited:
www.ptsecurity.com
Verified successful page load.

---

## Step 2 — Enforce Network Segmentation  

Initially, GuestNet devices could ping HomeNet devices, representing a security risk.

From Home Laptop 2: ping Home Laptop 1

Ping was successful.

---

### Fix Applied  

From router Guest Network settings:

Unchecked:
Allow guests to see each other and access the local network
Saved settings.

---

### Verification  

From Home Laptop 2:
ping Home Laptop 1
Ping failed, confirming proper network isolation.

---

## Security Analysis  

This lab demonstrated:

- Importance of changing default router credentials  
- Disabling unnecessary remote management  
- Using WPA2 encryption with strong passphrases  
- Separating guest and internal networks  
- Securing IoT devices  
- Preventing lateral movement between wireless segments  

These are foundational hardening practices used to reduce attack surfaces in home and enterprise environments.

---

## Solution Summary  

In this lab, I:

- Hardened router administration settings  
- Secured wireless networks using WPA2 encryption  
- Created separate HomeNet and GuestNet networks  
- Connected laptops and IoT devices securely  
- Implemented guest network isolation  
- Verified secure connectivity  

This resulted in a properly segmented and hardened wireless environment.
