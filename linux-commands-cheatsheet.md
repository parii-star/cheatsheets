# Linux Terminal Cheat Sheet

> **Goal:** Understand common Linux terminal commands clearly enough to use them even as a beginner.

The Linux terminal lets you control your computer by typing commands. You can move between folders, create files, install software, check system health, manage services, inspect logs, and automate repeated work.

This cheat sheet is written for Ubuntu and similar Linux distributions.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[file]` | replace with a real file name, such as `notes.txt` |
| `[directory]` | replace with a folder name, such as `Documents` |
| `[package]` | replace with a software package name, such as `htop` |
| `[service]` | replace with a service name, such as `ssh` |
| `[pid]` | replace with a process ID number, such as `1234` |
| `.` | the current directory |
| `..` | the parent directory |
| `~` | your home directory |

Example:

```bash
cd [directory]
```

If the folder is named `Downloads`, run:

```bash
cd Downloads
```

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Navigation](#navigation) | move around folders |
| [Files And Directories](#files-and-directories) | create, copy, move, and delete files |
| [Viewing Files](#viewing-files) | read file contents |
| [Search And Find](#search-and-find) | search text and locate files |
| [Essential Commands](#essential-commands) | everyday terminal basics |
| [Permissions](#permissions) | understand and change file access |
| [Processes](#processes) | view and stop running programs |
| [Pipes And Redirection](#pipes-and-redirection) | connect commands and save output |
| [Archives And Compression](#archives-and-compression) | compress and extract files |
| [System Info](#system-info) | inspect CPU, memory, disk, and OS details |
| [Packages](#packages) | install and update software |
| [Services](#services) | manage background services |
| [Networking](#networking) | inspect network connections |
| [Disk And Storage](#disk-and-storage) | check disks and storage usage |
| [Logs](#logs) | read system logs |
| [Handy Shortcuts](#handy-shortcuts) | useful keyboard shortcuts |

## Command Categories
The items in your image are already covered in this cheat sheet. This section groups them by purpose so they are easier to scan.

| Category | Related Sections | Main Commands |
|---|---|---|
| Process Monitoring | [Processes](#processes) | `ps aux`, `ps -ef`, `top`, `htop`, `kill` |
| Performance Monitoring | [Processes](#processes), [System Info](#system-info), [Disk And Storage](#disk-and-storage) | `top`, `htop`, `free -h`, `uptime`, `df -h` |
| Networking Tools | [Networking](#networking) | `ip a`, `ip r`, `ping`, `curl`, `ss`, `nmcli`, `wget` |
| Text Manipulation | [Viewing Files](#viewing-files), [Search And Find](#search-and-find), [Pipes And Redirection](#pipes-and-redirection) | `cat`, `less`, `head`, `tail`, `grep`, `tee`, `|`, `>` |

## Navigation
Move around the filesystem.

**Syntax:**

```bash
command [path]
```

| Command | Clear Description |
|---|---|
| `pwd` | Print the full path of the folder you are currently inside. Useful when you feel lost. |
| `ls` | List files and folders in the current directory. |
| `ls -la` | List all files, including hidden files, with permissions, owner, size, and date. |
| `cd [directory]` | Move into a specific directory. Example: `cd Documents`. |
| `cd ..` | Move one level up to the parent directory. |
| `cd ~` | Move to your home directory. |
| `cd -` | Go back to the previous directory you were in. |

Example:

```bash
pwd
ls
cd Downloads
```

## Files And Directories
Create, copy, move, rename, and delete files or folders.

**Syntax:**

```bash
command [source] [destination]
```

| Command | Clear Description |
|---|---|
| `touch [file]` | Create an empty file if it does not exist. If it exists, update its modified time. |
| `mkdir [directory]` | Create a new directory. Example: `mkdir reports`. |
| `mkdir -p path/to/dir` | Create nested directories. Missing parent folders are created automatically. |
| `cp [source] [destination]` | Copy a file from one location to another. The original file remains. |
| `cp -r [source-dir] [destination]` | Copy a directory and everything inside it. `-r` means recursive. |
| `mv [source] [destination]` | Move a file/folder or rename it. Example: `mv old.txt new.txt`. |
| `rm [file]` | Delete a file permanently. |
| `rm -r [directory]` | Delete a directory and everything inside it. |
| `rm -rf [directory]` | Force delete a directory without asking. Use with extreme care. |

> **Warning:** Deleted files usually do not go to a recycle bin. Be very careful with `rm -rf`.

Example:

```bash
mkdir project
touch project/notes.txt
cp project/notes.txt backup.txt
```

## Viewing Files
Read file contents from the terminal.

**Syntax:**

```bash
command [file]
```

| Command | Clear Description |
|---|---|
| `cat [file]` | Print the entire file to the terminal. Best for short files. |
| `less [file]` | Open a file page by page. Press `q` to quit. Best for long files. |
| `head [file]` | Show the first 10 lines of a file. |
| `head -n 20 [file]` | Show the first 20 lines of a file. Change `20` to any number. |
| `tail [file]` | Show the last 10 lines of a file. |
| `tail -f [file]` | Keep showing new lines as they are added. Useful for log files. |
| `wc -l [file]` | Count how many lines are in a file. |

Example:

```bash
less /var/log/syslog
tail -f app.log
```

## Search And Find
Search inside files or locate files by name.

**Syntax:**

```bash
grep [options] "text" [file]
find [location] [condition]
```

| Command | Clear Description |
|---|---|
| `grep "text" [file]` | Search for matching text inside one file. |
| `grep -R "text" [directory]` | Search inside all files under a directory. `-R` means recursive. |
| `grep -i "text" [file]` | Search without caring about uppercase or lowercase letters. |
| `find . -name "*.sh"` | Find files ending with `.sh` under the current directory. |
| `find . -type f` | List only files under the current directory. |
| `which [command]` | Show where a command is installed. Example: `which python3`. |
| `history` | Show commands you typed earlier in the terminal. |

Example:

```bash
grep -R "error" logs/
find . -name "*.py"
```

## Essential Commands
Commands used frequently in daily terminal work.

**Syntax:**

```bash
command [option] [value]
```

| Command | Clear Description |
|---|---|
| `clear` | Clear the terminal screen. It does not delete files or command history. |
| `echo "Hello"` | Print text to the terminal. Useful in scripts and quick checks. |
| `man ls` | Open the manual/help page for the `ls` command. Press `q` to quit. |
| `sudo command` | Run a command with administrator privileges. Use only when needed. |
| `sudo !!` | Repeat the previous command with `sudo` added in front. |
| `nano file.txt` | Open a file in the Nano text editor. Easier for beginners. |
| `vim file.txt` | Open a file in the Vim editor. Powerful, but has a learning curve. |

Example:

```bash
man ls
echo "Deployment complete"
```

## Permissions
Control who can read, write, or execute files.

**Syntax:**

```bash
chmod [permission] [file]
chown [user]:[group] [file]
```

| Command | Clear Description |
|---|---|
| `ls -l` | Show permissions, owner, group, size, and date for files. |
| `chmod +x script.sh` | Add execute permission so the script can be run as `./script.sh`. |
| `chmod 644 file` | Owner can read/write. Group and others can only read. Common for normal files. |
| `chmod 755 script.sh` | Owner can read/write/execute. Others can read/execute. Common for scripts. |
| `chown user file` | Change the owner of a file to `user`. |
| `chown user:group file` | Change both owner and group. |
| `whoami` | Show the username of the current logged-in user. |
| `id` | Show your user ID, group ID, and groups. |

Permission symbols:

| Symbol | Meaning |
|---|---|
| `r` | read permission: can view file contents |
| `w` | write permission: can modify or delete |
| `x` | execute permission: can run as a program or enter a directory |

Example permission string:

```text
-rwxr-xr-x
```

Meaning: owner has `rwx`, group has `r-x`, others have `r-x`.

## Processes
View and control running programs.

**Syntax:**

```bash
ps [options]
kill [pid]
```

| Command | Clear Description |
|---|---|
| `ps aux` | Show all running processes with CPU, memory, user, and command details. |
| `ps -ef` | Show all running processes in full-format style. |
| `top` | Open a live process monitor that updates automatically. Press `q` to quit. |
| `htop` | Open a more user-friendly interactive process viewer. May need installation. |
| `command &` | Run a command in the background so the terminal is free. |
| `jobs` | List background jobs started from the current terminal. |
| `fg` | Bring the latest background job back to the foreground. |
| `kill [pid]` | Send a terminate signal to a process by process ID. |
| `kill -9 [pid]` | Forcefully kill a process using SIGKILL. Use only if normal `kill` fails. |

Example:

```bash
ps aux
kill 1234
```

## Pipes And Redirection
Send output to files or pass output from one command into another.

**Syntax:**

```bash
command > file
command1 | command2
```

| Command | Clear Description |
|---|---|
| `command > file` | Save normal output to a file, replacing old contents. |
| `command >> file` | Append normal output to the end of a file. |
| `command1 | command2` | Send output from `command1` as input to `command2`. |
| `command 2>/dev/null` | Hide error output by sending it to `/dev/null`. |
| `command > out.log 2>&1` | Save normal output and error output into the same log file. |
| `command | tee file` | Show output on screen and save it to a file at the same time. |

Example:

```bash
ls | grep ".sh"
python3 app.py > output.log 2>&1
```

## Archives And Compression
Compress files into archives or extract archives.

**Syntax:**

```bash
tar [options] [archive] [file-or-folder]
zip [options] [archive] [file-or-folder]
```

| Command | Clear Description |
|---|---|
| `tar -czf file.tar.gz folder/` | Create a compressed `.tar.gz` archive from a folder. |
| `tar -xzf file.tar.gz` | Extract a `.tar.gz` archive into the current directory. |
| `zip -r file.zip folder/` | Create a `.zip` archive from a folder. `-r` includes subfolders. |
| `unzip file.zip` | Extract a `.zip` archive into the current directory. |

Example:

```bash
tar -czf backup.tar.gz project/
tar -xzf backup.tar.gz
```

## Directory Size
Check folder sizes and directory structure.

**Syntax:**

```bash
du [options] [directory]
```

| Command | Clear Description |
|---|---|
| `du -sh *` | Show the size of each file and folder in the current directory. |
| `du -sh [directory]` | Show the total size of one directory. |
| `tree` | Show folders and files as a visual tree. May need installation. |

Example:

```bash
du -sh Downloads
tree
```

## System Info
Check operating system, CPU, memory, uptime, and disk usage.

**Syntax:**

```bash
command [option]
```

| Command | Clear Description |
|---|---|
| `uname -a` | Show detailed kernel and system information. |
| `uname -r` | Show only the kernel version. |
| `hostname` | Show the computer name on the network. |
| `hostnamectl` | Show hostname, OS, kernel, architecture, and hardware details. |
| `uptime` | Show how long the system has been running and current load average. |
| `who -b` | Show when the system last booted. |
| `lscpu` | Show CPU architecture, cores, threads, and model details. |
| `free -h` | Show RAM and swap usage in human-readable units like MB/GB. |
| `df -h` | Show disk space usage for mounted filesystems in human-readable units. |

Example:

```bash
hostnamectl
free -h
df -h
```

## Packages
Install, update, search, and remove software.

**Syntax:**

```bash
sudo apt install [package]
sudo apt remove [package]
```

| Command | Clear Description |
|---|---|
| `sudo apt update` | Refresh the package list from software repositories. Does not upgrade packages. |
| `sudo apt upgrade` | Install available updates for already installed packages. |
| `sudo apt install [package]` | Download and install a package. Example: `sudo apt install htop`. |
| `sudo apt remove [package]` | Remove a package but usually keep its configuration files. |
| `apt search [name]` | Search repositories for packages matching a name or keyword. |
| `apt list --installed` | Show packages currently installed through APT. |
| `snap list` | Show installed Snap packages. |
| `flatpak list` | Show installed Flatpak applications. |

Example:

```bash
sudo apt update
sudo apt install htop
```

## Services
Manage background services such as web servers, SSH, databases, and scheduled workers.

**Syntax:**

```bash
systemctl [action] [service]
journalctl -u [service]
```

| Command | Clear Description |
|---|---|
| `systemctl status [service]` | Show whether a service is running, stopped, failed, or disabled. |
| `systemctl start [service]` | Start a service now. |
| `systemctl stop [service]` | Stop a service now. |
| `systemctl restart [service]` | Stop and start a service again. Useful after config changes. |
| `systemctl enable [service]` | Make a service start automatically when the computer boots. |
| `systemctl disable [service]` | Prevent a service from starting automatically at boot. |
| `journalctl -xe` | Show recent system log messages with extra details for troubleshooting. |
| `journalctl -u [service]` | Show logs for one specific service. |

Example:

```bash
systemctl status ssh
journalctl -u ssh
```

## Networking
Check IP addresses, routes, connectivity, ports, and downloads.

**Syntax:**

```bash
ip [object]
ping [host]
curl [url]
```

| Command | Clear Description |
|---|---|
| `ip a` | Show network interfaces and their IP addresses. |
| `ip r` | Show the routing table, including the default gateway. |
| `ping google.com` | Send test packets to check if a host is reachable. Press `Ctrl+C` to stop. |
| `curl -s https://ifconfig.me` | Show your public internet IP address quietly. |
| `ss -tulnp` | Show listening TCP/UDP ports and the processes using them. |
| `nmcli device status` | Show NetworkManager device connection status. |
| `wget [url]` | Download a file from a URL. |

Example:

```bash
ip a
ping google.com
ss -tulnp
```

## Disk And Storage
Inspect disks, partitions, mounted filesystems, and usage.

**Syntax:**

```bash
df [options]
lsblk
mount
```

| Command | Clear Description |
|---|---|
| `lsblk` | List block devices such as disks, partitions, and removable drives. |
| `df -h` | Show free and used space for mounted filesystems. |
| `du -sh [directory]` | Show how much space one directory uses. |
| `mount` | Show mounted filesystems and where they are attached. |
| `sudo fdisk -l` | List disk partitions. Requires administrator privileges. |

Example:

```bash
lsblk
df -h
du -sh /var/log
```

## Logs
Read system and application logs for troubleshooting.

**Syntax:**

```bash
journalctl [options]
tail -f [log-file]
```

| Command | Clear Description |
|---|---|
| `dmesg` | Show kernel messages, often useful for hardware and driver issues. |
| `dmesg | tail` | Show the latest kernel messages only. |
| `journalctl` | Show logs collected by systemd. |
| `journalctl -f` | Follow system logs live as new entries appear. |
| `journalctl -u [service]` | Show logs for one service. Example: `journalctl -u ssh`. |
| `tail -f /var/log/syslog` | Follow the Ubuntu system log live if the file exists. |

> **Tip:** On modern Ubuntu systems, `journalctl -f` is usually the best live log command.

Example:

```bash
journalctl -f
journalctl -u ssh
```

## Handy Shortcuts
Use the keyboard faster in the terminal.

| Shortcut | Clear Description |
|---|---|
| `Ctrl+C` | Stop the command currently running in the terminal. |
| `Ctrl+D` | Close the current shell or end input. |
| `Ctrl+L` | Clear the terminal screen. |
| `Ctrl+A` | Move the cursor to the start of the current line. |
| `Ctrl+E` | Move the cursor to the end of the current line. |
| `Ctrl+R` | Search your command history interactively. |
| `Tab` | Autocomplete command names, file names, and folder names. |

## Quick Safety Rules

- Read commands carefully before pressing `Enter`.
- Be extra careful with `rm`, `rm -r`, and `rm -rf`.
- Use `sudo` only when the command truly needs administrator permission.
- If you are unsure what a command does, check it with `man [command]` first.
- Prefer testing dangerous commands on sample files before using real data.

## Where DevOps Engineers Use This

Use Linux commands every day when you are operating servers, containers, and cloud VMs.

- Inspect processes, logs, ports, disks, and memory on live systems.
- Install packages, manage services, and verify system health.
- Troubleshoot deployment issues directly from the terminal.
