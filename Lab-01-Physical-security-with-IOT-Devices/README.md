# Lab8 – Connect IoT Devices and Configure Registration Server

## Objectives

Part 1: Connect IoT Devices to the Network  
Part 2: Add IoT Devices to the Registration Server  
Part 3: Explore IoT Security Device Functionality  

---

## Background / Scenario

In this Packet Tracer activity, I installed IoT security devices in a simulated home network environment. I connected the IoT devices to the wireless network, configured MAC filtering for controlled access, and registered the devices with a remote IoT registration server. Finally, I tested device behavior and monitored functionality through the server interface.

This lab demonstrates how IoT devices integrate into secure wireless environments and how centralized monitoring improves home security management.

---

# Part 1 – Connect IoT Devices to the Network

## Step 1: Connect the Siren to the Door

I navigated to the Home environment and located:

- Home_Siren  
- Home_Doors  

Using the **IoT Custom Cable**, I connected:

Home_Siren (DO interface) → Home_Doors (DO interface)

After connecting, I tested functionality by holding the **ALT key** and clicking the door to open and close it.

### Observation:
When the door was opened, the siren automatically activated.  
This confirmed successful IoT device linkage.

---

## Step 2: Associate IoT Devices to HomeNet Wireless Network

The following wireless IoT devices were configured:

- Home_Siren  
- Home_Doors  
- Home_Motion_Sensor  
- Home_Webcam  

For each device, I performed the following: SSID: HomeNet
Authentication: WPA2-PSK
Pass Phrase: ciscorocks
3. Under IP Configuration:
   - Selected DHCP
   - Verified IP address from 192.168.0.0/24 network

If convergence was delayed, I toggled between Static and DHCP.

---

## Step 3: Record MAC Addresses

For each IoT device, I recorded the MAC address.

I reformatted them using colons:

Example format:AA:BB:CC:DD:EE:FF

1. Opened **Config tab → Wireless0**
2. Set:

These MAC addresses were required for MAC filtering configuration.

---

## Step 4: Configure MAC Address Filtering

From **Home Office PC → Web Browser**, I accessed:
http://192.168.0.1
Logged in using: Username: admin
Password: admin
Navigated to:

Wireless → Wireless MAC Filter

Verified:
- MAC Filter enabled
- Set to Permit listed devices

Added the four IoT device MAC addresses.

Clicked **Save Settings**.

The router rebooted.

After reboot:
- Renewed IP configuration if required
- Verified Home Office PC received 192.168.0.x address

---

# Part 2 – Add IoT Devices to the Registration Server

## Step 1: Create Account on ISP IoT Server

From the Home Office PC browser, I navigated to:
http://10.3.0.125
Clicked **Sign Up Now** and created: Username: HomeUser
Password: Pa$$w0rd
---

## Step 2: Register IoT Devices

For each IoT device:

1. Opened device → Config tab → GLOBAL Settings
2. Scrolled to IoT section
3. Selected:
Remote Server
Server Address: 10.3.0.125
Username: HomeUser
Password: Pa$$w0rd
4. Clicked **Connect**

The status changed:
Connecting → Refresh

This confirmed successful registration.

Repeated for all four devices.

---

## Step 3: Verify Registration

Logged into: http://10.3.0.125
Verified all four IoT devices appeared in dashboard.

---

# Part 3 – Explore IoT Security Device Functionality

## Step 1: Control Devices from Server

From the Registration Server dashboard:

- Checked status of each device.
- Activated Home_Doors using red rectangle.
- Observed door state changed.
- Activated Home_Webcam (green rectangle).
- Motion Sensor displayed monitoring-only functionality.

### Observations:

- Door activation triggered siren.
- Webcam status toggled ON/OFF.
- Motion sensor only reported activity (monitoring device).

---

## Step 2: Interact Using ALT Key

Performed ALT interactions inside Packet Tracer:

- ALT-clicked Door → Triggered siren alert.
- ALT-clicked Webcam → Status changed on server.
- ALT-hover over Motion Sensor → Activity logged on server dashboard.

This demonstrated real-time synchronization between IoT device and registration server.

---

# Reflection Questions

## 1. Advantages of IoT Enabled Devices in Home Security

- Real-time monitoring
- Remote control access
- Automated alert systems
- Improved situational awareness
- Integrated device communication

---

## 2. Advantage of Registration Server

- Centralized monitoring
- Remote management
- Device authentication
- Real-time status updates
- Simplified device control

---

## 3. Examples of IoT Security Devices

Common IoT devices used in home security:

- Smart cameras
- Smart locks
- Motion sensors
- Smart doorbells
- Environmental sensors
- Alarm systems
- Smart lighting automation

---

# Summary

In this lab, I successfully configured and integrated IoT devices within a secured wireless home network. I established device-to-device communication using custom IoT cabling, configured WPA2 wireless authentication, implemented MAC address filtering for enhanced security, and registered all devices with a centralized IoT registration server.

The lab demonstrated how IoT systems operate within a structured network environment and highlighted the importance of authentication, network segmentation, and centralized monitoring. This exercise reinforced practical knowledge of IoT device configuration, wireless security enforcement, and remote device management in a smart home environment.
