# 👥 **User Management & Privilege Control**

Managing user accounts and system permissions is critical for maintaining server security and compliance. 🛡️  
Running production systems directly as `root` is dangerous, as a single mistyped command can break an OS. ⚠️  
Creating dedicated user accounts with selective `sudo` elevation enforces the principle of least privilege. 🔑

---

## 👤 **Creating a New User**

### ➕ `adduser` (Interactive User Creation)

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

## 🔄 **Switching User Accounts**

### 🔀 `su -` (Switch User with Full Environment)

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

## 🛡️ **Granting Administrative Privileges (Sudo)**

### ⚡ `usermod -aG sudo` (Append User to Sudoers Group)

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
