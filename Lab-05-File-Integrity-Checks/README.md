# Lab 05 — File and Data Integrity Checks

---

## Objectives  

**Part 1:** Recover Files after a Cyber Attack  

**Part 2:** Using Hashing to Verify File Integrity  

**Part 3:** Using HMAC to Verify File Integrity  

---

## Background  

In this lab, I verified the integrity of multiple files using hashing techniques to ensure that no data had been tampered with after a simulated cyber attack. File integrity is critical in cybersecurity because even a single modified character will generate a completely different hash value.

In this activity, I recovered archived client files, validated them using MD5 hashing, identified a tampered file, escalated the issue, and finally used HMAC with a secret key to validate a critical financial file.

The network configuration and services were already pre-configured in Packet Tracer. My role was to verify, recover, and validate file integrity using hashing tools.

---

# Part 1 — Recover Files After a Cyber Attack  

### Step 1: Access the Branch Server  

From Laptop BR-1 in the Branch Office:

1. Opened **Desktop → Web Browser**
2. Entered: http://branch.corp
3. Accessed the current files available on the branch server

This confirmed that the branch server had experienced data loss or corruption.

---

### Step 2: Retrieve Original Hash Values  

To validate file integrity, I needed the original archived hash values.

1. Entered: http://hq.corp
2. Accessed the most recent file archive
3. Copied the file names and corresponding hash values
4. Opened the **CSE-LABVM**
5. Pasted the hash values into a text file for comparison

These hashes serve as the baseline integrity reference.

---

### Step 3: Download Backup Files Using FTP  

Back in Packet Tracer on Laptop BR-1:

1. Opened **Command Prompt**
2. Connected to the FTP server:
ftp hq.corp
3. Logged in with: Username: mike
Password: cisco123
4. Listed available files: dir
5. Downloaded all six client files:
get NEclients.txt
get NWclients.txt
get Nclients.txt
get SEclients.txt
get SWclients.txt
get Sclients.txt
6. Verified successful download using: dir

All files were successfully restored to Mike’s PC.

---

# Part 2 — Using Hashing to Verify File Integrity  

### Step 1: Compute MD5 Hash Values  

To verify integrity, I:

1. Opened each downloaded file on Mike’s PC
2. Copied the file contents
3. Opened the CSE-LABVM terminal
4. Generated an MD5 hash using:
echo -n 'file-contents' | md5sum
5. Compared the generated hash with the original archived hash

For most files, the hash values matched, confirming they had not been altered.

However, one file produced a different hash value, indicating tampering.

---

### Identifying the Tampered File  

The file whose computed MD5 hash did not match the archived hash was identified as compromised.

Since hashing produces a completely different output even if one character changes, this confirmed that the file had been modified after archival.

---

### Step 2: Escalation  

After identifying the tampered file:

1. Opened **Email**
2. Composed a message to:
sally@branch.corp
3. Reported that the file server had been compromised and a file integrity issue was detected

This simulated proper incident escalation procedures.

---

### Step 3: Transfer Tampered File to Sally  

From HQ-Laptop-1:

1. Opened **Command Prompt**
2. Connected to FTP server: ftp hq.corp
3. Logged in with: Username: sally
Password: cisco321
4. Downloaded the compromised file
5. Verified it was present using: dir
The file was successfully transferred for further forensic analysis.

---

# Part 3 — Using HMAC to Verify File Integrity  

In this section, I validated a critical financial file using HMAC (Hash-Based Message Authentication Code).

HMAC improves security by combining hashing with a secret key.

---

### Step 1: Verify File Availability  

On HQ-Laptop-2:

1. Opened **Command Prompt**
2. Used: dir

3. Confirmed that the file `income.txt` existed

---

### Step 2: Generate HMAC  

In the CSE-LABVM:

1. Opened the terminal
2. Saved the file contents as `income.txt`
3. Generated HMAC using: openssl dgst -sha256 -hmac cisco123 income.txt
This generated a secure SHA-256 HMAC using the secret key `cisco123`.

---

### Security Analysis  

Using basic hashing (MD5):

- Detects whether file contents have changed  
- Does not provide authentication  
- Is vulnerable to collision attacks  

Using HMAC:

- Requires a secret key  
- Prevents unauthorized tampering  
- Provides stronger integrity validation  
- Protects against man-in-the-middle manipulation  

HMAC is more secure than standard hashing because only parties with the secret key can generate the correct authentication code.

---

## Solution Summary  

In this lab, I:

- Recovered client files from a backup FTP server  
- Retrieved archived hash values  
- Generated MD5 hashes to verify file integrity  
- Identified a tampered file  
- Escalated the incident to a supervisor  
- Transferred the compromised file for investigation  
- Used HMAC with SHA-256 to verify a critical financial document  

This lab demonstrated the importance of file integrity validation in cybersecurity operations.
