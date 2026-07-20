# Lab 01: Rogue Process Identification & Containment

## Objective
Simulate the identification, tracking, and termination of a hidden background process using core Linux command-line utilities.

## Environment
* **OS:** Kali Linux (VirtualBox)
* **User:** `kali`
* **Tools Used:** `ss`, `ps`, `grep`, `kill`

---

## Execution Steps

### 1. Active Listening Port Inspection
Executed `ss -tulnp` to verify active network connections and confirm no unauthorized listening ports were exposed on the host.

### 2. Rogue Process Simulation
Initiated an unauthorized background process using `sleep 300 &` to simulate background malware or an active shell session.

### 3. Memory Snapshot & PID Isolation
Executed a full system process query filtered with `grep`:
`ps aux | grep sleep`
Identified the target process running with **PID 3576**.

### 4. Incident Containment
Issued a forceful termination signal (`SIGKILL`) directly to the kernel:
`kill -9 3576`
Verified termination via kernel output confirmation (`+ killed sleep 300`).

---

## Key Takeaway
Command-line process hunting forms the foundation of incident response when graphical interfaces are unavailable. Fast isolation of Process IDs (PIDs) is critical during active endpoint containment.
