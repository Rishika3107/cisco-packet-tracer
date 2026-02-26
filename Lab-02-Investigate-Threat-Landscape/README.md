# Lab 02 — Investigate a Threat Landscape

---

## Objectives  

**Part 1:** Investigate a Network Configuration Vulnerability  

**Part 2:** Investigate a Phishing Malware Vulnerability  

**Part 3:** Investigate a Wireless Network and DNS Vulnerability  

---

## Background / Scenario  

In this lab, I investigated how different vulnerabilities can be exploited by threat actors. The “threat landscape” refers to all possible weaknesses that attackers can take advantage of. Most cybersecurity incidents do not occur because of a single issue. Instead, they happen when multiple vulnerabilities in systems, configurations, and user behavior are combined.

In this activity, I analyzed three types of vulnerabilities:

- A network misconfiguration in a home environment  
- A phishing-based malware attack  
- A rogue wireless access point combined with DNS manipulation  

Both the Data Center and ISP/Telco sites were locked in this simulation, so the focus was on exposed user networks and attacker-controlled environments.

---

# Part 1 — Investigate a Network Configuration Vulnerability  

### Step 1: Accessing the Guest Network  

I located Smartphone 3 outside the Home location and connected it to the open guest wireless network. Since the network was accessible without authentication, I used the command prompt to ping an internal device (192.168.100.101), which appeared to be a webcam.

After one or two request timeouts, the ping responses were successful. This confirmed that devices inside the private home network were reachable from the guest network.

This indicated a serious security misconfiguration.

---

### Step 2: Investigating the Home Router  

I moved to the Home Office PC and used the `ipconfig` command to determine the default gateway, which is the IP address of the Home Wireless Router.

Using the web browser, I accessed the router’s login page. Since the credentials were unknown, I researched the router model and discovered that the default username and password were both “admin.” I successfully logged in using these default credentials.

Inside the router configuration:

- I reviewed the Basic Wireless Settings and identified which radios were active along with their SSIDs.  
- I checked the Wireless Security settings to see whether encryption and passphrases were enabled.  
- I examined the Guest Network configuration.

I found that the Guest Network was active and improperly configured. Instead of providing internet-only access, it allowed access to devices inside the local network.

---

### Conclusion for Part 1  

The primary vulnerability was improper segmentation between the guest network and the internal LAN. This allowed unauthorized users to scan and access internal devices such as webcams.

To secure this network, I would recommend:

- Preventing guest networks from accessing internal devices  
- Changing default router credentials  
- Enabling WPA2/WPA3 encryption  
- Setting strong wireless passphrases  
- Regularly updating router firmware  

---

# Part 2 — Investigate a Phishing Malware Vulnerability  

### Step 1: Creating a Phishing Email  

From the Cafe network, I used the Cafe Hacker Laptop and opened the Email application. I composed a phishing email designed to persuade users to copy and paste a malicious URL (pix.example.com) into their web browser.

I sent this email to three users inside the Branch Office network.

---

### Step 2: Receiving the Email  

At the Branch Office, I opened the Email client on one of the devices and clicked Receive. After a short delay, the phishing email appeared in the inbox.

This demonstrated how easily malicious emails can be delivered to internal users.

---

### Step 3: Executing the Attack  

I copied the malicious URL from the email and pasted it into the web browser.

When the webpage loaded, it redirected to a malicious server, simulating malware delivery.

This type of attack is known as a phishing attack, which is a form of social engineering.

---

### Organizational Impact  

If this occurred in a real organization, such an attack could lead to:

- Credential theft  
- Malware infection  
- Ransomware spread  
- Data exfiltration  
- Financial and reputational damage  

This part of the lab highlighted that users are often the primary vulnerability in phishing attacks.

Preventive measures include:

- Employee awareness training  
- Email filtering systems  
- Intrusion prevention systems  
- Malicious URL filtering  
- Endpoint security solutions  

---

# Part 3 — Investigate a Wireless Network and DNS Vulnerability  

### Step 1: Connecting to a Rogue Wireless Network  

In the Cafe, I examined the Hacker Backpack and observed that the attacker had deployed a wireless router and a network sniffer.

Using the Cafe Customer laptop, I opened the PC Wireless application, refreshed available networks, and connected to one of the “Cafe_WI-FI_FAST” networks.

This simulated how users often connect to open Wi-Fi networks without verifying authenticity.

---

### Step 2: Visiting a Legitimate Website  

I opened the web browser and entered `friends.example.com`.

Instead of loading the legitimate website, the browser redirected to a malicious server.

I observed that the malware server IP matched the one used earlier in the phishing scenario (`pix.example.com`), showing attacker infrastructure reuse.

---

### Step 3: Investigating the Source of the Attack  

I compared IP configuration details between victim devices and identified differences in DNS settings.

I then examined the Cafe Hacker Laptop and found that it was running DNS and DHCP services. The DNS records redirected legitimate domains to the attacker-controlled malware server, and DHCP distributed the attacker’s DNS address to connected clients.

This confirmed a classic rogue access point combined with DNS hijacking and man-in-the-middle attack.

---

## Summary  

In this activity, I examined three different ways vulnerabilities can lead to real-world exploits:

- Network misconfiguration allowing unauthorized access  
- Phishing attacks exploiting user trust  
- Rogue wireless networks combined with DNS manipulation  

This lab demonstrated that cybersecurity failures usually occur through a chain of weaknesses rather than a single flaw. As a cybersecurity professional, it is essential to identify, detect, and mitigate these vulnerabilities before they are exploited by threat actors.
