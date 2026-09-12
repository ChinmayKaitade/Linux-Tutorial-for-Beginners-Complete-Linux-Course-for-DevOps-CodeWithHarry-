# 🐧 Linux Tutorial for Beginners

### 🚀 Complete Linux Course for DevOps & Cloud Engineers

A comprehensive, zero-to-production guide designed to take you from foundational shell navigation to real-world server orchestration, process automation, and web server deployment.

[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](#)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](#)
[![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)](#)
[![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](#)

[📺 Watch Video Tutorial](https://youtube.com) • [📝 Course Notes & Cheatsheets](./linux_handbook.pdf) • [⭐ Star This Repo](https://github.com/ChinmayKaitade/Linux-Tutorial-for-Beginners-Complete-Linux-Course-for-DevOps-CodeWithHarry-)

---

## 📌 Table of Contents

- [🎯 What You Will Learn](#-what-you-will-learn)
- [🗺️ Course Curriculum & Modules](#️-course-curriculum--modules)
- [🛠️ Essential Prerequisites](#️-essential-prerequisites)
- [⚡ Quick Start: Clone & Setup](#-quick-start-clone--setup)
- [📚 Additional Resources & Cheatsheets](#-additional-resources--cheatsheets)
- [⭐ Support & Community](#-support--community)
- [📄 License](./LICENSE)

---

## 🎯 What You Will Learn

- **🖥️ System Administration:** Remote cloud VPS configuration, virtual machines (VirtualBox), and WSL 2 development setups.
- **⚡ Terminal Fluency:** Everyday filesystem navigation, text manipulation in Vim, and piping utilities (`grep`, `cat`, `less`).
- **🛡️ Security & Access Control:** Multi-user isolation, least-privilege administrative elevation (`sudo`), file ownership (`chown`), and permissions (`chmod`).
- **🔄 Service Orchestration:** Managing system daemons (`systemd`), monitoring real-time telemetry (`top`, `ps aux`), and inspecting logs.
- **🤖 Workload Automation:** Bash shell scripting, `$PATH` customization, persistent profiles (`.bashrc`), and scheduled cron jobs.
- **🌐 Web Infrastructure:** Deploying and configuring Nginx web servers, reverse proxy routing, and encrypted SFTP file transfers.

---

## 🗺️ Course Curriculum & Modules

|  Step  | Topic & Module Folder                                                                                              | Core Focus & Hands-on Concepts                                                                        |
| :----: | :----------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------- |
| **01** | [📜 History of Linux](./01_History-of-Linux/README.md)                                                             | Linus Torvalds, open-source revolution, and GNU GPL foundations.                                      |
| **02** | [🌐 Getting an Online Linux Server](./02_Getting-an-online-Linux-Server/README.md)                                 | Hostinger KVM VPS deployment, SSH key setup, and system diagnostics.                                  |
| **03** | [📦 Installing Linux Through VirtualBox on Windows](./03_Installing-Linux-through-VirtualBox-on-Windows/README.md) | Local VM sandboxing, resource allocation, and bridged networking.                                     |
| **04** | [🪟 Installing Linux on Windows Using WSL](./04_Installing-Linux-on-Windows-using-WSL/README.md)                   | Native Linux kernel on Windows, cross-filesystem access, and VS Code.                                 |
| **05** | [💻 Basic Linux Commands](./05_Basic-Linux-Commands/README.md)                                                     | Filesystem traversal (`pwd`, `cd`, `ls`), file ops, Vim editing, and `whoami`.                        |
| **06** | [👤 User Management & Privilege Control](./06_Creating-Users/README.md)                                            | User creation (`adduser`, `useradd`), switching shells (`su -`), and `sudo` administrative elevation. |
| **07** | [📦 Package Management](./07_Package-Management/README.md)                                                         | Repository updates, upgrading, installing stacks, and clean purging via APT.                          |
| **08** | [🔐 Groups & Permissions](./08_Groups-&-Permissions/README.md)                                                     | Role-based groups (`groupadd`, `usermod`), file ownership (`chown`), and symbolic modes (`chmod`).    |
| **09** | [⚙️ Processes & Services](./09_Processes-&-Services/README.md)                                                     | Process monitoring (`ps aux`, `top`), background jobs, and `systemctl` lifecycle actions.             |
| **10** | [🌐 Environment Variables, Path and bashrc](./10_Environment-variables-path-and-bashrc/README.md)                  | Shell vs. exported variables, extending `$PATH`, scripts, and `.bashrc`.                              |
| **11** | [🗜️ Archives & Compression](./11_Archives-&-Compression/README.md)                                                 | Bundling tarballs (`tar`), compression (`gzip`), and cross-platform `.zip`.                           |
| **12** | [⏰ Cronjobs](./12_CronJobs/README.md)                                                                             | Background automation, crontab syntax, interval debugging, and logging.                               |
| **13** | [🗂️ Understanding Linux Filesystem](./13_Understanding-Linux-Filesystem/README.md)                                 | The root tree (`/etc`, `/var`, `/proc`), disk audits (`df -h`, `du -sh`), and paths.                  |
| **14** | [🌐 Understanding Nginx](./14_Understanding-Nginx/README.md)                                                       | Web server setup, reverse proxy roles, configuration structure, and reloads.                          |
| **15** | [📁 Using FileZilla To Transfer Files](./15_Using-Filezilla-to-transfer-Files/README.md)                           | Secure remote file sync over SSH/SFTP, permission debugging, and key authentication.                  |

---

## 🛠️ Essential Prerequisites

- A workstation running Windows 10/11, macOS, or Linux.
- A terminal emulator (Windows Terminal, PowerShell, or standard bash/zsh prompt).
- _(Optional)_ A remote VPS instance (Hostinger, AWS, DigitalOcean) for real-world server exercises.

---

## ⚡ Quick Start: Clone & Setup

```bash
# 1. Clone this repository
git clone [https://github.com/](https://github.com/)<YOUR_USERNAME>/linux-devops-course.git

# 2. Navigate into the course directory
cd linux-devops-course

# 3. Explore any module (e.g., Basic Commands)
cd 05-basic-linux-commands
cat README.md
```

---

## 📚 Additional Resources & Cheatsheets

- 📺 **Full Video Course Walkthrough:** [YouTube Linux DevOps Playlist](https://youtube.com)
- 📝 **Interactive Notion Study Notes:** [DevOps Linux Study Guide](https://notion.so)
- ⏰ **Crontab Visualizer:** [Crontab.guru](https://crontab.guru)
- 🐧 **Linux Man Pages Online:** [man7.org](https://man7.org/linux/man-pages/)

---

## ⭐ Support & Community

- ⭐ **Star this repository** to help other engineers discover it.
- 🍴 **Fork it** to maintain your personal reference and experiment hands-on.
- 🐛 **Open an Issue** to report corrections, typos, or request additional modules.
- 📢 **Share with peers** learning DevOps, Linux systems administration, and cloud engineering.

---

## 📄 License

This repository is distributed under the **MIT License**. You are free to adapt, modify, and distribute the contents for personal and educational use.

---

_Built with ❤️ for aspiring DevOps Engineers and Cloud Practitioners._
