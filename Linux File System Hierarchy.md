# 🐧 Linux File System Hierarchy (Cloud Engineer Guide)

Linux follows a **single-root directory structure**, where everything starts from `/`.  
Unlike Windows (C:, D:), Linux treats **everything as a file** — even devices and processes.

For a **Cloud Engineer**, understanding this hierarchy is critical because:
- Server issues are debugged using logs
- Services are configured using config files
- Permissions & security depend on directory structure

---

## 📌 Root Directory `/`
The starting point of the Linux file system.

```bash
ls /
All system directories originate from here.

📂 Important Linux Directories (Cloud Focused)
🔹 /bin – Essential User Commands
Contains basic command binaries like:

ls, cp, mv, cat, bash

👉 Cloud Use:
Used even in recovery or minimal mode.

🔹 /sbin – System Administration Commands
Contains system-level commands:

reboot, shutdown, ip, fsck

👉 Cloud Use:
Server restart, networking & disk repair.

⭐ /etc – Configuration Files (MOST IMPORTANT)
Stores configuration files for:

OS

Services (nginx, ssh, cron)

bash
Copy code
ls /etc
👉 Cloud Use:
90% service issues are solved here.

Examples:

SSH config → /etc/ssh/sshd_config

Nginx config → /etc/nginx/nginx.conf

🔹 /home – User Home Directories
Each normal user gets a folder here.

bash
Copy code
/home/username
👉 Cloud Use:
Application files, non-root operations.

🔹 /root – Root User Home
Home directory of the root (admin) user.

👉 Cloud Use:
Emergency admin access.

⭐ /var – Variable Data
Contains frequently changing data:

Logs

Cache

Mail

Spool files

bash
Copy code
ls /var/log
👉 Cloud Use:
Server troubleshooting & debugging.

🔹 /tmp – Temporary Files
Used for short-lived temporary data.

👉 Cloud Use:
Temporary scripts & downloads.

🔹 /usr – User System Resources
Stores applications and libraries.

Common paths:

/usr/bin

/usr/lib

👉 Cloud Use:
Installed software lives here.

🔹 /opt – Optional / Third-Party Software
Used for manually installed applications.

👉 Cloud Use:
Custom tools & enterprise software.

🔹 /dev – Device Files
Represents hardware as files.

Examples:

Disk → /dev/sda

Null device → /dev/null

👉 Cloud Use:
Disk & block storage management.

🔹 /proc – Process Information (Virtual)
Contains runtime system information.

👉 Cloud Use:
Performance & process monitoring.

⚠️ /boot – Boot Files
Contains kernel & bootloader files.

👉 Cloud Use:
Rarely touched. Editing can break the system.

☁️ Real Cloud Scenarios
🔧 Nginx Not Working
Check config → /etc/nginx/

Check logs → /var/log/nginx/

💽 Disk Full Issue
Logs → /var/log

Cache → /var/cache

🔐 SSH Login Issue
Config → /etc/ssh/

User home → /home/username

🧪 Practice Commands
bash
Copy code
ls /
cd /etc
ls
cd /var/log
ls
pwd
