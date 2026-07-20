# Lab 03: Network Traffic Analysis & Packet Inspection

## Objective
Capture and analyze live network traffic to understand packet structures, isolate specific protocols, and filter out background network noise.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** Wireshark, Ping

---

## Execution Steps

### 1. Packet Capture Initialization
Launched Wireshark with elevated system privileges to bind to the network interface. Initiated a live packet capture on the primary virtual ethernet interface (`eth0`).

### 2. Traffic Generation
Generated controlled, predictable network traffic to a known external endpoint (Google Public DNS) by executing:
`ping -c 4 8.8.8.8`

### 3. Traffic Isolation and Filtering
Halted the live capture and applied a display filter (`icmp`) to the raw packet data. This successfully removed background noise (such as local ARP broadcasts) and isolated the target traffic for analysis.

---

## Findings & Packet Analysis

The isolated capture confirmed a perfect handshake between the local machine and the external server. The capture revealed:

* **Source IP:** `10.0.2.15` (Local Kali VM)
* **Destination IP:** `8.8.8.8` (Google DNS)
* **Packet Count:** Exactly 8 ICMP packets were isolated.
* **Traffic Flow:** 4 `Echo (ping) request` packets were transmitted by the local machine, and 4 `Echo (ping) reply` packets were successfully received from the destination. 
* **Background Activity:** Prior to filtering, Address Resolution Protocol (ARP) packets were observed broadcasting to the local network to map IP addresses to physical MAC addresses.

## Key Takeaway
Raw network captures contain overwhelming amounts of background noise. The ability to write and apply targeted display filters (like `icmp`) is critical for an analyst to rapidly isolate suspicious traffic or verify successful network communications during an incident.
