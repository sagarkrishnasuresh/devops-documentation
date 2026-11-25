# Linux Fundamentals

A practical introduction to Linux concepts and commands for DevOps learning.

---

# 1. Linux Fundamentals

## 1.1 What is Linux?

- What an operating system does.
- What Linux is.
- Linux as an open-source, Unix-like kernel.
- Difference between the Linux kernel and a complete Linux operating system.

## 1.2 Linux Kernel

Understand the kernel's role in managing system resources:

- Process management.
- Memory management.
- Device management.
- Filesystem operations.
- Networking.

## 1.3 Linux Distributions

Understand what a Linux distribution is and how it combines the Linux kernel with system utilities and other software.

Examples:

- Ubuntu.
- Debian.
- Fedora.
- Red Hat Enterprise Linux (RHEL).
- Rocky Linux.

## 1.4 Basic Linux Architecture

Understand these components:

- **Hardware:** CPU, RAM, disks, and network devices.
- **Kernel:** Manages hardware and system resources.
- **Shell:** Interprets commands entered by a user.
- **User space:** Where applications and user-level programs run.

## 1.5 Why Linux Matters in DevOps

- Linux servers in cloud environments.
- Linux containers and Docker.
- Kubernetes worker nodes.
- CI/CD runners and build environments.
- Shell scripting and automation.
- Application deployment and troubleshooting.

## 1.6 Basic System Identification Commands

```bash
whoami
cat /etc/os-release
uname -r
uname -a
echo "$SHELL"
```

**Practice goal:** Identify the current user, Linux distribution, kernel version, and default shell.

---

# 2. Linux Filesystem

## 4.1 What is a Filesystem?

- How an operating system organizes, stores, and retrieves data.
- Difference between a filesystem and a directory hierarchy.
- Common filesystem types:
  - ext4
  - XFS
  - Btrfs
  - NTFS
  - FAT32

## 4.2 Linux Directory Hierarchy

Understand that `/` is the root of the Linux directory hierarchy and that other directories exist beneath it.

## 4.3 Important Linux Directories

| Directory | Purpose |
|---|---|
| `/` | Root of the filesystem hierarchy |
| `/home` | Home directories of regular users |
| `/root` | Home directory of the root user |
| `/etc` | System-wide configuration files |
| `/var` | Variable data, including logs and application state |
| `/var/log` | System and application log files |
| `/usr` | User-space programs, libraries, and shared data |
| `/bin` | Traditionally, essential user commands; commonly linked to `/usr/bin` on modern Ubuntu |
| `/sbin` | Traditionally, system administration commands; commonly linked to `/usr/sbin` on modern Ubuntu |
| `/boot` | Files required for the boot process |
| `/dev` | Device files |
| `/proc` | Virtual filesystem exposing process and kernel information |
| `/sys` | Virtual filesystem exposing device and kernel information |
| `/run` | Runtime data for the current boot |
| `/tmp` | Temporary files |
| `/opt` | Optional or additional application software |
| `/mnt` | Common mount location for manually mounted filesystems |
| `/media` | Common mount location for removable media |
| `/lib` | Essential shared libraries and kernel modules; often linked into `/usr/lib` on modern Ubuntu |

## 4.4 Important Path Concepts

**Absolute path**

- Starts from `/`.
- Example: `/home/albert/Documents/notes.txt`.

**Relative path**

- Starts from the current working directory.
- Example: `Documents/notes.txt`.

**Special path symbols**

| Symbol | Meaning |
|---|---|
| `.` | Current directory |
| `..` | Parent directory |
| `~` | Current user's home directory |

## 4.5 Mount Points — Introduction

- What mounting means.
- What a mount point is.
- How an additional disk or USB drive can become accessible through a directory.
- Why separate storage volumes are useful on servers.

Useful commands to recognize:

```bash
lsblk
df -h
mount
findmnt
```

## 4.6 Filesystem Exploration Practice

```bash
pwd
cd /
ls
cd /etc
ls
cat /etc/os-release
ls /var/log
cd ~
pwd
ls -la
df -h
lsblk
```

**Practice goal:** Explore the root directory, configuration directory, log directory, home directory, and available storage devices.

---

# 3. Essential Linux Commands

The objective is to understand the purpose and basic syntax of frequently used commands. Practice these in a safe working directory rather than experimenting with important system files.

## 5.1 Navigation Commands

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Print current working directory | `pwd` |
| `ls` | List files and directories | `ls` |
| `cd` | Change directory | `cd /etc` |
| `cd ..` | Move to parent directory | `cd ..` |
| `cd ~` | Move to home directory | `cd ~` |
| `ls -l` | Show detailed listing | `ls -l` |
| `ls -a` | Include hidden files | `ls -a` |
| `ls -la` | Detailed listing including hidden files | `ls -la` |

## 5.2 File and Directory Management

| Command | Purpose | Example |
|---|---|---|
| `mkdir` | Create a directory | `mkdir practice` |
| `touch` | Create an empty file or update timestamps | `touch notes.txt` |
| `cp` | Copy files or directories | `cp notes.txt backup.txt` |
| `mv` | Move or rename files | `mv notes.txt new-notes.txt` |
| `rm` | Remove files | `rm new-notes.txt` |
| `rmdir` | Remove an empty directory | `rmdir practice` |

Directory copy example:

```bash
cp -r source_dir destination_dir
```

**Safety note:** `rm` can permanently remove files. Check the path carefully before running it. Avoid using `rm -rf` while learning unless you fully understand the target and consequences.

## 5.3 Reading File Contents

| Command | Purpose | Example |
|---|---|---|
| `cat` | Display file contents | `cat notes.txt` |
| `less` | Read a file page by page | `less notes.txt` |
| `head` | Display the first lines | `head notes.txt` |
| `tail` | Display the last lines | `tail notes.txt` |
| `tail -f` | Follow new lines added to a file | `tail -f app.log` |

Useful for DevOps:

- Inspect configuration files.
- Read application output.
- Investigate logs.
- Follow logs while an application is running.

## 5.4 Searching

| Command | Purpose | Example |
|---|---|---|
| `find` | Find files and directories by criteria | `find . -name "*.log"` |
| `grep` | Search for text patterns | `grep "error" app.log` |
| `grep -i` | Search without case sensitivity | `grep -i "error" app.log` |
| `grep -r` | Search recursively in directories | `grep -r "TODO" .` |

## 5.5 System Information

| Command | Purpose | Example |
|---|---|---|
| `whoami` | Show current username | `whoami` |
| `uname -r` | Show kernel release | `uname -r` |
| `uname -a` | Show system and kernel information | `uname -a` |
| `hostname` | Show system hostname | `hostname` |
| `date` | Show current date and time | `date` |
| `uptime` | Show how long the system has been running | `uptime` |
| `free -h` | Show memory usage | `free -h` |
| `df -h` | Show filesystem disk usage | `df -h` |
| `du -sh` | Show the size of a directory | `du -sh ~/Downloads` |
| `ps` | Show process information | `ps aux` |
| `top` | Display running processes and resource usage | `top` |

## 5.6 Permissions — Introduction

Understand:

- File ownership.
- User, group, and others.
- Read (`r`), write (`w`), and execute (`x`) permissions.
- Numeric permission notation.
- Difference between `chmod` and `chown`.

Commands:

```bash
ls -l
chmod
chown
```

Examples to understand:

```bash
chmod 755 script.sh
chmod 644 notes.txt
```

Do not change ownership or permissions of system files during this introductory exercise.

## 5.7 Suggested Hands-on Command Practice

Create a small practice workspace:

```bash
mkdir -p ~/devops-linux-practice
cd ~/devops-linux-practice

mkdir logs scripts backups

touch notes.txt
touch logs/app.log
touch scripts/hello.sh

ls -la
pwd
```

Add some content:

```bash
echo "Learning Linux for DevOps" > notes.txt
echo "Application started" > logs/app.log
echo "ERROR: Sample error" >> logs/app.log
```

Read and search:

```bash
cat notes.txt
cat logs/app.log
grep "ERROR" logs/app.log
head logs/app.log
tail logs/app.log
```

Copy and rename:

```bash
cp notes.txt backups/notes-backup.txt
mv notes.txt learning-notes.txt
ls -R
```

**Practice goal:** Become comfortable navigating directories, creating files, copying and moving files, reading content, and searching for text.

---

# 4. Linux Boot Process

## 6.1 What Happens When a Computer Starts?

Understand the sequence of events from switching on the computer to reaching the login screen.

## 6.2 Main Boot Stages

#### Stage 1: BIOS / UEFI

- Firmware starts when the computer is powered on.
- Performs initial hardware checks.
- Identifies a bootable device.
- Starts the bootloader.

#### Stage 2: Bootloader (GRUB)

- GRUB is a commonly used Linux bootloader.
- Presents boot options when configured to do so.
- Loads the Linux kernel and the initial RAM filesystem.

#### Stage 3: Linux Kernel Initialization

- Kernel initializes CPU, memory, device drivers, and other core components.
- Detects and initializes hardware.
- Prepares the system to start user space.

#### Stage 4: initramfs / initrd

- A temporary initial filesystem loaded into memory.
- Provides tools and drivers needed early in boot.
- Helps the kernel access the real root filesystem.

#### Stage 5: systemd (PID 1)

- The kernel starts the first user-space process.
- On most modern Ubuntu systems, this is `systemd`.
- `systemd` has process ID 1.
- It starts and manages services and other system units.

#### Stage 6: Services and Login

- System services are started according to the configured boot target.
- Networking and other required services become available.
- The system reaches a login screen or terminal login prompt.

## 6.3 Boot Process Flow

```text
Power On
   |
   v
BIOS / UEFI
   |
   v
Hardware Initialization
   |
   v
Bootloader (GRUB)
   |
   v
Linux Kernel
   |
   v
initramfs / initrd
   |
   v
Mount Real Root Filesystem
   |
   v
systemd (PID 1)
   |
   v
Start Services and Targets
   |
   v
Login Screen / Login Prompt
```

## 6.4 Useful Commands for Boot and Service Inspection

```bash
systemd-analyze
systemd-analyze blame
systemctl list-units --type=service
systemctl status
journalctl -b
```

These commands help inspect boot timing, services, and system logs. Some output may require elevated permissions for full detail.

**Practice goal:** Be able to explain the boot stages in the correct order and understand the role of GRUB, the kernel, initramfs, and systemd.

---

# 5. Revision and Knowledge Check

Before finishing, verify that you can answer these questions without looking at the notes.

1. What is Linux, and how is it different from Ubuntu?
2. What is the responsibility of the Linux kernel?
3. What is the difference between a shell and a kernel?
4. What is the root directory in Linux?
5. What kind of files are generally stored in `/etc`?
6. Where are system logs commonly stored?
7. What is the difference between `/root` and `/home`?
8. What is the difference between an absolute path and a relative path?
9. What is a mount point?
10. Which command displays disk usage?
11. Which command displays memory usage?
12. What is the purpose of `grep`?
13. What does `chmod` do?
14. What is the role of GRUB?
15. What is systemd, and why is PID 1 important?

---

# 6. Commands Quick Reference

| Category | Commands |
|---|---|
| Navigation | `pwd`, `ls`, `cd` |
| File management | `mkdir`, `touch`, `cp`, `mv`, `rm`, `rmdir` |
| Reading files | `cat`, `less`, `head`, `tail` |
| Searching | `find`, `grep` |
| System information | `whoami`, `uname`, `hostname`, `date`, `uptime` |
| Processes | `ps`, `top` |
| Memory and storage | `free`, `df`, `du`, `lsblk` |
| Permissions | `chmod`, `chown` |
| Boot and services | `systemd-analyze`, `systemctl`, `journalctl` |

---

# 7. Topics to Explore Further

The following topics can be explored in more depth as part of continued Linux and DevOps learning.

- Linux users, groups, and permissions in depth.
- Process management and signals.
- Package management (`apt`, `dpkg`).
- Services and service management with `systemd`.
- Networking commands and troubleshooting.
- SSH and remote server administration.
- Disk partitioning, formatting, mounting, and `/etc/fstab`.
- Environment variables and shell configuration.
- Bash scripting.
- Cron jobs and scheduling.
- Linux security and firewall fundamentals.
- Kernel modules and advanced boot troubleshooting.