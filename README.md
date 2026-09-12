# 🐧 **Linux Tutorial for Beginners | Complete DevOps Course**

Master foundational Linux skills tailored specifically for DevOps engineers and cloud practitioners. 🚀

Learn core system architecture, terminal wizardry, and real-world server administration hands-on. 💻

Build a solid foundation to automate deployments, configure servers, and supercharge your infrastructure workflows. ⚡

---

## 📜 **The Origin Story: History of Linux**

- **🗓️ September 17, 1991:** Linus Torvalds introduced the first Linux kernel release version to the computing community.
- **🔓 The Open-Source Revolution (1992):** Relicensed under the **GNU GPL (General Public License)**, transforming Linux from a private hobby project into a global, community-driven OS powerhouse. 🌐

---

## 🌐 **Getting an Online Linux Server (Hostinger VPS)**

Hands-on DevOps requires a remote, production-style virtual environment. 🏗️

Hostinger KVM VPS offers full root access, dedicated compute resources, and reliable network throughput. ⚡

Deploy an Ubuntu server in minutes to practice remote administration, firewall setups, and CI/CD operations. 🛡️

---

### 🛠️ **Step-by-Step Setup Guide**

- **🛒 1. Pick a VPS Plan:**
- Select a **KVM VPS** tier (e.g., KVM 1 or KVM 2) inside the Hostinger hPanel.
- Choose the nearest geographic data center to minimize ping and network latency. 📍

- **💿 2. Choose Operating System:**
- Select **Ubuntu 24.04 LTS** (or **22.04 LTS**) — the industry baseline for Docker, Kubernetes, and web stacks. 🐧

- **🔐 3. Configure Authentication:**
- Set a secure `root` password.
- Upload your public SSH key (`id_ed25519.pub` or `id_rsa.pub`) in hPanel for passwordless key-based login. 🔑

---

### 💻 **Connecting to Your Server**

Launch your local terminal, PowerShell, or Git Bash and connect via SSH:

- **🔑 SSH Key Login (Best Practice):**

```bash
ssh -i ~/.ssh/id_ed25519 root@<YOUR_HOSTINGER_SERVER_IP>
```

- **🔒 Password-Based Login:**

```bash
ssh root@<YOUR_HOSTINGER_SERVER_IP>
```

- **🖥️ Emergency Browser Console:**
- Use Hostinger's built-in **Browser Terminal** inside hPanel if you ever misconfigure SSH or firewall ports.

---

### ⚡ **Essential First-Run Health Checks**

Run these diagnostic commands immediately after your initial login to update repositories and inspect your server resources:

```bash
# 🔄 Update package index & apply system security patches
sudo apt update && sudo apt upgrade -y

# 🔍 Verify Linux kernel build & system architecture
uname -r

# 💾 Check disk usage across mounted partitions
df -h

# 🧠 Monitor available and used RAM (in megabytes)
free -m
```

## 📦 **Installing Linux Through VirtualBox on Windows**

Running Linux inside Oracle VM VirtualBox is the safest local sandbox to experiment without affecting Windows. 🧪

It allows you to test risky system configurations, network bridging, and bash scripts completely isolated. 🔒

Follow this local hypervisor setup to get an Ubuntu virtual machine running smoothly on your machine. 🚀

### 📥 **Prerequisites & Downloads**

- **🧰 Oracle VM VirtualBox:** Download and install the latest VirtualBox for Windows along with the Extension Pack.
- **💿 Ubuntu ISO Image:** Download the official **Ubuntu Desktop 24.04 LTS** (or Ubuntu Server) `.iso` file.
- **⚙️ Hardware Virtualization (VT-x / AMD-V):** Ensure Virtualization Technology is enabled inside your Windows Task Manager (`Performance > CPU`) or motherboard BIOS/UEFI.

### 🖥️ **Virtual Machine Configuration**

- **1. Create New VM:** Open VirtualBox, click **New**, name it `Ubuntu-DevOps`, and select the downloaded ISO image.
- **2. Allocate Resources:**
- **🧠 RAM:** Assign at least **4 GB (4096 MB)** (or 2 GB minimum for Server).
- **⚙️ CPU:** Assign at least **2 vCPUs** to keep the guest OS responsive.

- **3. Virtual Hard Disk:** Allocate a dynamically allocated virtual hard disk of **25 GB to 30 GB**.
- **4. Complete OS Installation:** Boot the VM, follow the on-screen Ubuntu installer prompts, set your username and password, and reboot when finished.

### 🔌 **Post-Install Optimizations**

- **🧩 Install Guest Additions:** From the VirtualBox menu, click **Devices > Insert Guest Additions CD image...** to unlock shared clipboards, drag-and-drop, and full-screen auto-resizing.
- **🌐 Network Setup (Bridged vs. NAT):**
- Keep **NAT** for simple outbound internet access.
- Switch to **Bridged Adapter** under `Settings > Network` if you want your local router to give your VM its own IP address on your home Wi-Fi/LAN.

## 🪟 **Installing Linux on Windows Using WSL (Windows Subsystem for Linux)**

WSL 2 delivers a genuine Linux kernel directly inside Windows without the overhead of a traditional VM. ⚡  
It bridges your Windows filesystem with Linux tools, providing near-native file read/write speeds and zero latency. 🚀  
This is the gold standard setup for developing, running Docker containers, and managing cloud servers from Windows. 💻

### ⚙️ **System Prerequisites**

- **🖥️ Windows Version:** Windows 10 (Build 19041 and higher) or Windows 11.
- **🔧 Virtualization Enabled:** Ensure **Virtual Machine Platform** is toggled on in Windows Features or enabled via your BIOS/UEFI.

### 🚀 **One-Command Installation**

Open **PowerShell** or **Windows Terminal** as **Administrator** and run:

```powershell
# 📥 Install WSL with the default Ubuntu distribution
wsl --install
```

> 💡 **Tip:** If WSL is already installed and you want a specific distro, run `wsl --list --online` to view choices, then install with `wsl --install -d Ubuntu-24.04`.

### 🔑 **Initial Configuration**

- **🔄 1. Restart Windows:** Reboot your PC when prompted to finalize virtual platform components.
- **👤 2. Set Up User Account:** Once the terminal launches automatically:
- Enter a new **UNIX username** (does not need to match your Windows username).
- Set a secure **UNIX password** (keystrokes will remain invisible while typing).

- **📌 3. Confirm WSL 2 Version:** Verify your distro runs on the modern WSL 2 architecture:

```powershell
wsl -l -v
```

### 🛠️ **Essential Post-Install Workflow**

Run standard updates and integrate directly with VS Code for a seamless development experience:

```bash
# 🔄 Update package index & system libraries
sudo apt update && sudo apt upgrade -y

# 📂 Access your Windows C: drive directly from the Linux prompt
cd /mnt/c/Users/

# 💻 Launch VS Code directly inside your WSL Linux environment
code .
```

---

## 💻 **Essential Basic Linux Commands for DevOps**

Navigating the Linux command line is the bedrock of server administration, scripting, and cloud deployments. 🧭  
These everyday commands handle file management, directory structures, content inspection, and terminal identity. 🛠️  
Mastering them directly in your shell builds the muscle memory needed for troubleshooting and automating CI/CD tasks. 🚀

### 🧭 **Navigation & Directory Traversal**

#### 📍 `pwd` (Print Working Directory)

- **What it does:** Displays the absolute path of the directory you are currently standing in.
- **DevOps Use Case:** Verifying your location before running dangerous deployment scripts or deleting files.

```bash
pwd
# Output: /home/ubuntu
```

#### 📁 `cd` (Change Directory)

- **What it does:** Moves between directories across the filesystem hierarchy.
- **DevOps Use Case:** Navigating into a cloned repository or an application deployment directory.

```bash
# Move to home directory
cd ~

# Enter a specific folder
cd myproject

# Go up one level in the folder tree
cd ..

# Go up two directory levels at once
cd ../../
```

#### 📋 `ls` (List Directory Contents)

- **What it does:** Lists files and folders contained in the specified path.
- **DevOps Use Case:** Inspecting newly extracted build artifacts or checking hidden environment variables (`.env`).

```bash
# Standard listing
ls

# Detailed view with permissions, owner, file size, and timestamp
ls -l

# Show all files including hidden dotfiles (.env, .git)
ls -la
```

---

### 📁 **File & Folder Operations**

#### 🏗️ `mkdir` (Make Directory)

- **What it does:** Creates one or more new directories.
- **DevOps Use Case:** Provisioning project workspaces and nested log or configuration directories in one pass.

```bash
# Create a single folder
mkdir myfirstwebsite

# Create nested/parent directories all at once using -p
mkdir -p my/folder/one
```

#### 📄 `touch` (Create Empty File)

- **What it does:** Creates a blank file instantly or updates the timestamp of an existing file without modifying content.
- **DevOps Use Case:** Initializing empty configuration files, log targets, or placeholder templates.

```bash
touch one.txt
```

#### 📋 `cp` (Copy Files & Directories)

- **What it does:** Duplicates files or directories from a source path to a destination path.
- **DevOps Use Case:** Creating immediate backups of configuration files before editing them on a production server.

```bash
# Copy one.txt to root directory with a new name
cp one.txt /root/chinmay.txt

# Copy an entire folder recursively using -r
cp -r myfirstwebsite /var/www/backup_website
```

---

### 📝 **Text Editing with Vim**

#### ✍️ `vim` (Visual Editor)

- **What it does:** A lightweight, terminal-based text editor found on almost every remote Linux distribution.
- **DevOps Use Case:** Updating production `.env` files, adjusting Nginx server blocks, or tweaking Dockerfiles via SSH.

```bash
vim one.txt
```

- **⚡ Core Vim Workflow:**
- **Enter Insert Mode:** Press `i` to begin writing or editing text.
- **Return to Command Mode:** Press `Esc` when you are done typing.
- **Save and Exit:** Type `:wq` (write + quit) and press `Enter`.
- **Exit Without Saving:** Type `:q!` (force quit, discard changes) and press `Enter`.

---

### 🔍 **File Inspection & System Identity**

#### 👁️ `cat` (Concatenate & Print)

- **What it does:** Outputs the entire contents of a file directly into the terminal screen.
- **DevOps Use Case:** Reading small configuration files, API keys, or quick debug scripts.

```bash
# View file content
cat chinmay.txt

# View content with line numbers for easier debugging (-n)
cat -n chinmay.txt
```

#### 📜 `less` (Paginated File Viewer)

- **What it does:** Opens large files in an interactive, scrollable terminal viewer without loading the whole file into memory.
- **DevOps Use Case:** Reading massive server access or error logs (`/var/log/nginx/access.log`) smoothly.

```bash
less chinmay.txt
```

> 💡 **Navigation in `less`:** Use `↑` / `↓` arrows or `Space` to scroll, `/search-term` to find text, and press `q` to exit.

#### 👤 `whoami` (Identify Current User)

- **What it does:** Prints the username associated with your current shell session.
- **DevOps Use Case:** Verifying whether you are operating as a standard user or have elevated to `root` before running critical commands.

```bash
whoami
# Output: root (or ubuntu)
```

## 👥 **User Management & Privilege Control**

Managing user accounts and system permissions is critical for maintaining server security and compliance. 🛡️  
Running production systems directly as `root` is dangerous, as a single mistyped command can break an OS. ⚠️  
Creating dedicated user accounts with selective `sudo` elevation enforces the principle of least privilege. 🔑

### 👤 **Creating a New User**

#### ➕ `adduser` (Interactive User Creation)

- **What it does:** Creates a new system user, sets up their personal `/home` directory, and prompts to configure their password and profile metadata.
- **DevOps Use Case:** Onboarding developers, system administrators, or CI/CD runner agents on a shared production or staging server.

```bash
sudo adduser chinmay
```

- **Interactive Terminal Prompts:**

```text
Adding user `chinmay' ...
Adding new group `chinmay' (1001) ...
Adding new user `chinmay' (1001) with group `chinmay' ...
Creating home directory `/home/chinmay' ...
Copying files from `/etc/skel' ...
New password:                      <-- Enter secure password (hidden)
Retype new password:               <-- Retype to confirm
passwd: password updated successfully
Changing the user information for chinmay
Enter the new value, or press ENTER for the default
    Full Name []: Chinmay
    Room Number []:
    Work Phone []:
    Home Phone []:
    Other []:
Is the information correct? [Y/n] Y
```

---

### 🔄 **Switching User Accounts**

#### 🔀 `su -` (Switch User with Full Environment)

- **What it does:** Switches your active terminal session to another user account. The `-` (or `-l`) flag loads that user's specific environment variables, path configurations, and home directory.
- **DevOps Use Case:** Switching from `root` into an application user or debugging deployment files inside a specific developer's workspace.

```bash
# Switch to the 'chinmay' account with login environment
su - chinmay

# Verify active account
whoami
# Output: chinmay

# Check the current directory (automatically shifts to user home)
pwd
# Output: /home/chinmay

# Return back to your previous shell/root session
exit
```

---

### 🛡️ **Granting Administrative Privileges (Sudo)**

#### ⚡ `usermod -aG sudo` (Append User to Sudoers Group)

- **What it does:** Modifies a user's account by adding them to the administrative `sudo` group (`-a` for append, `-G` for secondary group).
- **DevOps Use Case:** Giving developers root-level power for tasks like restarting services or updating packages without sharing the actual `root` password.

```bash
# Run this from an account with root privileges
sudo usermod -aG sudo chinmay
```

- **Flags Explained:**
- `-a` (**Append**): Adds the user to the specified group without removing them from their existing groups.
- `-G` (**Group**): Specifies the target supplementary group (e.g., `sudo` on Ubuntu/Debian or `wheel` on CentOS/RHEL).

- **Verifying Sudo Access:**

```bash
# Switch to user
su - chinmay

# Test administrative privileges
sudo apt update
```

## 📦 **Package Management with APT (Advanced Package Tool)**

Package managers handle installing, updating, and removing software libraries and runtime dependencies on Debian and Ubuntu systems. ⚙️  
They resolve complex dependency trees automatically, ensuring that binaries and system libraries integrate safely. 🔄  
Mastering APT workflows is essential for provisioning application stacks, web servers, and automated CI/CD runners. 🚀

### 🔄 **Updating & Upgrading Packages**

#### 📋 `sudo apt update`

- **What it does:** Downloads and synchronizes the latest package metadata from configured remote repositories (`/etc/apt/sources.list`). It checks what versions exist without modifying installed packages.
- **DevOps Use Case:** Running as the first step before installing tools to avoid downloading outdated or nonexistent package versions.

```bash
sudo apt update
```

#### ⬆️ `sudo apt upgrade`

- **What it does:** Upgrades all currently installed packages to their highest available versions based on the updated package list.
- **DevOps Use Case:** Applying the latest OS security patches, bug fixes, and library enhancements to production servers.

```bash
sudo apt upgrade -y
```

---

### 📥 **Installing Packages**

#### 🌐 `sudo apt install apache2` / `sudo apt install nginx`

- **What it does:** Fetches, unpacks, and installs software packages along with all required system dependencies.
- **DevOps Use Case:** Setting up web servers, reverse proxies, and load balancers to route incoming HTTP/HTTPS traffic.

```bash
# Install Apache Web Server
sudo apt install apache2 -y

# Install Nginx High-Performance Web Server & Reverse Proxy
sudo apt install nginx -y
```

#### 🛠️ `sudo apt install curl git python3` (Multi-Package Installation)

- **What it does:** Installs multiple software packages simultaneously in a single terminal command.
- **DevOps Use Case:** Provisioning a standard developer workstation or CI/CD build node with essential CLI tooling in one step.

```bash
sudo apt install curl git python3 -y
```

---

### 🗑️ **Uninstalling & Cleaning Up Packages**

#### ❌ `sudo apt remove apache2`

- **What it does:** Removes the application binary and runtime dependencies, but leaves user configurations and log files intact on the disk.
- **DevOps Use Case:** Temporarily taking down a service to replace it or resolve conflicts while keeping configuration files for later reuse.

```bash
sudo apt remove apache2 -y
```

#### 🧹 `sudo apt purge apache2`

- **What it does:** Performs a deep removal by deleting the application binary along with all associated configuration files in `/etc/`.
- **DevOps Use Case:** Completely wiping an obsolete or misconfigured service to start over with a fresh, clean configuration.

```bash
sudo apt purge apache2 -y
```

---

### 🔍 **Listing & Inspecting Packages**

#### 📜 `apt list --installed`

- **What it does:** Displays an exhaustive list of all software packages currently installed on the host system.
- **DevOps Use Case:** Auditing server environments, verifying software compliance, or piping into `grep` to check specific package versions.

```bash
# View all installed packages
apt list --installed

# Check if a specific package is installed
apt list --installed | grep nginx
```

## 🔐 **Groups & User Access Control**

Linux groups organize multiple users under a unified identity to simplify permission management across files and directories. 👥  
Instead of managing permissions user-by-user, you grant access to a shared team group like developers or operations. 🛡️  
This role-based access model protects sensitive system directories and fosters secure multi-user collaboration. 🚀

### 👥 **Creating Groups & Provisioning Team Members**

#### 🏢 `groupadd developers` (Create a Team Group)

- **What it does:** Registers a new user group inside `/etc/group`.
- **DevOps Use Case:** Setting up shared team roles (e.g., `developers`, `devops`, `qa`) before onboarding engineers to a shared server.

```bash
sudo groupadd developers
```

#### 👤 `useradd -m <username>` (Create User with Home Directory)

- **What it does:** Creates a new system user account. The `-m` flag explicitly creates the user's home directory (`/home/<username>`) with default shell configuration files.
- **DevOps Use Case:** Scripting user creation non-interactively during server setup or CI/CD provisioning pipelines.

```bash
# Create user accounts for team members with dedicated home folders
sudo useradd -m aman
sudo useradd -m dipak
```

#### 🔑 `passwd <username>` (Assign or Update User Password)

- **What it does:** Sets or changes the login authentication password for the specified user account.
- **DevOps Use Case:** Initializing credentials during manual user setup or resetting credentials when team members rotate.

```bash
# Set password for Aman
sudo passwd aman

# Set password for Dipak
sudo passwd dipak
```

---

### 🤝 **Assigning Users to Shared Groups**

#### 🔗 `usermod -aG developers <username>`

- **What it does:** Appends (`-a`) the user to the specified secondary group (`-G`) without removing them from their primary or other existing groups.
- **DevOps Use Case:** Granting engineers access to shared deployment folders, web directories (`/var/www/`), or Docker daemons (`docker` group).

```bash
# Add Aman and Dipak to the developers group
sudo usermod -aG developers aman
sudo usermod -aG developers dipak

# Verify group membership for a user
groups aman
# Output: aman : aman developers
```

---

### 🔍 **Inspecting Ownership & Permissions**

#### 📋 `ls -l` (Long-Format File Listing)

- **What it does:** Displays detailed metadata including file permissions, link count, owner, group, file size, and last modified timestamp.
- **DevOps Use Case:** Checking which user and group own deployment directories and diagnosing "Permission Denied" issues.

```bash
ls -l
```

- **Deciphering `ls -l` Output:**

```text
-rwxr-xr-- 1 aman developers 4096 Sep 9 10:00 app.js
┬└────┬───┘ │ └──┬┘ └───┬────┘ └──┬─┘ └────┬─────┘ └──┬──┘
│     │     │    │      │        │        │          └─ File Name
│     │     │    │      │        │        └─ Modification Date & Time
│     │     │    │      │        └─ File Size (in bytes)
│     │     │    │      └─ Owning Group (developers)
│     │     │    └─ File Owner (aman)
│     │     └─ Hard Link Count
│     └─ Permission Triplets (User: rwx, Group: r-x, Others: r--)
└─ File Type (- for file, d for directory, l for symlink)

```

---

## 🛡️ **File Ownership & Permission Management**

Linux enforces strict access control by pairing every file and directory with a designated owner and group. 🔒  
System administrators can reassign ownership and fine-tune read, write, and execute permissions at granular levels. ⚙️  
Understanding ownership commands and permission flags prevents unauthorized access and resolves runtime permission conflicts. 🚀

### 🏢 **Setting Up the Shared Workspace**

Before adjusting permissions, navigate to the target parent directory and create the folder designated for the team:

```bash
# Navigate to chinmay's directory
cd chinmay

# Create a shared team directory named 'devs'
mkdir devs
```

---

### 👤 **Managing File & Directory Ownership**

#### 🔑 `sudo chown <owner> <target>` (Change Owner)

- **What it does:** Transfers file or folder ownership to a different system user account.
- **DevOps Use Case:** Handing over newly cloned application files or Docker build outputs to the appropriate service user.

```bash
sudo chown aman devs
```

#### 👥 `sudo chgrp <group> <target>` (Change Group)

- **What it does:** Reassigns the associated primary group ownership of a file or folder.
- **DevOps Use Case:** Assigning a project directory to the `developers` group so team members can share files without permission errors.

```bash
sudo chgrp developers devs
```

> 💡 **DevOps Pro Tip:** You can set both owner and group simultaneously with a single `chown` command:
>
> ```bash
> sudo chown aman:developers devs
> ```

---

### 🎛️ **Modifying Permissions with `chmod` (Symbolic Mode)**

The `chmod` (change mode) command modifies who can read (`r`), write (`w`), or execute (`x`) files and folders.

Symbolic notation uses categories to specify which permissions to grant (`+`) or revoke (`-`):

- **`u` (User / Owner):** The account that owns the file.
- **`g` (Group):** Users belonging to the owning group.
- **`o` (Others):** Everyone else with access to the system.
- **`a` (All):** Applies to User, Group, and Others simultaneously (`u + g + o`).

#### ✍️ Modifying Access Step-by-Step

- **👥 Grant Write Access to the Group (`g+w`):**
  Allows any user inside the `developers` group to create, modify, and delete files inside `devs`.

```bash
chmod g+w devs
```

- **👤 Grant Write Access to the Owner (`u+w`):**
  Ensures the file owner (`aman`) maintains write privileges.

```bash
chmod u+w devs
```

- **🌍 Grant Write Access to Others (`o+w`):**
  Allows all other system users on the server to write to the directory _(use with caution in production!)_.

```bash
chmod o+w devs
```

- **🌐 Grant Write Access to Everyone (`a+w`):**
  Applies write permission across all three levels (owner, group, and others) simultaneously.

```bash
chmod a+w devs
```

---

### 🔍 **Verifying Updated Permissions**

Inspect the directory to confirm that the owner, group, and permission flags match the intended access policies:

```bash
ls -ld devs
# Output preview: drwxrwxrwx 2 aman developers 4096 Sep 12 10:30 devs
```

---

## ⚙️ **Process & Service Management**

Managing active background processes and system daemons is a cornerstone of Linux server administration. 🔄  
System engineers monitor compute resources to diagnose bottlenecks, hung processes, and service failures. 📊  
Using `systemd` controllers ensures production workloads like Nginx, Docker, or Node.js auto-recover and run reliably. 🚀

---

### 🔍 **Monitoring Active System Processes**

#### 📋 `ps` (Process Status Snapshot)

- **What it does:** Displays an instant snapshot of processes currently running in your active shell terminal session.
- **DevOps Use Case:** Quick sanity checks to see your active bash commands or shell subprocesses.

```bash
ps
```

#### 🌐 `ps aux` (Exhaustive System-Wide Process List)

- **What it does:** Lists every running process across the entire operating system, regardless of which user owns it.
- **DevOps Use Case:** Auditing PID (Process ID) numbers, user execution contexts, CPU percentages, and RAM consumption.

```bash
ps aux
```

- **Deciphering the Flags:**
- `a`: Shows processes running for all users.
- `u`: Displays detailed user-oriented information (owner, `%CPU`, `%MEM`).
- `x`: Includes processes running in the background without an attached terminal session (daemons).

#### 🎯 `ps aux | grep nginx` (Process Filtering)

- **What it does:** Pipes the full process table into `grep` to isolate only records matching a specific application name.
- **DevOps Use Case:** Confirming whether web server workers, database instances, or microservice listeners are live and retrieving their PIDs.

```bash
ps aux | grep nginx

```

#### 📊 `top` (Real-Time System & Resource Dashboard)

- **What it does:** Opens an interactive, auto-refreshing monitor showing overall CPU load, memory utilization, and top resource-draining processes.
- **DevOps Use Case:** Identifying memory leaks, rogue infinite loops, or CPU spikes during production traffic surges.

```bash
top
```

> 💡 **Navigation in `top`:** Press `M` to sort by Memory usage, `P` to sort by CPU usage, `k` to kill a PID interactively, and `q` to exit.

---

### 🎛️ **Service Orchestration with `systemctl**`

Ubuntu uses `systemd` as its default initialization system to manage daemon lifecycles and background services.

#### 🩺 Inspecting & Modifying Service States

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

### 🔁 **Boot-Time Lifecycle Configuration**

Configure which services should automatically spin up whenever the virtual machine or cloud server reboots.

#### 🟢 `sudo systemctl enable nginx` (Auto-Start on Boot)

- **What it does:** Creates a symlink inside the systemd startup directory targets, ensuring Nginx boots up automatically on system start.
- **DevOps Use Case:** Guaranteeing web servers and background queue workers recover immediately after an unexpected server reboot or kernel patch.

```bash
sudo systemctl enable nginx
```

#### 🔴 `sudo systemctl disable nginx` (Prevent Auto-Start)

- **What it does:** Removes the systemd startup symlink so the service stays dormant until manually invoked.
- **DevOps Use Case:** Decommissioning secondary or staging services so they do not consume server memory after reboots.

```bash
sudo systemctl disable nginx
```

---

## 🌐 **Environment Variables, PATH, & `.bashrc`**

Environment variables define the operating environment and behavioral defaults for shells, scripts, and applications. ⚙️
System utilities and CI/CD jobs rely on dynamic variables like `$PATH` to discover where executable programs reside. 🔍
Persisting custom paths and global flags inside configuration files like `.bashrc` streamlines recurring automation workflows. 🚀

---

### 🔍 **Inspecting Environment Variables**

#### 🏠 `echo $HOME` (Check User Home Path)

- **What it does:** Prints the absolute filesystem path of the current user's personal home directory.
- **DevOps Use Case:** Writing robust, non-hardcoded backup and configuration scripts that adapt across different environments.

```bash
echo $HOME
# Output: /home/chinmay
```

#### 📋 `printenv` (List Global Environment Variables)

- **What it does:** Dumps every active exported environment variable configured in your current session.
- **DevOps Use Case:** Auditing runtime variables, locale configs, and container environment keys during server troubleshooting.

```bash
# Print all environment variables
printenv

# Filter for a specific variable
printenv USER
```

#### 🛣️ `echo $PATH` (View Executable Lookup Directories)

- **What it does:** Displays a colon-separated (`:`) list of directories where Linux looks for executable binaries when you run commands.
- **DevOps Use Case:** Diagnosing "command not found" errors when newly installed runtimes like Node.js, Go, or custom tools fail to launch.

```bash
echo $PATH
# Output: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

---

### 🏷️ **Shell Variables vs. Exported Environment Variables**

#### 💬 Local Shell Variable

- **What it does:** Creates a temporary variable accessible **only** within the active terminal prompt; child processes cannot see it.

```bash
name="Chinmay"
echo $name
# Output: Chinmay
```

#### 🌍 Global Environment Variable (`export`)

- **What it does:** Uses `export` to make the variable available to child shells, spawned processes, and executing scripts.
- **DevOps Use Case:** Supplying database URLs, runtime environments (`NODE_ENV=production`), or API keys to applications.

```bash
export friend="Aman"
echo $friend
# Output: Aman
```

---

### 📜 **Writing & Executing a Custom Bash Script**

#### ✍️ 1. Create the Script File

Create a new script file using Vim:

```bash
vim chinmay.sh
```

Add your bash code inside:

```bash
echo "Hello Chinmay";
```

- Press `Esc`, type `:wq`, and press `Enter` to save and exit.

#### ⚡ 2. Grant Execute Permissions

By default, new files lack execution rights. Add execute permission (`+x`):

```bash
chmod +x chinmay.sh
```

#### 🚚 3. Organize Into the Workspace

Move the executable script into your team folder:

```bash
# Move chinmay.sh inside the devs folder
mv chinmay.sh devs/
```

---

### 🛣️ **Extending the System `$PATH**`

#### ➕ `export PATH="$PATH:/home/chinmay/devs"`

- **What it does:** Appends a custom directory to the existing `$PATH` lookup list.
- **DevOps Use Case:** Enabling custom scripts and internal CLI tools to be executed globally from any directory without typing their full paths (`./script.sh`).

```bash
# Append custom directory to active PATH
export PATH="$PATH:/home/chinmay/devs"

# Run the script directly from any location!
chinmay.sh
# Output: Hello Chinmay
```

---

### 💾 **Making Variables & Paths Permanent via `.bashrc**`

Variables set in an active terminal session disappear when the session closes. Storing them in `~/.bashrc` ensures they load automatically every time an interactive bash shell opens.

#### 🕵️ 1. View Hidden Files

```bash
# List all files sorted by modification time, oldest to newest (-lart)
ls -lart
```

#### 📝 2. Edit `.bashrc`

Open the user's `.bashrc` file in Vim:

```bash
vim ~/.bashrc
```

Scroll to the very bottom, press `i` to enter Insert Mode, and append your persistent settings:

```bash
# Custom Developer Configurations
export friend="Aman"
export PATH="$PATH:/home/chinmay/devs"
```

Save and quit by pressing `Esc`, typing `:wq`, and hitting `Enter`.

#### 🔄 3. Reload Shell Configuration (`source`)

- **What it does:** Forces the active bash session to re-read and apply updates from `.bashrc` without needing to log out or reboot.

```bash
source ~/.bashrc
```

---

## 🗜️ **Archives & Compression**

Compressing and archiving files is vital for managing backups, transferring artifacts, and saving storage space. 📦
Archiving combines multiple files into a single bundle, while compression shrinks file sizes for faster network transfer. ⚡
Tools like `tar`, `gzip`, and `zip` form the backbone of backup strategies and artifact deployment in DevOps workflows. 🚀

---

### 📂 **Setting Up a Sample Project Structure**

Create a mock Python application directory with code files, templates, and logs to practice packaging:

```bash
# Create main project directory
mkdir python-projects
cd python-projects

# Create application subdirectories
mkdir static templates

# Generate empty project files
touch log.log main.py utils.py

# Navigate back to parent directory
cd ..
```

---

### 📦 **Archiving with `tar` (Tape Archive)**

`tar` bundles multiple files and directories into a single archive file (often called a tarball) without compressing by default.

#### 🗃️ 1. Create an Archive (`-cf`)

- **What it does:** Creates (`-c`) an archive file (`-f`) named `python.tar` containing the specified directory.
- **DevOps Use Case:** Grouping complex project folders and build outputs before archiving or moving them.

```bash
tar -cf python.tar python-projects/
```

#### 🗑️ 2. Simulate Clean State

Remove the uncompressed directory to test restoration:

```bash
rm -rf python-projects/
```

#### 🔍 3. Inspect Archive Contents (`-tf`)

- **What it does:** Lists or tests (`-t`) the contents of the archive file (`-f`) without unpacking it to disk.
- **DevOps Use Case:** Auditing backup bundles to verify essential files are present before restoring them.

```bash
tar -tf python.tar
```

#### 📤 4. Extract the Archive (`-xf` & `-xvf`)

- **What it does:** Extracts (`-x`) the files from the archive file (`-f`). Adding `-v` (**verbose**) prints each file as it unpacks.
- **DevOps Use Case:** Restoring backups or unbundling deployed code packages on target servers.

```bash
# Silent extraction
tar -xf python.tar

# Verbose extraction (shows files being unpacked)
tar -xvf python.tar
```

---

### 🗜️ **File Compression with `gzip` & `gunzip**`

`gzip` compresses single files using the DEFLATE algorithm, creating a `.gz` file.

#### 📉 1. Compress an Archive (`gzip`)

- **What it does:** Compresses `python.tar` into `python.tar.gz` and replaces the original uncompressed file.
- **DevOps Use Case:** Reducing large database dumps or log bundles before uploading them to cloud object storage (e.g., AWS S3).

```bash
gzip python.tar
# Creates: python.tar.gz (original python.tar is compressed)
```

#### 📈 2. Decompress an Archive (`gunzip`)

- **What it does:** Decompresses `.gz` files back to their uncompressed format.
- **DevOps Use Case:** Decompressing downloaded database snapshots or server backups for inspection.

```bash
gunzip python.tar.gz
# Restores: python.tar
```

> 💡 **DevOps Pro Tip:** You can create a compressed `.tar.gz` archive in a single command using the `-z` flag:
>
> ```bash
> tar -czvf python.tar.gz python-projects/
> ```

---

### 🤐 **Cross-Platform Archiving with `zip` & `unzip**`

`zip` simultaneously archives and compresses files, making it universally compatible across Linux, macOS, and Windows environments.

#### 🗜️ 1. Compress a Directory (`zip -r`)

- **What it does:** Recursively (`-r`) compresses an entire folder structure into a `.zip` file.
- **DevOps Use Case:** Packaging AWS Lambda deployment zips or sending compressed artifacts across cross-platform teams.

```bash
# Install zip utility if not present
sudo apt install zip unzip -y

# Recursively zip the directory
zip -r python.zip python-projects/
```

#### 📂 2. Decompress with `unzip`

- **What it does:** Extracts all packaged files and restores directory hierarchies from a `.zip` archive.
- **DevOps Use Case:** Unpacking software releases, theme bundles, or application assets.

```bash
unzip python.zip
```


---

## ⏰ **Scheduled Tasks & Automation with Cron Jobs**

Automating recurring scripts and periodic housekeeping tasks is essential for stable production environments. ⏱️  
The Linux `cron` daemon runs scheduled commands in the background at specific intervals, dates, and times. 🤖  
From running scheduled database backups to executing maintenance scripts, mastering `cron` is a core DevOps skill. 🚀

---

### 📋 **Inspecting & Managing Cron Tables**

Each user maintains their own dedicated cron schedule file managed through the `crontab` utility.

#### 👁️ `crontab -l` (List Scheduled Jobs)
* **What it does:** Displays all active cron jobs scheduled under the current user account.
* **DevOps Use Case:** Auditing existing scheduled jobs before deploying new automation scripts.
```bash
crontab -l
```

#### ✏️ `crontab -e` (Edit Scheduled Jobs)

* **What it does:** Opens the user's crontab schedule inside an interactive terminal editor.
* **Selecting Your Preferred Editor:**
On the first execution, Linux prompts you to select a default text editor:
```text
Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <-- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny

Choose 1-3 [1]: 2
```


Type `2` and hit `Enter` to set **Vim** as your default editor.

---

### 🐍 **Creating a Sample Python Automation Script**

Prepare a simple script that logs timestamps to verify that your scheduled cron job triggers reliably.

#### ✍️ 1. Write the Script (`main.py`)

Create the script using Vim:

```bash
vim main.py
```

Paste the following Python code:

```python
from datetime import datetime

# Append the current timestamp to time.txt
with open("/home/chinmay/time.txt", "a") as f:
    f.write(f"Cron executed successfully at: {datetime.now()}\n")
```

Press `Esc`, type `:wq`, and hit `Enter`.

#### 🧪 2. Test Execution & Clean Up

Run the script manually to confirm it writes to the destination file:

```bash
# Execute the script
python3 main.py

# Verify that time.txt was created and populated
cat time.txt

# Remove the test file before scheduling the cron job
rm time.txt
```

---

### 🧠 **Crontab Syntax & Crontab Guru Guide**

Every scheduled cron entry follows a five-field time specification followed by the absolute executable command:

```text
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of the month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday)
│ │ │ │ │
* * * * * <command-to-execute>
```

#### 🎯 Special Operator Cheatsheet

* `*` (**Wildcard / Every**): Runs on every matching value (e.g., `*` in the minute field runs every minute).
* `,` (**Value List**): Specifies distinct execution intervals (e.g., `15,45` runs at minute 15 and minute 45).
* `-` (**Range**): Defines an inclusive range (e.g., `1-5` in day-of-week runs Monday through Friday).
* `/` (**Step Value**): Specifies incremental intervals (e.g., `*/10` in minute runs every 10 minutes).

> 💡 **DevOps Tip:** Use **[crontab.guru](https://crontab.guru)** to test, validate, and human-read any complex cron expression before pushing it to production!

#### 🚀 Common Real-World Cron Examples

| Expression | Schedule Description |
| --- | --- |
| `* * * * *` | Every single minute |
| `*/5 * * * *` | Every 5 minutes |
| `0 * * * *` | Every hour on the hour |
| `0 2 * * *` | Daily at 2:00 AM (Ideal for nightly backups) |
| `0 0 * * 0` | Weekly on Sunday at midnight |

---

### ⚙️ **Configuring the Cron Job**

Always use **absolute paths** for both the runtime interpreter (`/usr/bin/python3`) and the script target (`/home/chinmay/main.py`), because cron runs in a minimal environment without user-defined `$PATH` entries.

#### ➕ 1. Add the Scheduled Entry

Open the schedule editor:

```bash
crontab -e
```

Add the following line to the bottom:

```cron
* * * * * /usr/bin/python3 /home/chinmay/main.py
```

Save and exit (`Esc` -> `:wq` -> `Enter`).

#### 🔍 2. Verify Active Configuration

Confirm the schedule has been updated:

```bash
crontab -l
```

#### 📊 3. Monitor Automatic Execution

Watch the log file populate automatically each minute:

```bash
cat /home/chinmay/time.txt
```


---

## 🗂️ **Understanding the Linux Filesystem (FHS)**

Unlike Windows, which organizes storage across distinct drive letters (`C:\`, `D:\`), Linux unifies everything under a single hierarchical tree structure. 🌳  
This layout adheres strictly to the **Filesystem Hierarchy Standard (FHS)**, ensuring predictable file locations across distributions. 📐  
In Linux, the core philosophy holds true: *"Everything is a file"* — including hardware devices, processes, and network sockets. ⚙️

---

### 🌳 **The Root Directory (`/`) & Core Hierarchy**

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

### 📂 **Directory Breakdown & DevOps Relevance**

| Directory | Full Name & Purpose | DevOps Real-World Relevance |
| --- | --- | --- |
| **`/etc`** | **Editable Text Configurations**<br>

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

### 🧭 **Absolute vs. Relative Paths**

* **📍 Absolute Path:** Always begins from the root directory (`/`). It points directly to the exact target location regardless of where your terminal currently stands.
```bash
cd /var/log/nginx
```


* **🚶 Relative Path:** Resolves relative to your **current working directory** (`pwd`). Does not begin with a leading `/`.
```bash
# Assuming current path is /var
cd log/nginx

# Reference the parent directory
cd ../etc
```



---

### 🔍 **Useful Commands for Filesystem Inspection**

#### 💾 1. Check Filesystem Disk Usage (`df -h`)

Displays disk space utilization, mount points, and remaining capacity in human-readable units (MB/GB):

```bash
df -h
```

#### 📊 2. Inspect Directory Disk Consumption (`du -sh`)

Calculates the actual disk space consumed by a specific folder and its nested contents:

```bash
# Check size of the log directory
sudo du -sh /var/log

# List top 10 largest folders inside /var
sudo du -h /var | sort -rh | head -n 10
```

#### 🌳 3. Visualize Directory Structures (`tree`)

Renders a visual tree overview of your folder hierarchy (install via `sudo apt install tree`):

```bash
# View directory structure up to 2 levels deep
tree -L 2 /var/log
```

---

## 🌐 **Understanding Nginx (Web Server & Reverse Proxy)**

Nginx (pronounced *engine-x*) is an open-source, high-performance HTTP server, reverse proxy, and load balancer. 🚀  
Its asynchronous, event-driven architecture handles thousands of concurrent client connections with minimal RAM and CPU overhead. ⚡  
In modern DevOps workflows, Nginx acts as the front-facing gateway routing external traffic into internal microservices and web apps. 🛡️

---

### 📦 **Installing & Verifying Nginx**

Install Nginx on Ubuntu using the standard `apt` package manager:

#### 🔄 1. Refresh Package Indexes
Synchronize the local package index with upstream repositories to pull the latest stable build:
```bash
sudo apt update
```

#### 📥 2. Install the Nginx Package

Download and install the Nginx server daemon along with its standard modules:

```bash
sudo apt install nginx -y

```

#### 🩺 3. Check Service Health

Verify that the Nginx daemon initialized correctly and is actively listening for incoming HTTP traffic:

```bash
sudo systemctl status nginx
```

> 💡 Look for `Active: active (running)` in green. You can press `q` to exit the status view.

---

### 📂 **Web Root: Navigating `/var/www**`

In the Linux Filesystem Hierarchy (FHS), `/var/www` serves as the standard directory designated for public-facing web data.

```bash
# Navigate to the web hosting directory
cd /var/www

# List contents
ls -la
```

* Inside `/var/www/html`, you will find the default `index.nginx-debian.html` landing page.
* You can test your setup by opening your server's public IP address (`http://<YOUR_SERVER_IP>`) in any browser to see the default *"Welcome to nginx!"* page. 🌐

---

### 🗺️ **Core Architecture & Configuration Paths**

| Path | Purpose & DevOps Functionality |
| --- | --- |
| **`/etc/nginx/nginx.conf`** | The master global configuration file defining worker processes, events, timeouts, and logging formats. |
| **`/etc/nginx/sites-available/`** | Contains individual server block (virtual host) configurations for each website or reverse-proxy application. |
| **`/etc/nginx/sites-enabled/`** | Contains active symbolic links pointing back to files in `sites-available/`. Only files linked here are served. |
| **`/var/www/`** | Standard location where static application assets (HTML, CSS, React/Vue build outputs) are hosted. |
| **`/var/log/nginx/`** | Houses runtime logs: `access.log` (incoming HTTP requests) and `error.log` (crashes and routing failures). |

---

### 🔀 **Common DevOps Use Cases for Nginx**

* **Static Site Hosting:** Serves HTML, CSS, JavaScript, and images directly off the disk with high caching efficiency. 📄
* **Reverse Proxy:** Accepts external HTTP/HTTPS requests on port 80/443 and passes them to internal backend services (Node.js, Python Flask/FastAPI, Go) running on private ports like `3000` or `8000`. 🔁
* **Load Balancing:** Distributes incoming web traffic across multiple backend application instances using algorithms like Round Robin or Least Connections. ⚖️
* **SSL/TLS Termination:** Offloads HTTPS decryption/encryption duties at the gateway using Let's Encrypt certificates before forwarding plain traffic internally. 🔒

---

### 🧪 **Quick Configuration Test & Reload**

Whenever you update Nginx server blocks, always validate syntax before restarting the daemon to prevent downtime:

```bash
# 🔍 1. Test configuration files for syntax errors
sudo nginx -t

# ⚡ 2. Reload configurations without dropping active client connections
sudo systemctl reload nginx
```


