# Lab 05: File Hashing & Integrity Analysis

## Objective
Generate cryptographic hashes to establish data integrity and observe the Avalanche Effect by modifying file contents. 

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `echo`, `sha256sum`

---

## Execution Steps

### 1. Baseline File Creation
Simulated a plain-text digital artifact (representing a potential phishing payload or evidence file) using the `echo` command to write strings directly into a new file named `invoice_urgent.txt`.

### 2. Baseline Hash Generation
Utilized the SHA-256 cryptographic algorithm to generate the initial digital fingerprint of the artifact:
`sha256sum invoice_urgent.txt`
*Resulting Hash:* `b1c1209f2e0cd7b8329f78c700789ac282b4bb5d4c1691b85442c0423783220b`

### 3. File Modification & The Avalanche Effect
Appended a single character (`!`) to the end of the text file to simulate tampering or a minor malware mutation. The file was then hashed a second time. 

---

## Findings & Concept Analysis

The second execution of the `sha256sum` command yielded a completely unrecognizable hash compared to the baseline. 

This perfectly demonstrated the **Avalanche Effect**—a cryptographic property where a microscopic change to the input (even a single bit) results in a drastically different output hash. 

## Key Takeaway
Cryptographic hashing (SHA-256) is a vital mechanism for SOC analysts and digital forensics investigators. It is actively used to prove that digital evidence maintains absolute integrity and has not been tampered with, and to map malicious file signatures against global threat intelligence databases (like VirusTotal) for rapid identification.
