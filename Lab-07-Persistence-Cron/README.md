# Lab 07: Establishing and Hunting Persistence (Cron Jobs)

## Objective
Simulate a malicious persistence mechanism using Linux scheduled tasks (cron jobs) and execute a defensive hunt to identify and neutralize the automated backdoor.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `crontab`, `bash`, `cat`

---

## Execution Steps

### 1. Creating the Malicious Beacon
Developed a bash script (`beacon.sh`) to simulate malware communicating with a Command and Control (C2) server by appending a timestamp to a log file (`beacon_log.txt`) upon execution. 

### 2. Establishing Persistence
Leveraged the Linux cron daemon to automate the script. Edited the system crontab (`crontab -e`) and injected the schedule `* * * * * /home/kali/beacon.sh`, forcing the beacon to execute every 60 seconds autonomously, surviving system reboots.

### 3. Hunting and Remediation (SOC Response)
* **Discovery:** Audited the user's scheduled tasks using `crontab -l` to identify unauthorized automated jobs.
* **Neutralization:** Accessed the cron configuration (`crontab -e`), removed the malicious entry, and verified the removal to secure the system against persistent execution. 

## Key Takeaway
Attackers utilize native system scheduling tools like `cron` to maintain long-term access to compromised machines. Auditing scheduled tasks is a mandatory step in incident response and threat hunting to ensure all persistence mechanisms are eradicated.
