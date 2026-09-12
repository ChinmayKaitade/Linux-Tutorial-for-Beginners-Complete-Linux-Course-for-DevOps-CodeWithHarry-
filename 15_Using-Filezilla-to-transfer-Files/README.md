# 📁 **Using FileZilla To Transfer Files**

FileZilla is a cross-platform graphical client used for secure, bidirectional file transfers between local machines and remote servers. 💻  
Instead of insecure plain FTP, modern DevOps engineers use **SFTP (SSH File Transfer Protocol)** running encrypted over standard SSH port 22. 🔒  
It simplifies managing static website assets, downloading application logs, and staging code files without writing complex shell commands. 🚀

---

## 📥 **Prerequisites & Download**

- **🖥️ Download FileZilla Client:** Install the free **FileZilla Client** (not Server) for Windows, macOS, or Linux from the official site.
- **🌐 Server Credentials:** You will need your server's Public IP address, SSH username (`root` or your sudo user), and password or private SSH key.
- **🛡️ Firewall Check:** Ensure TCP port **22** (SSH/SFTP) is open on your host provider (Hostinger hPanel, AWS Security Groups, or UFW).

---

## ⚡ **Method 1: QuickConnect (Password Authentication)**

Use the top QuickConnect bar for fast, session-based connections:

1. **Host:** `sftp://<YOUR_SERVER_PUBLIC_IP>` _(Prepending `sftp://` explicitly forces secure SSH transfer mode)._
2. **Username:** `root` (or your created user, e.g., `chinmay`).
3. **Password:** Your server user password.
4. **Port:** `22` (default SSH port).
5. Click **Quickconnect**.
6. **Host Key Verification:** On the first connection, check **"Always trust this host"** and click **OK** to accept the remote server's fingerprint. 🔑

---

## 🔑 **Method 2: Site Manager with SSH Keys (Recommended & Secure)**

For recurring access using an SSH private key (`id_ed25519` or `id_rsa`), use FileZilla's persistent Site Manager:

1. Open FileZilla and navigate to **File > Site Manager** (or press `Ctrl + S` / `Cmd + S`).
2. Click **New Site** and name it (e.g., `Hostinger-DevOps-VPS`).
3. Set the connection properties:
   - **Protocol:** Select **SFTP - SSH File Transfer Protocol**.
   - **Host:** Enter your server's public IP address.
   - **Port:** `22`.
   - **Logon Type:** Select **Key file**.
   - **User:** `root` (or your user account).
   - **Key file:** Browse and select your private key file (e.g., `C:\Users\<user>\.ssh\id_rsa` or `~/.ssh/id_ed25519`).
4. Click **Connect**.

---

## 🖥️ **Navigating the FileZilla Dual-Pane Interface**

Once connected, FileZilla presents two primary working directory trees side-by-side:

| Left Pane (Local Site)                                                | Right Pane (Remote Site)                                                          |
| :-------------------------------------------------------------------- | :-------------------------------------------------------------------------------- |
| Displays the filesystem of your local computer (Windows/macOS/Linux). | Displays the filesystem of your remote Linux server (starting at `/` or `/root`). |

- **⬆️ Uploading Files:** Navigate to the project folder on your local pane, find the files, right-click, and select **Upload** (or simply drag and drop them into the remote right pane, e.g., into `/var/www/html/`).
- **⬇️ Downloading Logs/Backups:** Navigate on the remote right pane to `/var/log/nginx/` or `/home/chinmay/`, right-click a file (like `access.log`), and select **Download**.
- **📝 Direct Remote File Editing:** Right-click any text file on the remote server and select **View/Edit** to modify code locally in your default editor and automatically sync changes back on save.

---

## ⚠️ **Common Troubleshooting & Permission Fixes**

- **❌ Error: "Permission Denied" while uploading to `/var/www/`:**  
  Non-root users might lack write permissions in web directories. Fix directory ownership via terminal:

  ```bash
  sudo chown -R $USER:www-data /var/www/html
  sudo chmod -R 775 /var/www/html
  ```

- **❌ Error: "Connection timed out":**
  Verify your server's firewall allows port 22:

```bash
sudo ufw allow 22/tcp
sudo ufw reload
```
