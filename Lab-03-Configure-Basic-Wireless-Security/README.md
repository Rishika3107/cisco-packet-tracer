# Lab 03 — Configure Basic Wireless Security

---

## Objectives  

Configure basic wireless security using WPA2 Personal.

---

## Background / Scenario  

In this lab, I secured a small wireless network to prevent unauthorized access.  
The scenario represents a small business environment where the wireless router was initially unsecured.

The goal was to implement WPA2 Personal security on the 2.4 GHz network and verify that legitimate users could still access the internet after encryption was enabled.

---

## Logical Topology  

The network consisted of:

- A Laptop (wireless client)  
- A Wireless Router  
- Internet connectivity  
- A Web Server (www.cisco.pka)  

The laptop connects wirelessly to the router, which provides internet access to the web server.

---

## Part 1 — Verify Initial Connectivity  

Before configuring security, I verified that the network was functioning.

Steps performed:

1. Opened **Desktop → Web Browser** on the Laptop  
2. Entered: www.cisco.pka
The webpage loaded successfully, confirming that connectivity existed before applying wireless security.

---

## Part 2 — Configure Basic Wireless Security  

I accessed the wireless router configuration page using the default gateway: 192.168.1.1
Login credentials used:

- Username: admin  
- Password: admin  

Inside the router interface:

1. Navigated to **Wireless → Wireless Security**
2. Observed that security was initially disabled
3. For the **2.4 GHz network**, changed security mode to:
WPA2 Personal
4. Left the 5 GHz networks disabled
5. Entered the passphrase: Network123
6. Saved the settings and closed the browser

This applied WPA2 encryption to the wireless network.

---

## Part 3 — Update Wireless Settings on Laptop  

After securing the router, I reconnected the laptop using the new credentials:

1. Opened **Desktop → PC Wireless**
2. Selected the **Academy** network
3. Clicked **Connect**
4. Entered the pre-shared key:
Network123
5. Successfully connected to the secured wireless network

---

## Part 4 — Verify Connectivity After Security Configuration  

To confirm everything worked correctly:

1. Opened **Web Browser** on the Laptop
2. Entered:
www.cisco.pka
The webpage loaded successfully again, proving that:

- WPA2 security was correctly configured  
- The laptop authenticated properly  
- Internet connectivity was preserved  

---

## Security Analysis  

Before configuration, the wireless network was open and vulnerable to:

- Unauthorized access  
- Packet interception  
- Credential theft  

By enabling WPA2 Personal:

- Wireless traffic became encrypted  
- Only authenticated users could connect  
- The attack surface was significantly reduced  

This demonstrates how basic wireless security controls can immediately improve network protection.

---

## Solution Summary  

In this lab, I:

- Verified initial connectivity  
- Enabled WPA2 Personal on the wireless router  
- Configured a secure passphrase  
- Reconnected the laptop using the new credentials  
- Confirmed successful internet access  

This exercise showed how simple security configurations can prevent unauthorized wireless access while maintaining normal network operations.
