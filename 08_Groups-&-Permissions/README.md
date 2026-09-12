# 🔐 **Groups & User Access Control**

Linux groups organize multiple users under a unified identity to simplify permission management across files and directories. 👥  
Instead of managing permissions user-by-user, you grant access to a shared team group like developers or operations. 🛡️  
This role-based access model protects sensitive system directories and fosters secure multi-user collaboration. 🚀

---

## 👥 **Creating Groups & Provisioning Team Members**

### 🏢 `groupadd developers` (Create a Team Group)

- **What it does:** Registers a new user group inside `/etc/group`.
- **DevOps Use Case:** Setting up shared team roles (e.g., `developers`, `devops`, `qa`) before onboarding engineers to a shared server.

```bash
sudo groupadd developers
```

### 👤 `useradd -m <username>` (Create User with Home Directory)

- **What it does:** Creates a new system user account. The `-m` flag explicitly creates the user's home directory (`/home/<username>`) with default shell configuration files.
- **DevOps Use Case:** Scripting user creation non-interactively during server setup or CI/CD provisioning pipelines.

```bash
# Create user accounts for team members with dedicated home folders
sudo useradd -m aman
sudo useradd -m dipak
```

### 🔑 `passwd <username>` (Assign or Update User Password)

- **What it does:** Sets or changes the login authentication password for the specified user account.
- **DevOps Use Case:** Initializing credentials during manual user setup or resetting credentials when team members rotate.

```bash
# Set password for Aman
sudo passwd aman

# Set password for Dipak
sudo passwd dipak
```

---

## 🤝 **Assigning Users to Shared Groups**

### 🔗 `usermod -aG developers <username>`

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

## 🔍 **Inspecting Ownership & Permissions**

### 📋 `ls -l` (Long-Format File Listing)

- **What it does:** Displays detailed metadata including file permissions, link count, owner, group, file size, and last modified timestamp.
- **DevOps Use Case:** Checking which user and group own deployment directories and diagnosing "Permission Denied" issues.

```bash
ls -l
```

- **Deciphering `ls -l` Output:**

```text
-rwxr-xr-- 1 aman developers 4096 Sep 9 10:00 app.js
┬└────┬───┘ │ └──┬┘ └───┬────┘ └──┬─┘ └────┬─────┘ └──┬──┘
│     │     │    │      │         │        │          └─ File Name
│     │     │    │      │         │        └─ Modification Date & Time
│     │     │    │      │         └─ File Size (in bytes)
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

## 👤 **Managing File & Directory Ownership**

### 🔑 `sudo chown <owner> <target>` (Change Owner)

- **What it does:** Transfers file or folder ownership to a different system user account.
- **DevOps Use Case:** Handing over newly cloned application files or Docker build outputs to the appropriate service user.

```bash
sudo chown aman devs
```

### 👥 `sudo chgrp <group> <target>` (Change Group)

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

## 🎛️ **Modifying Permissions with `chmod` (Symbolic Mode)**

The `chmod` (change mode) command modifies who can read (`r`), write (`w`), or execute (`x`) files and folders.

Symbolic notation uses categories to specify which permissions to grant (`+`) or revoke (`-`):

- **`u` (User / Owner):** The account that owns the file.
- **`g` (Group):** Users belonging to the owning group.
- **`o` (Others):** Everyone else with access to the system.
- **`a` (All):** Applies to User, Group, and Others simultaneously (`u + g + o`).

### ✍️ Modifying Access Step-by-Step

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

## 🔍 **Verifying Updated Permissions**

Inspect the directory to confirm that the owner, group, and permission flags match the intended access policies:

```bash
ls -ld devs
# Output preview: drwxrwxrwx 2 aman developers 4096 Sep 12 10:30 devs
```
