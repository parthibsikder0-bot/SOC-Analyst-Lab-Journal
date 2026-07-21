# Lab 09: Packet Analysis and Credential Harvesting

## Objective
Capture raw network traffic and analyze the packets to demonstrate the vulnerabilities of transmitting authentication credentials over unencrypted protocols (HTTP).

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `tcpdump`, `wireshark`, `curl`, `nc`, `base64`

---

## Execution Steps

### 1. Packet Capture Generation
Established a local network listener using Netcat (`nc -lvnp 8080`) and simultaneously initiated a packet capture on the loopback interface using `tcpdump`. 

### 2. Simulating Insecure Authentication
Transmitted a mock authentication request containing cleartext credentials (`admin:ClearTextIsDangerous`) over HTTP using `curl`. 

### 3. Traffic Analysis & Credential Extraction
Analyzed the captured raw HTTP GET request. Identified the `Authorization: Basic` header, which transmits credentials using easily reversible Base64 encoding rather than secure encryption. 

### 4. Decoding the Payload
Extracted the encoded string (`YWRtaW46Q2xlYXJUZXh0SXNEYW5nZXJvdXM=`) and reversed the encoding using the command-line `base64 -d` utility, successfully recovering the compromised username and password in plain text.

## Key Takeaway
Unencrypted protocols (like HTTP, Telnet, and FTP) offer zero data confidentiality. Network sniffers can trivially intercept and decode Basic Authentication headers, highlighting the critical necessity of enforcing TLS/SSL (HTTPS) across all network communications.
