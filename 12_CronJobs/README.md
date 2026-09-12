# ⏰ **Cronjobs**

Automating recurring scripts and periodic housekeeping tasks is essential for stable production environments. ⏱️  
The Linux `cron` daemon runs scheduled commands in the background at specific intervals, dates, and times. 🤖  
From running scheduled database backups to executing maintenance scripts, mastering `cron` is a core DevOps skill. 🚀

---

## 📋 **Inspecting & Managing Cron Tables**

Each user maintains their own dedicated cron schedule file managed through the `crontab` utility.

### 👁️ `crontab -l` (List Scheduled Jobs)

- **What it does:** Displays all active cron jobs scheduled under the current user account.
- **DevOps Use Case:** Auditing existing scheduled jobs before deploying new automation scripts.

```bash
crontab -l
```

### ✏️ `crontab -e` (Edit Scheduled Jobs)

- **What it does:** Opens the user's crontab schedule inside an interactive terminal editor.
- **Selecting Your Preferred Editor:**
  On the first execution, Linux prompts you to select a default text editor:

```text
Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <-- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny

Choose 1-3 [1]: 2
```

Type `2` and hit `Enter` to set **Vim** as your default editor.

---

## 🐍 **Creating a Sample Python Automation Script**

Prepare a simple script that logs timestamps to verify that your scheduled cron job triggers reliably.

### ✍️ 1. Write the Script (`main.py`)

Create the script using Vim:

```bash
vim main.py
```

Paste the following Python code:

```python
from datetime import datetime

# Append the current timestamp to time.txt
with open("/home/chinmay/time.txt", "a") as f:
    f.write(f"Cron executed successfully at: {datetime.now()}\n")
```

Press `Esc`, type `:wq`, and hit `Enter`.

### 🧪 2. Test Execution & Clean Up

Run the script manually to confirm it writes to the destination file:

```bash
# Execute the script
python3 main.py

# Verify that time.txt was created and populated
cat time.txt

# Remove the test file before scheduling the cron job
rm time.txt
```

---

## 🧠 **Crontab Syntax & Crontab Guru Guide**

Every scheduled cron entry follows a five-field time specification followed by the absolute executable command:

```text
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of the month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday)
│ │ │ │ │
* * * * * <command-to-execute>
```

### 🎯 Special Operator Cheatsheet

- `*` (**Wildcard / Every**): Runs on every matching value (e.g., `*` in the minute field runs every minute).
- `,` (**Value List**): Specifies distinct execution intervals (e.g., `15,45` runs at minute 15 and minute 45).
- `-` (**Range**): Defines an inclusive range (e.g., `1-5` in day-of-week runs Monday through Friday).
- `/` (**Step Value**): Specifies incremental intervals (e.g., `*/10` in minute runs every 10 minutes).

> 💡 **DevOps Tip:** Use **[crontab.guru](https://crontab.guru)** to test, validate, and human-read any complex cron expression before pushing it to production!

### 🚀 Common Real-World Cron Examples

| Expression    | Schedule Description                         |
| ------------- | -------------------------------------------- |
| `* * * * *`   | Every single minute                          |
| `*/5 * * * *` | Every 5 minutes                              |
| `0 * * * *`   | Every hour on the hour                       |
| `0 2 * * *`   | Daily at 2:00 AM (Ideal for nightly backups) |
| `0 0 * * 0`   | Weekly on Sunday at midnight                 |

---

## ⚙️ **Configuring the Cron Job**

Always use **absolute paths** for both the runtime interpreter (`/usr/bin/python3`) and the script target (`/home/chinmay/main.py`), because cron runs in a minimal environment without user-defined `$PATH` entries.

### ➕ 1. Add the Scheduled Entry

Open the schedule editor:

```bash
crontab -e
```

Add the following line to the bottom:

```cron
* * * * * /usr/bin/python3 /home/chinmay/main.py
```

Save and exit (`Esc` -> `:wq` -> `Enter`).

### 🔍 2. Verify Active Configuration

Confirm the schedule has been updated:

```bash
crontab -l
```

### 📊 3. Monitor Automatic Execution

Watch the log file populate automatically each minute:

```bash
cat /home/chinmay/time.txt
```
