# 🌐 **Environment Variables, Path and bashrc**

Environment variables define the operating environment and behavioral defaults for shells, scripts, and applications. ⚙️  
System utilities and CI/CD jobs rely on dynamic variables like `$PATH` to discover where executable programs reside. 🔍  
Persisting custom paths and global flags inside configuration files like `.bashrc` streamlines recurring automation workflows. 🚀

---

## 🔍 **Inspecting Environment Variables**

### 🏠 `echo $HOME` (Check User Home Path)

- **What it does:** Prints the absolute filesystem path of the current user's personal home directory.
- **DevOps Use Case:** Writing robust, non-hardcoded backup and configuration scripts that adapt across different environments.

```bash
echo $HOME
# Output: /home/chinmay
```

### 📋 `printenv` (List Global Environment Variables)

- **What it does:** Dumps every active exported environment variable configured in your current session.
- **DevOps Use Case:** Auditing runtime variables, locale configs, and container environment keys during server troubleshooting.

```bash
# Print all environment variables
printenv

# Filter for a specific variable
printenv USER
```

### 🛣️ `echo $PATH` (View Executable Lookup Directories)

- **What it does:** Displays a colon-separated (`:`) list of directories where Linux looks for executable binaries when you run commands.
- **DevOps Use Case:** Diagnosing "command not found" errors when newly installed runtimes like Node.js, Go, or custom tools fail to launch.

```bash
echo $PATH
# Output: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

---

## 🏷️ **Shell Variables vs. Exported Environment Variables**

### 💬 Local Shell Variable

- **What it does:** Creates a temporary variable accessible **only** within the active terminal prompt; child processes cannot see it.

```bash
name="Chinmay"
echo $name
# Output: Chinmay
```

### 🌍 Global Environment Variable (`export`)

- **What it does:** Uses `export` to make the variable available to child shells, spawned processes, and executing scripts.
- **DevOps Use Case:** Supplying database URLs, runtime environments (`NODE_ENV=production`), or API keys to applications.

```bash
export friend="Aman"
echo $friend
# Output: Aman
```

---

## 📜 **Writing & Executing a Custom Bash Script**

### ✍️ 1. Create the Script File

Create a new script file using Vim:

```bash
vim chinmay.sh
```

Add your bash code inside:

```bash
echo "Hello Chinmay";
```

- Press `Esc`, type `:wq`, and press `Enter` to save and exit.

### ⚡ 2. Grant Execute Permissions

By default, new files lack execution rights. Add execute permission (`+x`):

```bash
chmod +x chinmay.sh
```

### 🚚 3. Organize Into the Workspace

Move the executable script into your team folder:

```bash
# Move chinmay.sh inside the devs folder
mv chinmay.sh devs/
```

---

## 🛣️ **Extending the System `$PATH**`

### ➕ `export PATH="$PATH:/home/chinmay/devs"`

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

## 💾 **Making Variables & Paths Permanent via `.bashrc**`

Variables set in an active terminal session disappear when the session closes. Storing them in `~/.bashrc` ensures they load automatically every time an interactive bash shell opens.

### 🕵️ 1. View Hidden Files

```bash
# List all files sorted by modification time, oldest to newest (-lart)
ls -lart
```

### 📝 2. Edit `.bashrc`

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

### 🔄 3. Reload Shell Configuration (`source`)

- **What it does:** Forces the active bash session to re-read and apply updates from `.bashrc` without needing to log out or reboot.

```bash
source ~/.bashrc
```
