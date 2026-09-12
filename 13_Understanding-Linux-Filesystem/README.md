# 🗂️ **Understanding Linux Filesystem**

Unlike Windows, which organizes storage across distinct drive letters (`C:\`, `D:\`), Linux unifies everything under a single hierarchical tree structure. 🌳  
This layout adheres strictly to the **Filesystem Hierarchy Standard (FHS)**, ensuring predictable file locations across distributions. 📐  
In Linux, the core philosophy holds true: _"Everything is a file"_ — including hardware devices, processes, and network sockets. ⚙️

---

## 🌳 **The Root Directory (`/`) & Core Hierarchy**

Every path in Linux originates from the root directory (`/`). Subdirectories branch out systematically based on function, permissions, and volatility:

```text
/ (Root)
├── bin -> usr/bin       # Essential user command binaries
├── boot                 # Kernel & bootloader boot files
├── dev                  # Device nodes & special device files
├── etc                  # Host-specific system configuration files
├── home                 # Personal user directories
├── lib -> usr/lib       # Shared system libraries & kernel modules
├── media / mnt          # Mount points for removable media / temporary mounts
├── opt                  # Add-on application software packages
├── proc                 # Virtual pseudo-filesystem for kernel & processes
├── root                 # Home directory for the root superuser
├── run                  # Runtime variable data since last boot
├── sbin -> usr/sbin     # System administration binaries
├── srv                  # Site-specific data served by the system
├── sys                  # Kernel subsystem & hardware device parameters
├── tmp                  # Temporary scratch files
├── usr                  # Secondary hierarchy for user utilities & applications
└── var                  # Variable dynamic files (logs, spools, caches)
```

---

## 📂 **Directory Breakdown & DevOps Relevance**

| Directory  | Full Name & Purpose                  | DevOps Real-World Relevance |
| ---------- | ------------------------------------ | --------------------------- |
| **`/etc`** | **Editable Text Configurations**<br> |

<br>Contains static system-wide configuration files and startup scripts. | The most heavily edited folder in DevOps: contains Nginx configurations (`/etc/nginx`), SSH daemon rules (`/etc/ssh/sshd_config`), and environment definitions (`/etc/environment`). |
| **`/var`** | **Variable Data**<br>

<br>Stores files whose content continuously expands and changes during runtime. | Essential for troubleshooting: houses application & system logs (`/var/log/syslog`, `/var/log/nginx/`), package caches, and default web assets (`/var/www/html`). |
| **`/home`** | **User Home Directories**<br>

<br>Personal storage workspaces for non-root users. | Contains developer user workspaces, custom bash profiles (`~/.bashrc`), and SSH authorized keys (`~/.ssh/authorized_keys`). |
| **`/root`** | **Superuser Home**<br>

<br>The personal home directory of the `root` administrative user. | Kept separate from `/home` to ensure the administrator can access root files even if the `/home` partition fails to mount. |
| **`/usr`** | **Unix System Resources**<br>

<br>Contains shareable, read-only user data, documentation, and installed binaries. | Holds user-installed packages, global libraries (`/usr/lib`), and general CLI tools (`/usr/bin/python3`, `/usr/bin/git`). |
| **`/bin` & `/sbin**` | **Binaries & System Binaries**<br>

<br>Core executable commands required for basic operation and repair. | `/bin` stores general user utilities (`ls`, `cat`, `mkdir`), while `/sbin` holds admin binaries (`iptables`, `fdisk`, `reboot`). Modern distros symlink these to `/usr/bin` and `/usr/sbin`. |
| **`/proc`** | **Process Information Pseudo-FS**<br>

<br>A virtual filesystem generated in RAM by the Linux kernel on the fly. | Does not consume disk space; allows inspection of live kernel metrics: CPU info (`cat /proc/cpuinfo`), memory health (`cat /proc/meminfo`), or process runtime parameters. |
| **`/dev`** | **Device Nodes**<br>

<br>Represents attached physical and virtual hardware as files. | Access disks (`/dev/sda`, `/dev/nvme0n1`), discard output stream blackholes (`/dev/null`), or generate random cryptographic seeds (`/dev/urandom`). |
| **`/opt`** | **Optional Software**<br>

<br>Self-contained third-party standalone application packages. | Common deployment target for custom vendor stacks, agent collectors (e.g., Datadog, Prometheus node exporter), and Google Chrome. |
| **`/tmp`** | **Temporary Files**<br>

<br>Scratchpad directory accessible by all users. | Used by scripts to hold ephemeral build artifacts; usually cleared automatically on server reboot or via background tmpwatch cleanups. |

---

## 🧭 **Absolute vs. Relative Paths**

- **📍 Absolute Path:** Always begins from the root directory (`/`). It points directly to the exact target location regardless of where your terminal currently stands.

```bash
cd /var/log/nginx
```

- **🚶 Relative Path:** Resolves relative to your **current working directory** (`pwd`). Does not begin with a leading `/`.

```bash
# Assuming current path is /var
cd log/nginx

# Reference the parent directory
cd ../etc
```

---

## 🔍 **Useful Commands for Filesystem Inspection**

### 💾 1. Check Filesystem Disk Usage (`df -h`)

Displays disk space utilization, mount points, and remaining capacity in human-readable units (MB/GB):

```bash
df -h
```

### 📊 2. Inspect Directory Disk Consumption (`du -sh`)

Calculates the actual disk space consumed by a specific folder and its nested contents:

```bash
# Check size of the log directory
sudo du -sh /var/log

# List top 10 largest folders inside /var
sudo du -h /var | sort -rh | head -n 10
```

### 🌳 3. Visualize Directory Structures (`tree`)

Renders a visual tree overview of your folder hierarchy (install via `sudo apt install tree`):

```bash
# View directory structure up to 2 levels deep
tree -L 2 /var/log
```
