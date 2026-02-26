# Lab 04 — Access Control List Demonstration

---

## Objectives  

**Part 1:** Verify Local Connectivity and Test Access Control List  

**Part 2:** Remove Access Control List and Repeat Test  

---

## Background  

In this lab, I observed how an Access Control List (ACL) can be used to control traffic between networks. The activity demonstrates how ACLs can block specific types of traffic and how removing the ACL restores connectivity.

Initially, ICMP traffic from one network was denied by the router configuration. After removing the ACL, communication between networks was re-established.

---

# Part 1 — Verify Local Connectivity and Test Access Control List  

### Step 1: Verify Local Connectivity  

From PC1, I performed the following tests:

- Pinged PC2  
- Pinged PC3  

Both pings were successful.

### Explanation  

These devices are located on the same local network, and no ACL restrictions were applied to local traffic. Therefore, ICMP packets were allowed to pass freely.

---

### Step 2: Test Connectivity to Remote Networks  

Next, from PC1, I attempted to:

- Ping PC4  
- Ping the DNS Server  

Both pings failed.

### Explanation  

The failures occurred because an ACL was configured on Router R1 to block traffic originating from the 192.168.10.0/24 network. This ACL specifically denied ICMP packets, preventing PC1 from reaching remote hosts.

---

# Part 2 — Remove ACL and Repeat Test  

### Step 1: Investigate the ACL Configuration  

On Router R1, I used the following commands:
show run
show access-lists
The output showed: Standard IP access list 11
10 deny 192.168.10.0 0.0.0.255
20 permit any
This ACL denied all traffic from the 192.168.10.0/24 network and allowed all other traffic.

Using `show run`, I identified that ACL 11 was applied as an outgoing filter on interface:
Serial0/0/0
---

### Step 2: Remove the ACL  

I removed ACL 11 from the Serial0/0/0 interface using:R1(config)# interface se0/0/0
R1(config-if)# no ip access-group 11 out
Then, in global configuration mode, I deleted the ACL:
R1(config)# no access-list 11
---

### Step 3: Verify Connectivity After Removal  

After removing the ACL:

- PC1 successfully pinged PC4  
- PC1 successfully pinged the DNS Server  

This confirmed that traffic was no longer being filtered by the router.

---

## Security Analysis  

This lab demonstrated how ACLs act as traffic filters at the network layer. By denying traffic from a specific subnet, the router effectively prevented communication with remote networks.

ACLs are commonly used to:

- Restrict access between networks  
- Limit exposure of internal resources  
- Enforce security policies  

However, incorrect ACL configurations can unintentionally block legitimate traffic.

---

## Solution Summary  

In this lab, I:

- Verified local connectivity  
- Observed failed pings to remote networks due to ACL restrictions  
- Identified ACL 11 on Router R1  
- Removed the ACL from the interface and configuration  
- Confirmed restored connectivity  

This demonstrated the impact of ACLs on network communication.
