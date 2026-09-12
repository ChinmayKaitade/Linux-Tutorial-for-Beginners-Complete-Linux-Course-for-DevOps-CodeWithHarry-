# 💻 **Essential Basic Linux Commands for DevOps**

Navigating the Linux command line is the bedrock of server administration, scripting, and cloud deployments. 🧭  
These everyday commands handle file management, directory structures, content inspection, and terminal identity. 🛠️  
Mastering them directly in your shell builds the muscle memory needed for troubleshooting and automating CI/CD tasks. 🚀

---

## 🧭 **Navigation & Directory Traversal**

### 📍 `pwd` (Print Working Directory)

- **What it does:** Displays the absolute path of the directory you are currently standing in.
- **DevOps Use Case:** Verifying your location before running dangerous deployment scripts or deleting files.

```bash
pwd
# Output: /home/ubuntu
```

### 📁 `cd` (Change Directory)

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

### 📋 `ls` (List Directory Contents)

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

## 📁 **File & Folder Operations**

### 🏗️ `mkdir` (Make Directory)

- **What it does:** Creates one or more new directories.
- **DevOps Use Case:** Provisioning project workspaces and nested log or configuration directories in one pass.

```bash
# Create a single folder
mkdir myfirstwebsite

# Create nested/parent directories all at once using -p
mkdir -p my/folder/one
```

### 📄 `touch` (Create Empty File)

- **What it does:** Creates a blank file instantly or updates the timestamp of an existing file without modifying content.
- **DevOps Use Case:** Initializing empty configuration files, log targets, or placeholder templates.

```bash
touch one.txt
```

### 📋 `cp` (Copy Files & Directories)

- **What it does:** Duplicates files or directories from a source path to a destination path.
- **DevOps Use Case:** Creating immediate backups of configuration files before editing them on a production server.

```bash
# Copy one.txt to root directory with a new name
cp one.txt /root/chinmay.txt

# Copy an entire folder recursively using -r
cp -r myfirstwebsite /var/www/backup_website
```

---

## 📝 **Text Editing with Vim**

### ✍️ `vim` (Visual Editor)

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

## 🔍 **File Inspection & System Identity**

### 👁️ `cat` (Concatenate & Print)

- **What it does:** Outputs the entire contents of a file directly into the terminal screen.
- **DevOps Use Case:** Reading small configuration files, API keys, or quick debug scripts.

```bash
# View file content
cat chinmay.txt

# View content with line numbers for easier debugging (-n)
cat -n chinmay.txt
```

### 📜 `less` (Paginated File Viewer)

- **What it does:** Opens large files in an interactive, scrollable terminal viewer without loading the whole file into memory.
- **DevOps Use Case:** Reading massive server access or error logs (`/var/log/nginx/access.log`) smoothly.

```bash
less chinmay.txt
```

> 💡 **Navigation in `less`:** Use `↑` / `↓` arrows or `Space` to scroll, `/search-term` to find text, and press `q` to exit.

### 👤 `whoami` (Identify Current User)

- **What it does:** Prints the username associated with your current shell session.
- **DevOps Use Case:** Verifying whether you are operating as a standard user or have elevated to `root` before running critical commands.

```bash
whoami
# Output: root (or ubuntu)
```
