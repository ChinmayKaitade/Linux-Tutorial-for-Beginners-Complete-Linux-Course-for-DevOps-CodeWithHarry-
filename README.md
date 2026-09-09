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
