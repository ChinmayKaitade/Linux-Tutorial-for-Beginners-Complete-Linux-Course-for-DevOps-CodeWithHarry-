# ⚙️ **Processes & Services**

Managing active background processes and system daemons is a cornerstone of Linux server administration. 🔄  
System engineers monitor compute resources to diagnose bottlenecks, hung processes, and service failures. 📊  
Using `systemd` controllers ensures production workloads like Nginx, Docker, or Node.js auto-recover and run reliably. 🚀

---

## 🔍 **Monitoring Active System Processes**

### 📋 `ps` (Process Status Snapshot)

- **What it does:** Displays an instant snapshot of processes currently running in your active shell terminal session.
- **DevOps Use Case:** Quick sanity checks to see your active bash commands or shell subprocesses.

```bash
ps
```

### 🌐 `ps aux` (Exhaustive System-Wide Process List)

- **What it does:** Lists every running process across the entire operating system, regardless of which user owns it.
- **DevOps Use Case:** Auditing PID (Process ID) numbers, user execution contexts, CPU percentages, and RAM consumption.

```bash
ps aux
```

- **Deciphering the Flags:**
- `a`: Shows processes running for all users.
- `u`: Displays detailed user-oriented information (owner, `%CPU`, `%MEM`).
- `x`: Includes processes running in the background without an attached terminal session (daemons).

### 🎯 `ps aux | grep nginx` (Process Filtering)

- **What it does:** Pipes the full process table into `grep` to isolate only records matching a specific application name.
- **DevOps Use Case:** Confirming whether web server workers, database instances, or microservice listeners are live and retrieving their PIDs.

```bash
ps aux | grep nginx
```

### 📊 `top` (Real-Time System & Resource Dashboard)

- **What it does:** Opens an interactive, auto-refreshing monitor showing overall CPU load, memory utilization, and top resource-draining processes.
- **DevOps Use Case:** Identifying memory leaks, rogue infinite loops, or CPU spikes during production traffic surges.

```bash
top
```

> 💡 **Navigation in `top`:** Press `M` to sort by Memory usage, `P` to sort by CPU usage, `k` to kill a PID interactively, and `q` to exit.

---

## 🎛️ **Service Orchestration with `systemctl**`

Ubuntu uses `systemd` as its default initialization system to manage daemon lifecycles and background services.

### 🩺 Inspecting & Modifying Service States

- **🔍 `systemctl status nginx` (Health Check):**
  Inspects whether the target service is active (running), inactive (dead), or failed, along with recent service log lines.

```bash
systemctl status nginx
```

- **⏹️ `sudo systemctl stop nginx` (Halt Service):**
  Terminates the active processes belonging to the service immediately.

```bash
sudo systemctl stop nginx
```

- **▶️ `sudo systemctl start nginx` (Initiate Service):**
  Spins up the service daemon and binds it to configured network sockets.

```bash
sudo systemctl start nginx
```

- **🔄 `sudo systemctl restart nginx` (Hard Restart):**
  Stops the service entirely and launches it again. Drops active connections temporarily during the restart.

```bash
sudo systemctl restart nginx
```

- **⚡ `sudo systemctl reload nginx` (Graceful Zero-Downtime Reload):**
  Re-reads updated configuration files without dropping existing user connections or shutting down master worker processes.

```bash
sudo systemctl reload nginx
```

---

## 🔁 **Boot-Time Lifecycle Configuration**

Configure which services should automatically spin up whenever the virtual machine or cloud server reboots.

### 🟢 `sudo systemctl enable nginx` (Auto-Start on Boot)

- **What it does:** Creates a symlink inside the systemd startup directory targets, ensuring Nginx boots up automatically on system start.
- **DevOps Use Case:** Guaranteeing web servers and background queue workers recover immediately after an unexpected server reboot or kernel patch.

```bash
sudo systemctl enable nginx
```

### 🔴 `sudo systemctl disable nginx` (Prevent Auto-Start)

- **What it does:** Removes the systemd startup symlink so the service stays dormant until manually invoked.
- **DevOps Use Case:** Decommissioning secondary or staging services so they do not consume server memory after reboots.

```bash
sudo systemctl disable nginx
```
