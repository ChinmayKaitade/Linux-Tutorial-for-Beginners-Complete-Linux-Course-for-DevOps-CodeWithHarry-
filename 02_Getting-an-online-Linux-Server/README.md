# 🌐 **Getting an Online Linux Server (Hostinger VPS)**

Hands-on DevOps requires a remote, production-style virtual environment. 🏗️

Hostinger KVM VPS offers full root access, dedicated compute resources, and reliable network throughput. ⚡

Deploy an Ubuntu server in minutes to practice remote administration, firewall setups, and CI/CD operations. 🛡️

---

## 🛠️ **Step-by-Step Setup Guide**

- **🛒 1. Pick a VPS Plan:**
  - Select a **KVM VPS** tier (e.g., KVM 1 or KVM 2) inside the Hostinger hPanel.
  - Choose the nearest geographic data center to minimize ping and network latency. 📍

- **💿 2. Choose Operating System:**
  - Select **Ubuntu 24.04 LTS** (or **22.04 LTS**) — the industry baseline for Docker, Kubernetes, and web stacks. 🐧

- **🔐 3. Configure Authentication:**
  - Set a secure `root` password.
  - Upload your public SSH key (`id_ed25519.pub` or `id_rsa.pub`) in hPanel for passwordless key-based login. 🔑

---

## 💻 **Connecting to Your Server**

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

## ⚡ **Essential First-Run Health Checks**

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
