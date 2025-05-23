# Penetration Testing
# 🛡️ Wireshark Penetration Testing: Finding Weakly Encrypted Data

##  Project Overview

This project demonstrates how to use **Wireshark**, a powerful network protocol analyzer, to identify **weakly encrypted** or **plain text data** transmitted over a network. The focus is on detecting sensitive information like **usernames** and **passwords** that are not securely transmitted.

##  Prerequisites

* Basic understanding of computer networks
* Wireshark installed on your machine
* A test environment (e.g., local network or virtual machines)

---

##  Steps to Perform Wireshark Penetration Testing

### 1. **Start Wireshark Capture**

* Open Wireshark and select the **network interface** connected to the target.
* Click **Start Capture** to begin sniffing the network traffic.

### 2. **Apply Display Filters**

* Use display filters to narrow down the data:

  ```bash
  http
  tcp
  ftp
  telnet
  ```
* These protocols often transmit data in **plaintext**.

### 3. **Monitor Login Activities**

* Look for HTTP POST requests or **FTP login attempts**.
* Filter by:

  ```bash
  http.request.method == "POST"
  ftp.request.command == "USER"
  ftp.request.command == "PASS"
  ```

### 4. **Analyze Packet Details**

* Click on suspicious packets and expand the protocol layers.
* Check for fields such as:

  * `username`
  * `password`
  * `Authorization`

### 5. **Identify Weak Encryption or Plaintext Transmission**

* Look for credentials sent over:

  * HTTP instead of HTTPS
  * FTP instead of SFTP
  * Telnet instead of SSH

### 6. **Extract Credentials**

* Right-click the packet > **Follow TCP Stream**.
* Inspect the stream for readable **username\:password** data.

### 7. **Document Findings**

* Note down:

  * Protocol used
  * IP addresses
  * Timestamp
  * Credentials (if found)
  * Packet number

---

## ⚠️ Disclaimer

This project is intended for **educational** and **ethical testing** purposes **only**. Do not use Wireshark or any penetration testing tools on networks without **explicit authorization**.
