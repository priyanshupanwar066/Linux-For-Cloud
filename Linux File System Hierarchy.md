# Linux File System Hierarchy - Complete Guide

## Table of Contents
- [Introduction](#introduction)
- [Root Directory Structure](#root-directory-structure)
- [Directory Details](#directory-details)
  - [/ (Root Directory)](#-root-directory)
  - [/bin (Binaries)](#bin-binaries)
  - [/boot (Boot Loader)](#boot-boot-loader)
  - [/dev (Devices)](#dev-devices)
  - [/etc (Configuration)](#etc-configuration)
  - [/home (User Homes)](#home-user-homes)
  - [/lib (Libraries)](#lib-libraries)
  - [/media (Removable Media)](#media-removable-media)
  - [/mnt (Mount Point)](#mnt-mount-point)
  - [/opt (Optional Software)](#opt-optional-software)
  - [/proc (Process Info)](#proc-process-info)
  - [/root (Root Home)](#root-root-home)
  - [/run (Runtime Data)](#run-runtime-data)
  - [/sbin (System Binaries)](#sbin-system-binaries)
  - [/srv (Service Data)](#srv-service-data)
  - [/sys (System Info)](#sys-system-info)
  - [/tmp (Temporary)](#tmp-temporary)
  - [/usr (User Programs)](#usr-user-programs)
  - [/var (Variable Data)](#var-variable-data)
- [Common Commands](#common-commands)
- [Quick Reference](#quick-reference)

---

## Introduction

Linux organizes everything in a **tree structure** starting from the root (`/`). This guide covers all major directories and their related commands for Cloud Engineers.

---

## Root Directory Structure

```
/
├── bin      → Essential user commands
├── boot     → Boot loader files
├── dev      → Device files
├── etc      → Configuration files
├── home     → User home directories
├── lib      → Shared libraries
├── media    → Removable media mount points
├── mnt      → Temporary mount points
├── opt      → Optional software
├── proc     → Process information (virtual)
├── root     → Root user home
├── run      → Runtime data
├── sbin     → System binaries
├── srv      → Service data
├── sys      → System information (virtual)
├── tmp      → Temporary files
├── usr      → User programs
└── var      → Variable data
```

---

## Directory Details

### `/` (Root Directory)
**Purpose:** Top-level directory, starting point of entire filesystem

**Commands:**
```bash
cd /                    # Navigate to root
ls /                    # List root contents
tree -L 1 /            # Tree structure (one level)
df -h /                # Disk usage of root partition
du -sh /*              # Size of each directory in root
```

---

### `/bin` (Binaries)
**Purpose:** Essential user commands and programs

**Commands:**
```bash
ls /bin                 # List all binaries
ls -lh /bin/bash       # Details of bash shell
which ls               # Find command location
file /bin/ls           # Check file type
/bin/ls                # Run binary directly
type ls                # Command type information
```

**Key Binaries:**
- `bash`, `sh` - Shell programs
- `ls`, `cp`, `mv`, `rm` - File operations
- `cat`, `grep`, `sed`, `awk` - Text processing
- `chmod`, `chown` - Permission management

---

### `/boot` (Boot Loader)
**Purpose:** Files needed to boot the system

**Commands:**
```bash
ls /boot                      # List boot files
ls -lh /boot/vmlinuz*         # Kernel files
cat /boot/grub/grub.cfg       # GRUB config (needs sudo)
df -h /boot                   # Boot partition space
uname -r                      # Current kernel version
uname -a                      # All system information
ls /boot/initrd.img*          # Initial RAM disk images
```

**Important Files:**
- `vmlinuz` - Compressed Linux kernel
- `initrd.img` - Initial RAM disk
- `grub/` - GRUB bootloader configuration
- `config-*` - Kernel configuration

---

### `/dev` (Devices)
**Purpose:** Device files representing hardware

**Commands:**
```bash
ls /dev                       # List all devices
ls -l /dev/sda*              # Disk devices
ls -l /dev/tty*              # Terminal devices
lsblk                        # Block devices list
lsblk -f                     # Show filesystem info
fdisk -l                     # Partition info (sudo)
blkid                        # Block device attributes
mount | grep /dev            # Mounted devices
ls -l /dev/disk/by-uuid/     # Devices by UUID
cat /dev/null                # Null device (discard output)
head -c 10 /dev/random       # Random data
ls -l /dev/input/            # Input devices
```

**Common Devices:**
- `/dev/sda`, `/dev/sdb` - SATA/SCSI disks
- `/dev/nvme0n1` - NVMe SSDs
- `/dev/tty` - Terminals
- `/dev/null` - Null device
- `/dev/zero` - Zero device
- `/dev/random`, `/dev/urandom` - Random generators

---

### `/etc` (Configuration)
**Purpose:** System-wide configuration files

**Commands:**
```bash
ls /etc                          # List config files
cat /etc/hostname                # System hostname
cat /etc/hosts                   # IP/hostname mappings
cat /etc/passwd                  # User accounts
cat /etc/shadow                  # Encrypted passwords (sudo)
cat /etc/group                   # Group information
cat /etc/fstab                   # Filesystem mount table
cat /etc/resolv.conf             # DNS configuration
cat /etc/os-release              # OS information
cat /etc/timezone                # System timezone
ls /etc/ssh/                     # SSH configuration
ls /etc/systemd/                 # Systemd configs
grep username /etc/passwd        # Search specific user
vim /etc/hosts                   # Edit hosts file
ls /etc/apt/                     # APT package manager config
ls /etc/yum.repos.d/             # YUM repositories (RHEL/CentOS)
cat /etc/services                # Network services and ports
```

**Important Subdirectories:**
- `/etc/ssh/` - SSH server/client config
- `/etc/nginx/` - Nginx web server
- `/etc/apache2/` - Apache web server
- `/etc/network/` - Network settings
- `/etc/systemd/` - Systemd configuration
- `/etc/cron.d/` - Cron jobs

---

### `/home` (User Homes)
**Purpose:** Personal directories for each user

**Commands:**
```bash
ls /home                         # List all users
cd ~                             # Go to your home
cd /home/username                # Go to specific user home
pwd                              # Print current directory
ls -la ~/                        # Show hidden files
du -sh /home/*                   # Space usage per user
df -h /home                      # Home partition space
find ~ -name "*.txt"             # Find files in home
tree -L 2 ~                      # Home directory tree
ls -la ~/.ssh/                   # SSH keys and config
```

**Common Hidden Files/Directories:**
```bash
ls -la ~/
# .bashrc          - Bash shell configuration
# .bash_profile    - Bash login script
# .bash_history    - Command history
# .ssh/            - SSH keys and config
# .vimrc           - Vim editor config
# .gitconfig       - Git configuration
# .profile         - Shell profile
```

---

### `/lib` (Libraries)
**Purpose:** Shared libraries for system programs

**Commands:**
```bash
ls /lib                          # 32-bit libraries
ls /lib64                        # 64-bit libraries
ls /lib/modules/                 # Kernel modules
ldconfig -p                      # Show library cache
ldconfig -p | grep ssl           # Search specific library
ldd /bin/ls                      # Show program dependencies
find /lib -name "libc*"          # Find specific library
ls /lib/systemd/                 # Systemd libraries
```

---

### `/media` (Removable Media)
**Purpose:** Auto-mount point for removable media

**Commands:**
```bash
ls /media                        # List mounted media
ls /media/$USER/                 # User's mounted media
mount | grep media               # Show media mount points
df -h /media/*                   # Media storage info
umount /media/usb                # Unmount USB
lsblk | grep media               # Block devices in media
```

---

### `/mnt` (Mount Point)
**Purpose:** Temporary filesystem mount point

**Commands:**
```bash
ls /mnt                          # List mounted systems
sudo mount /dev/sdb1 /mnt        # Mount device
sudo mount -t nfs server:/path /mnt  # Mount NFS
sudo umount /mnt                 # Unmount
mount | grep /mnt                # Check mounts
df -h /mnt                       # Check space
sudo mount -o loop image.iso /mnt  # Mount ISO file
findmnt /mnt                     # Show mount info
```

---

### `/opt` (Optional Software)
**Purpose:** Third-party and optional software

**Commands:**
```bash
ls /opt                          # List installed software
du -sh /opt/*                    # Size of each package
sudo mkdir /opt/myapp            # Create app directory
sudo tar -xzf app.tar.gz -C /opt/  # Extract to opt
ls -la /opt/                     # Detailed listing
find /opt -name "*.sh"           # Find scripts
```

**Common Usage:**
- Commercial software installations
- Custom applications
- Third-party packages

---

### `/proc` (Process Info)
**Purpose:** Virtual filesystem with process and kernel information

**Commands:**
```bash
ls /proc                         # List processes (by PID)
cat /proc/cpuinfo                # CPU information
cat /proc/meminfo                # Memory information
cat /proc/version                # Linux version
cat /proc/uptime                 # System uptime
cat /proc/loadavg                # System load average
cat /proc/filesystems            # Supported filesystems
cat /proc/mounts                 # Currently mounted filesystems
cat /proc/partitions             # Partition information
cat /proc/cmdline                # Kernel command line
ls /proc/[PID]/                  # Specific process info
cat /proc/[PID]/status           # Process status
cat /proc/[PID]/cmdline          # Process command line
cat /proc/sys/kernel/hostname    # System hostname
cat /proc/net/dev                # Network devices
cat /proc/swaps                  # Swap space info
```

**Useful Files:**
- `/proc/cpuinfo` - CPU details
- `/proc/meminfo` - Memory stats
- `/proc/diskstats` - Disk I/O stats
- `/proc/net/*` - Network information

---

### `/root` (Root Home)
**Purpose:** Home directory for root user

**Commands:**
```bash
sudo ls /root                    # List root home
sudo ls -la /root                # Show hidden files
sudo cd /root                    # Navigate to root home
sudo cat /root/.bashrc           # Root bash config
sudo du -sh /root                # Root home size
sudo find /root -name "*.log"    # Find files
```

> **Note:** Requires sudo/root privileges

---

### `/run` (Runtime Data)
**Purpose:** Runtime data for processes since last boot

**Commands:**
```bash
ls /run                          # List runtime data
ls /run/lock                     # Lock files
ls /run/user/                    # User runtime directories
cat /run/systemd/*               # Systemd runtime info
ls /run/udev/                    # Udev runtime data
```

---

### `/sbin` (System Binaries)
**Purpose:** System administration commands

**Commands:**
```bash
ls /sbin                         # List system binaries
/sbin/ifconfig                   # Network configuration
/sbin/fdisk -l                   # Disk partitioning (sudo)
which ifconfig                   # Find command location
/sbin/ip addr                    # IP address management
/sbin/route                      # Routing table
ls -lh /sbin/                    # Detailed listing
```

**Important Commands:**
- `ifconfig`, `ip` - Network configuration
- `fdisk`, `mkfs` - Disk management
- `reboot`, `shutdown` - System control
- `iptables` - Firewall management
- `systemctl` - Service management

---

### `/srv` (Service Data)
**Purpose:** Data for services provided by system

**Commands:**
```bash
ls /srv                          # List service data
ls /srv/www                      # Web server data
ls /srv/ftp                      # FTP server data
du -sh /srv/*                    # Service data sizes
sudo mkdir /srv/myservice        # Create service directory
```

---

### `/sys` (System Info)
**Purpose:** Virtual filesystem for kernel and device information

**Commands:**
```bash
ls /sys                          # System information
ls /sys/class/                   # Device classes
ls /sys/class/net                # Network interfaces
cat /sys/class/power_supply/BAT*/capacity  # Battery info
ls /sys/block                    # Block devices
cat /sys/class/thermal/thermal_zone*/temp  # Temperature
ls /sys/devices/                 # Device hierarchy
cat /sys/kernel/mm/transparent_hugepage/enabled  # Memory info
```

---

### `/tmp` (Temporary)
**Purpose:** Temporary files (cleared on reboot)

**Commands:**
```bash
ls /tmp                          # List temp files
cd /tmp                          # Navigate to tmp
touch /tmp/test.txt              # Create temp file
echo "data" > /tmp/output.txt    # Write to temp
df -h /tmp                       # Check space
du -sh /tmp                      # Directory size
find /tmp -type f -mtime +7      # Files older than 7 days
sudo rm -rf /tmp/*               # Clear temp (careful!)
mktemp                           # Create unique temp file
mktemp -d                        # Create temp directory
```

> **Warning:** `/tmp` is cleared on reboot!

---

### `/usr` (User Programs)
**Purpose:** User applications and utilities

**Commands:**
```bash
ls /usr                          # List user programs
ls /usr/bin                      # User binaries
ls /usr/sbin                     # System admin binaries
ls /usr/local                    # Locally installed software
ls /usr/share                    # Shared data
ls /usr/lib                      # Libraries
ls /usr/include                  # Header files
du -sh /usr/*                    # Size of subdirectories
find /usr/bin -name "python*"    # Find specific program
which python3                    # Find program location
ls /usr/share/doc/               # Documentation
ls /usr/share/man/               # Manual pages
```

**Subdirectories:**
- `/usr/bin` - User commands
- `/usr/sbin` - System admin commands
- `/usr/lib` - Libraries
- `/usr/local` - Locally installed programs
- `/usr/share` - Architecture-independent data
- `/usr/include` - C header files
- `/usr/src` - Source code

---

### `/var` (Variable Data)
**Purpose:** Variable files that change frequently

**Commands:**
```bash
ls /var                          # List variable data
ls /var/log                      # System logs
ls /var/cache                    # Cache files
ls /var/www                      # Web server content
ls /var/lib                      # State information
ls /var/tmp                      # Persistent temp files

# Log management
tail -f /var/log/syslog          # Live log monitoring
tail -n 50 /var/log/auth.log     # Last 50 lines
cat /var/log/dmesg               # Kernel ring buffer
journalctl                       # Systemd logs
grep "error" /var/log/syslog     # Search in logs
du -sh /var/log/*                # Log file sizes
find /var/log -name "*.log" -mtime +30  # Old logs (30+ days)

# Other commands
ls /var/spool/cron/              # Cron jobs
ls /var/mail/                    # User emails
du -sh /var/*                    # Size of directories
df -h /var                       # Partition space
```

**Important Subdirectories:**
- `/var/log` - Log files
- `/var/cache` - Application cache
- `/var/tmp` - Temporary files (persistent across reboots)
- `/var/www` - Web content
- `/var/lib` - Variable state info
- `/var/spool` - Queued tasks
- `/var/mail` - User mailboxes

---

## Common Commands

### Navigation Commands
```bash
# Directory navigation
cd /path/to/directory            # Change directory
cd ..                            # Go up one level
cd -                             # Go to previous directory
cd ~                             # Go to home directory
cd                               # Go to home directory
pwd                              # Print working directory
pushd /path                      # Push directory to stack
popd                             # Pop directory from stack
dirs                             # Show directory stack
```

### Listing Commands
```bash
# Basic listing
ls                               # List files
ls -l                            # Long format
ls -la                           # Include hidden files
ls -lh                           # Human-readable sizes
ls -lt                           # Sort by time
ls -lS                           # Sort by size
ls -lR                           # Recursive listing
ls -i                            # Show inode numbers
tree                             # Tree structure
tree -L 2                        # Tree with depth limit
tree -a                          # Include hidden files
```

### Finding Files
```bash
# Find commands
find / -name "filename"          # Search by name
find /var -type f -name "*.log"  # Find log files
find /home -user username        # Find by user
find / -size +100M               # Files larger than 100MB
find / -mtime -7                 # Modified in last 7 days
find / -atime -7                 # Accessed in last 7 days
find / -perm 777                 # Find by permissions
locate filename                  # Quick search (needs updatedb)
updatedb                         # Update locate database
which command                    # Find command location
whereis command                  # Binary, source, manual locations
type command                     # Command type info
```

### Disk Usage Commands
```bash
# Disk space
df -h                            # Disk space (human-readable)
df -i                            # Inode usage
df -T                            # Show filesystem type
du -sh directory                 # Directory size
du -h --max-depth=1              # Subdirectory sizes
du -ah                           # All files with sizes
du -sh /*                        # Size of root directories
ncdu                             # Interactive disk usage (if installed)
```

### File Information
```bash
# File details
file filename                    # File type
stat filename                    # Detailed file info
ls -li filename                  # Inode number
md5sum filename                  # MD5 checksum
sha256sum filename               # SHA256 checksum
wc -l filename                   # Count lines
wc -w filename                   # Count words
wc -c filename                   # Count bytes
```

### File Operations
```bash
# Copy, move, remove
cp source dest                   # Copy file
cp -r source dest                # Copy directory recursively
cp -p source dest                # Preserve attributes
mv source dest                   # Move/rename
rm file                          # Remove file
rm -r directory                  # Remove directory recursively
rm -rf directory                 # Force remove (careful!)
mkdir directory                  # Create directory
mkdir -p path/to/directory       # Create parent directories
rmdir directory                  # Remove empty directory
touch file                       # Create empty file or update timestamp
ln -s target link                # Create symbolic link
ln target link                   # Create hard link
```

### Permissions & Ownership
```bash
# Permission management
chmod 755 file                   # Change permissions (rwxr-xr-x)
chmod u+x file                   # Add execute for user
chmod g-w file                   # Remove write for group
chmod o=r file                   # Set read-only for others
chmod -R 644 directory           # Recursive permission change
ls -l                            # Check permissions

# Ownership management
chown user:group file            # Change owner and group
chown user file                  # Change owner only
chown -R user directory          # Recursive ownership change
chgrp group file                 # Change group only
```

### Viewing Files
```bash
# View file content
cat file                         # Display entire file
cat file1 file2 > combined       # Combine files
tac file                         # Display in reverse
head file                        # First 10 lines
head -n 20 file                  # First 20 lines
tail file                        # Last 10 lines
tail -n 20 file                  # Last 20 lines
tail -f file                     # Follow file (live updates)
less file                        # Paginated view
more file                        # Paginated view (basic)
nl file                          # Number lines
```

### Searching in Files
```bash
# Search commands
grep "pattern" file              # Search in file
grep -r "pattern" directory      # Recursive search
grep -i "pattern" file           # Case-insensitive
grep -n "pattern" file           # Show line numbers
grep -v "pattern" file           # Invert match
grep -c "pattern" file           # Count matches
egrep "pattern1|pattern2" file   # Extended regex
find / -name "*.conf" -exec grep "pattern" {} \;  # Combine find and grep
```

### System Information
```bash
# System commands
uname -a                         # All system info
uname -r                         # Kernel version
hostname                         # System hostname
hostnamectl                      # Host information
uptime                           # System uptime
who                              # Logged in users
w                                # Who and what they're doing
last                             # Login history
date                             # Current date and time
timedatectl                      # Time and date settings
```

### Process Management
```bash
# Process commands
ps aux                           # All processes
ps aux | grep process            # Find specific process
top                              # Real-time process monitor
htop                             # Interactive process viewer
kill PID                         # Kill process
kill -9 PID                      # Force kill
killall process_name             # Kill by name
pgrep process_name               # Find process ID
pkill process_name               # Kill by name
bg                               # Background job
fg                               # Foreground job
jobs                             # List jobs
nohup command &                  # Run immune to hangups
```

### Network Commands
```bash
# Network
ifconfig                         # Network interfaces (deprecated)
ip addr                          # IP addresses
ip link                          # Network interfaces
ip route                         # Routing table
ping host                        # Test connectivity
ping -c 4 host                   # Ping 4 times
traceroute host                  # Trace route
netstat -tulpn                   # Listening ports
ss -tulpn                        # Socket statistics
curl URL                         # Transfer data from URL
wget URL                         # Download file
nslookup domain                  # DNS lookup
dig domain                       # DNS lookup (detailed)
```

### Archive & Compression
```bash
# Tar archives
tar -czf archive.tar.gz directory   # Create gzip archive
tar -xzf archive.tar.gz             # Extract gzip archive
tar -cjf archive.tar.bz2 directory  # Create bzip2 archive
tar -xjf archive.tar.bz2            # Extract bzip2 archive
tar -tvf archive.tar                # List contents

# Zip files
zip -r archive.zip directory        # Create zip
unzip archive.zip                   # Extract zip
unzip -l archive.zip                # List zip contents

# Other compression
gzip file                           # Compress file
gunzip file.gz                      # Decompress
bzip2 file                          # Compress with bzip2
bunzip2 file.bz2                    # Decompress bzip2
```

---

## Quick Reference

### Directory Purpose Summary

| Directory | Primary Purpose | Common Usage |
|-----------|----------------|--------------|
| `/` | Root directory | Starting point of filesystem |
| `/bin` | Essential binaries | Basic commands (ls, cp, cat) |
| `/boot` | Boot files | Kernel and bootloader |
| `/dev` | Device files | Hardware devices |
| `/etc` | Configuration | System-wide configs |
| `/home` | User homes | Personal user files |
| `/lib` | Libraries | Shared libraries |
| `/media` | Removable media | USB, CD-ROM auto-mount |
| `/mnt` | Mount point | Temporary mounts |
| `/opt` | Optional software | Third-party apps |
| `/proc` | Process info | Virtual filesystem |
| `/root` | Root home | Root user files |
| `/run` | Runtime data | Process runtime info |
| `/sbin` | System binaries | Admin commands |
| `/srv` | Service data | Server data |
| `/sys` | System info | Virtual filesystem |
| `/tmp` | Temporary | Temp files (cleared on reboot) |
| `/usr` | User programs | Applications and utilities |
| `/var` | Variable data | Logs, cache, spools |

### Permission Numbers

| Number | Permission | Symbolic |
|--------|------------|----------|
| 0 | No permission | --- |
| 1 | Execute | --x |
| 2 | Write | -w- |
| 3 | Write + Execute | -wx |
| 4 | Read | r-- |
| 5 | Read + Execute | r-x |
| 6 | Read + Write | rw- |
| 7 | Read + Write + Execute | rwx |

**Common Permission Sets:**
- `755` - rwxr-xr-x (directories, executables)
- `644` - rw-r--r-- (regular files)
- `600` - rw------- (private files)
- `777` - rwxrwxrwx (full access - avoid!)

### File Type Indicators (ls -l)

| Symbol | File Type |
|--------|-----------|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |
| `c` | Character device |
| `b` | Block device |
| `s` | Socket |
| `p` | Named pipe |

### Essential Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Kill current process |
| `Ctrl + Z` | Suspend current process |
| `Ctrl + D` | Exit/logout |
| `Ctrl + L` | Clear screen |
| `Ctrl + A` | Move to beginning of line |
| `Ctrl + E` | Move to end of line |
| `Ctrl + U` | Delete from cursor to start |
| `Ctrl + K` | Delete from cursor to end |
| `Ctrl + R` | Search command history |
| `Tab` | Auto-complete |
| `↑/↓` | Navigate command history |

---

## Practice Tips

1. **Explore Daily:** Navigate through different directories every day
2. **Use Tab Completion:** Save time and avoid typos
3. **Read Man Pages:** `man command` for detailed help
4. **Practice Safely:** Use test directories for destructive commands
5. **Create Aliases:** Add shortcuts in `~/.bashrc` for frequent commands
6. **Keep Notes:** Document commands you find useful
7. **Use History:** `history` command to review past commands
8. **Learn Wildcards:** `*`, `?`, `[]` for pattern matching

---

## Additional Resources

- Man pages: `man hier` - Filesystem hierarchy description
- Online documentation: [Linux Documentation Project](https://tldp.org/)
- Interactive learning: Practice in a safe VM or container environment

---

## Contributing

Feel free to contribute to this guide by:
- Adding more useful commands
- Providing better examples
- Correcting errors
- Sharing tips and tricks

---

## License

This guide is free to use and distribute for educational purposes.

---

**Author:** Priyanshu Panwar
**Last Updated:** January 2026  
**Version:** 1.0

---

### Quick Search Tips

Use your browser's search (Ctrl+F / Cmd+F) to quickly find:
- Specific directories (e.g., "/var")
- Commands (e.g., "chmod")
- Topics (e.g., "permissions")

Happy Learning! 🚀🐧
