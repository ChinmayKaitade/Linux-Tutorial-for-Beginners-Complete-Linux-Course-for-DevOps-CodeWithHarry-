# 🪟 **Installing Linux on Windows Using WSL (Windows Subsystem for Linux)**

WSL 2 delivers a genuine Linux kernel directly inside Windows without the overhead of a traditional VM. ⚡  
It bridges your Windows filesystem with Linux tools, providing near-native file read/write speeds and zero latency. 🚀  
This is the gold standard setup for developing, running Docker containers, and managing cloud servers from Windows. 💻

---

## ⚙️ **System Prerequisites**

- **🖥️ Windows Version:** Windows 10 (Build 19041 and higher) or Windows 11.
- **🔧 Virtualization Enabled:** Ensure **Virtual Machine Platform** is toggled on in Windows Features or enabled via your BIOS/UEFI.

---

## 🚀 **One-Command Installation**

Open **PowerShell** or **Windows Terminal** as **Administrator** and run:

```powershell
# 📥 Install WSL with the default Ubuntu distribution
wsl --install
```

> 💡 **Tip:** If WSL is already installed and you want a specific distro, run `wsl --list --online` to view choices, then install with `wsl --install -d Ubuntu-24.04`.

---

## 🔑 **Initial Configuration**

- **🔄 1. Restart Windows:** Reboot your PC when prompted to finalize virtual platform components.
- **👤 2. Set Up User Account:** Once the terminal launches automatically:
- Enter a new **UNIX username** (does not need to match your Windows username).
- Set a secure **UNIX password** (keystrokes will remain invisible while typing).

- **📌 3. Confirm WSL 2 Version:** Verify your distro runs on the modern WSL 2 architecture:

```powershell
wsl -l -v
```

---

## 🛠️ **Essential Post-Install Workflow**

Run standard updates and integrate directly with VS Code for a seamless development experience:

```bash
# 🔄 Update package index & system libraries
sudo apt update && sudo apt upgrade -y

# 📂 Access your Windows C: drive directly from the Linux prompt
cd /mnt/c/Users/

# 💻 Launch VS Code directly inside your WSL Linux environment
code .
```
