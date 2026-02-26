# Lab 06 — Explore File and Data Encryption

---

## Objectives  

**Part 1:** Discover the FTP Account Credentials for Mary  

**Part 2:** Upload Confidential Data using FTP  

**Part 3:** Discover the FTP Account Credentials for Bob  

**Part 4:** Download Confidential Data using FTP  

**Part 5:** Decrypt the Contents of a Sensitive File  

---

## Background  

In this lab, I accessed encrypted files, transferred confidential data using FTP, and decrypted sensitive information using OpenSSL. The activity simulated how encrypted credentials and files can be securely exchanged between users.

The network and services were already configured. My task was to decrypt login credentials, upload encrypted data, download it as another user, and finally decrypt the contents of the sensitive file.

OpenSSL was used for decryption. This lab also highlighted that while encryption protects confidentiality, the method used here is not suitable for real-world production systems due to weak key derivation and lack of integrity protection.

---

# Part 1 — Discover Mary’s FTP Account Credentials  

### Step 1: Access Mary’s Encrypted Login File  

On Laptop BR-1:

1. Opened **Desktop → Text Editor**
2. Opened the file: maryftplogin.txt
The file contained encrypted text.

---

### Step 2: Decrypt Mary’s Credentials  

1. Copied the encrypted contents  
2. Opened the terminal on CSE-LABVM  
3. Used OpenSSL to decrypt:
echo 'encrypted-text' | openssl aes-256-cbc -pbkdf2 -a -d
4. Entered the password:
maryftp123
This revealed Mary’s FTP username and password.

---

# Part 2 — Upload Confidential Data Using FTP  

### Step 1: View the Encrypted Client File  

Back on Laptop BR-1, I opened:
clientinfo.enc
The contents were unreadable, confirming the data was encrypted.

---

### Step 2: Connect to the BR Server  

Using Command Prompt:
ftp 10.0.3.30
Logged in with Mary’s decrypted credentials.

---

### Step 3: Upload the Encrypted File  

1. Listed server files:
dir
2. Uploaded the encrypted file:
put clientinfo.enc
3. Verified upload: dir
4. Quit FTP.

---

### Observation  

If attackers captured this transfer, they would only see encrypted data, not readable client information. However, FTP credentials would still be visible in clear text.

---

# Part 3 — Discover Bob’s FTP Account Credentials  

### Step 1: Access Bob’s Encrypted Login File  

On Laptop BR-2:

1. Opened **Text Editor**
2. Opened:
bobftplogin.txt
---

### Step 2: Decrypt Bob’s Credentials  

1. Copied encrypted contents  
2. Returned to CSE-LABVM terminal  
3. Ran: echo 'encrypted-text' | openssl aes-256-cbc -pbkdf2 -a -d

4. Entered:
bobftp123
This revealed Bob’s FTP username and password.

---

# Part 4 — Download Confidential Data Using FTP  

### Step 1: Connect to the BR Server  

On Laptop BR-2: ftp 10.0.3.30
Logged in using Bob’s credentials.

---

### Step 2: Download Encrypted File  

1. Listed files: dir
2. Downloaded:
get clientinfo.enc
3. Verified file locally: dir
---

### Observation  

If attackers intercepted this transfer, only encrypted data would be visible, but FTP authentication details would still be exposed.

---

# Part 5 — Decrypt the Sensitive File  

### Step 1: Retrieve Decryption Key  

Bob received the decryption password through email.  
I opened Email and recorded the key sent by Mary.

---

### Step 2: Decrypt clientinfo.enc  

1. Opened `clientinfo.enc`
2. Copied contents  
3. Saved file in CSE-LABVM as:
clientinfo.enc
4. Used OpenSSL: openssl aes-256-cbc -pbkdf2 -a -d -in clientinfo.enc -out clientinfo.txt
5. Entered the decryption password from email

This produced:
clientinfo.txt
Opening this file revealed the decrypted customer information.

---

## Security Analysis  

This lab demonstrated:

- Encryption protects confidentiality during file transfer  
- FTP does not protect usernames or passwords  
- Password-based encryption depends heavily on strong passwords  
- The method used does not provide integrity validation  

Although encrypted files were protected, FTP credentials remained exposed, highlighting why secure protocols like SFTP or FTPS are preferred in real environments.

---

## Solution Summary  

In this lab, I:

- Decrypted FTP credentials for two users  
- Uploaded encrypted client data  
- Downloaded the encrypted file as another user  
- Retrieved the decryption key via email  
- Decrypted confidential data using OpenSSL  

This demonstrated practical use of encryption and decryption in file transfers.
