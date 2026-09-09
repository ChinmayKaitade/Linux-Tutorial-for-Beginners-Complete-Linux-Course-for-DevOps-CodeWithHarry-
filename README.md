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
