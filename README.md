# 🐧 The Comprehensive Linux Guide for Beginners

A repository that aims to be your first guide in the world of Linux, providing a simplified and organized explanation of the most important commands and tools you will need on your journey.

## 📜 Table of Contents

1.  [Filesystem Commands](#filesystem)
2.  [Users & Permissions Commands](#users-permissions)
3.  [Networking Commands](#networking)
4.  [Process Commands](#processes)
5.  [Package Management Commands](#package-management)
6.  [Text & Search Commands](#text-search)
7.  [Shell Commands](#shell)
8.  [Scripting Commands](#scripting)
9.  [Development Commands](#development)
10. [System Monitoring & Hardware](#system-monitoring)
11. [Useful Tools](#useful-tools)

---

<a id="filesystem"></a>
## 📁 1. Filesystem Commands
| Command | Description | Example |
|:---|:---|:---|
| `pwd` | **P**rint **W**orking **D**irectory - Prints the path of the current directory you are in. | `pwd` |
| `ls` | **L**i**s**t - Displays a list of files and directories in the current directory. | `ls -la` (to show all files with details) |
| `cd` | **C**hange **D**irectory - Used to navigate between directories. | `cd /home/user` |
| `mkdir` | **M**a**k**e **Dir**ectory - Used to create a new directory. | `mkdir my_project` |
| `touch` | Creates a new empty file or updates the timestamp of an existing file. | `touch new_file.txt` |
| `cp` | **C**o**p**y - To copy files or directories from one place to another. | `cp source.txt destination.txt` |
| `mv` | **M**o**v**e - To move or rename files and directories. | `mv old_name.txt new_name.txt` |
| `rm` | **R**e**m**ove - To delete files. (Use with caution!) | `rm file_to_delete.txt` |
| `rm -r` | To delete directories and everything inside them. (Use with extreme caution!) | `rm -r old_directory` |
| `cat` | **Cat**enate - To display the contents of a text file on the screen. | `cat file.txt` |

<br>

#### Additional and Advanced Filesystem Commands

| Command | Description | Example |
|:---|:---|:---|
| `df` | **D**isk **F**ree - Displays a report on the used and available disk space for all filesystems. | `df -h` |
| `du` | **D**isk **U**sage - Displays the amount of space a specific directory and its contents consume. | `du -sh /path/to/dir` |
| `ln` | **L**i**n**k - Used to create links between files. | `ln -s original.txt link.txt` |
| `stat` | Displays very detailed information about a file or directory (inode data). | `stat file.txt` |
| `find` | (Advanced example) Find all files ending in `.log` larger than 10MB. | `find . -type f -name "*.log" -size +10M` |
| `rmdir` | **R**e**m**ove **Dir**ectory - Deletes an empty directory only. | `rmdir empty_folder` |
| `locate` | Quickly find a file using a pre-updated database. | `locate httpd.conf` |
| `less` | Interactively browse the content of a file (more powerful than `cat`). | `less large_log_file.log` |
| `mount` | Mount a filesystem (like a USB drive) to a specific point in the directory tree. | `sudo mount /dev/sdb1 /mnt` |
| `umount` | Unmount a mounted filesystem. | `sudo umount /mnt` |
| `fdisk` | A tool for partitioning hard drives (requires extreme caution). | `sudo fdisk -l` |
| `mkfs` | **M**a**k**e **F**ile**s**ystem - Create a filesystem on a specific partition. | `sudo mkfs.ext4 /dev/sdb1` |
| `dd` | Copy and convert files at the bit level. | `sudo dd if=/dev/sda of=backup.img` |
| `file` | Determine the file type (text, image, executable, etc.). | `file my_script.sh` |
| `tree` | Display the contents of directories in a tree-like format (may need to be installed). | `tree /path/to/dir` |

<a id="users-permissions"></a>
## 👤 2. Users & Permissions Commands
| Command | Description | Example |
|:---|:---|:---|
| `whoami` | Shows the current username. | `whoami` |
| `sudo` | **S**uper**u**ser **Do** - Executes the following command with root privileges. | `sudo apt update` |
| `chown` | **Ch**ange **Own**er - Used to change the owner of a file or directory. | `sudo chown user:group file.txt` |
| `chmod` | **Ch**ange **Mod**e - Used to change the read (r), write (w), and execute (x) permissions of files and directories. | `chmod +x script.sh` (to grant execute permission) |

<br>

#### Deeper Understanding of Permissions

Permissions in Linux can be represented by Octal Notation. Each permission has a value:
*   **r (read)** = 4
*   **w (write)** = 2
*   **x (execute)** = 1

The permission values are summed for each class (owner, group, others). For example, `rwx` = 4+2+1 = 7. `r-x` = 4+0+1 = 5.
Thus, the command `chmod 755 file.sh` means:
*   **7** (rwx): The owner has all permissions.
*   **5** (r-x): The group can read and execute.
*   **5** (r-x): Others can read and execute.

| Command | Description | Example |
|:---|:---|:---|
| `chgrp` | **Ch**ange **Gr**ou**p** - Used to change the group owner of a file or directory. | `sudo chgrp developers script.sh` |
| `umask` | Sets the default permissions for newly created files and directories. | `umask 022` |

<br>

#### User Information Commands

| Command | Description |
|:---|:---|
| `id` | Display user ID (UID), group ID (GID), and the groups the user belongs to. |
| `who` | Show which users are currently logged into the system. |
| `w` | Show logged-in users and what they are doing. |
| `users` | Display the usernames of all current users on a single line. |
| `groups` | Display the groups the current user is a member of. |
| `last` | Show a log of the last user logins. |
| `lastlog` | Show information about the most recent login for each user. |
| `chage` | Change user password expiry information. |

#### User and Group Management Commands

| Command | Description |
|:---|:---|
| `su` | **S**witch **U**ser - Switch to another user account (becomes root if no name is specified). |
| `passwd` | Change a user's password. |
| `useradd` | Add a new user to the system. |
| `usermod` | Modify an existing user's properties. |
| `userdel` | Delete a user account. |
| `groupadd` | Add a new group. |
| `groupdel` | Delete a group. |
| `gpasswd` | Administer groups (e.g., add or delete members). |

#### Advanced Permissions Commands (ACL & SELinux)

| Command | Description |
|:---|:---|
| `sudo visudo` | Safely edit the `/etc/sudoers` file to grant `sudo` privileges. |
| `getfacl` | Get File Access Control Lists. |
| `setfacl` | Set File Access Control Lists. |
| `sestatus` | Show the current status of SELinux on the system. |
| `chcon` | Change the SELinux security context of a file. |
| `restorecon` | Restore the default SELinux security context of a file. |

<a id="networking"></a>
## 🌐 3. Networking Commands
| Command | Description | Example |
|:---|:---|:---|
| `ping` | Used to test the connection to another host on the network by sending ICMP packets and waiting for a response. | `ping google.com` |
| `ip a` | (replaces `ifconfig`) Displays detailed information about network interfaces and their IP addresses. | `ip a` |
| `netstat` | **Net**work **Stat**istics - Displays information about network connections, routing tables, and interface statistics. | `netstat -tuln` (to show open ports) |

<br>

#### Additional Networking Commands

| Command | Description | Example |
|:---|:---|:---|
| `ifconfig` | Display/configure network interfaces (considered legacy; `ip` is the modern replacement). | `ifconfig` |
| `traceroute` | Trace the packet route to a host to show the hops between devices. | `traceroute google.com` |
| `ssh` | **S**ecure **Sh**ell - Securely log into a remote host. | `ssh user@hostname` |
| `scp` | **S**ecure **C**o**p**y - Securely copy files over SSH. | `scp file.txt user@host:/path` |
| `rsync` | Efficiently synchronize files and directories between systems. | `rsync -avz /src /dest` |
| `wget` | A non-interactive tool for downloading files from the internet. | `wget https://example.com/file.zip` |
| `curl` | A powerful tool for transferring data to or from servers. | `curl -O https://example.com/file.zip` |
| `ss` | (replaces `netstat`) A utility to investigate sockets. | `ss -tuln` |
| `dig` | An advanced tool for querying DNS servers. | `dig google.com` |
| `host` | A simple DNS lookup utility (easier than `dig`). | `host google.com` |
| `hostname` | Show or set the system's hostname. | `hostname` |
| `nmap` | A powerful tool for network scanning and host discovery. | `nmap -sT 192.168.1.1` |
| `nmcli` | Command-line interface for controlling NetworkManager. | `nmcli device status` |
| `firewall-cmd` | Command-line interface for firewalld (on RHEL/Fedora systems). | `firewall-cmd --list-all` |
| `nslookup` | Query Internet name servers ( `dig` and `host` are preferred). | `nslookup google.com` |
| `ftp` | File Transfer Protocol (insecure; `scp` or `sftp` are preferred). | `ftp hostname` |

<a id="processes"></a>
## ⚙️ 4. Process Commands
| Command | Description | Example |
|:---|:---|:---|
| `ps` | **P**rocess **S**tatus - Displays a list of currently running processes. | `ps aux` (to show all processes) |
| `top` | Displays a live, interactive view of processes and their resource consumption (CPU, memory). | `top` |
| `htop` | A more user-friendly, colorful, and interactive alternative to `top`. | `htop` |
| `kill` | Used to forcibly terminate a specific process using its Process ID (PID). | `kill 1234` |

<br>

#### Additional Process Control Commands

| Command | Description | Example |
|:---|:---|:---|
| `pgrep` | Searches for processes by name or other attributes and displays their PIDs. | `pgrep firefox` |
| `pkill` | Sends a signal to processes by name, without needing the PID. | `pkill -9 firefox` |
| `killall` | Kills all processes with a specific name. | `killall -9 firefox` |
| `nice` | Execute a new command with a specific priority level. | `nice -n 10 ./my_script.sh` |
| `renice` | Modify the priority of a currently running process. | `renice 15 -p 1234` |
| `jobs` | Lists processes running in the background or stopped. | `jobs -l` |
| `bg` | Sends a suspended process to run in the background. | `bg %1` |
| `fg` | Brings a background process to the foreground to interact with it. | `fg %1` |
| `nohup` | **No H**ang **Up** - Run a process that continues to run even after closing the terminal. | `nohup ./long_script.sh &` |
| `systemctl` | The main tool for managing services in `systemd` systems. | `sudo systemctl start httpd` |
| `pstree` | Display running processes as a tree to show their relationships. | `pstree` |
| `uptime` | Show how long the system has been running, number of users, and load average. | `uptime` |
| `lsof` | **L**i**s**t **O**pen **F**iles - Show currently open files and the processes using them. | `sudo lsof -i :80` |

<a id="package-management"></a>
## 📦 5. Package Management Commands
A package manager is an essential tool in any Linux distribution, allowing you to easily install, update, and remove software. Each distribution family has its own package manager.

### For Debian/Ubuntu Systems (using `apt`)
| Command | Description |
|:---|:---|
| `sudo apt update` | Update the list of available packages. |
| `sudo apt upgrade` | Upgrade all installed packages to their latest versions. |
| `sudo apt install <package_name>` | Install a new package. |
| `sudo apt remove <package_name>` | Remove a specific package. |
| `apt search <keyword>` | Search for a package. |

### For Fedora/CentOS Systems (using `dnf`)
| Command | Description |
|:---|:---|
| `sudo dnf upgrade` | Upgrade all packages. |
| `sudo dnf install <pkg>` | Install a new package. |
| `sudo dnf remove <pkg>` | Remove a package. |
| `dnf search <keyword>` | Search repositories for a package. |
| `dnf info <pkg>` | Display detailed information about a package. |
| `dnf list installed` | List all installed packages. |
| `dnf history` | View the history of dnf transactions (install, remove, update). |
| `dnf provides <file>` | Find which package provides a specific file. |
| `sudo dnf autoremove` | Remove packages that were installed as dependencies and are no longer needed. |
| `sudo dnf groupinstall <group>` | Install a predefined group of packages (e.g., "Development Tools"). |

### `rpm` Commands (for RHEL/Fedora/CentOS systems)
`rpm` is the underlying package manager that `dnf` uses. It is sometimes used to handle `.rpm` files directly.

| Command | Description |
|:---|:---|
| `rpm -qa` | **Q**uery **A**ll - List all installed packages. |
| `sudo rpm -ivh <file.rpm>` | **I**nstall, **V**erbose, **H**ash - Install a package from a local `.rpm` file. |
| `sudo rpm -e <pkg>` | **E**rase - Remove a package (does not resolve dependencies). |
| `rpm -qf <file>` | **Q**uery **F**ile - Query which package a specific file belongs to. |

### For Arch Linux Systems (using `pacman`)
| Command | Description |
|:---|:---|
| `sudo pacman -Syu` | Synchronize and fully update the system. |
| `sudo pacman -S <package_name>` | Install a new package. |
| `sudo pacman -Rns <package_name>` | Remove a package and its dependencies. |
| `pacman -Ss <keyword>` | Search for a package. |

### `flatpak` Commands (for containerized apps)
`flatpak` is a system for building, distributing, and running sandboxed desktop applications.

| Command | Description |
|:---|:---|
| `flatpak install <app>` | Install an application. |
| `flatpak update` | Update all applications. |
| `flatpak run <app-id>` | Run an application. |
| `flatpak list` | List installed applications. |

<a id="text-search"></a>
## 🔍 6. Text & Search Commands
| Command | Description | Example |
|:---|:---|:---|
| `grep` | **G**lobal **R**egular **E**xpression **P**rint - Searches for a specific text pattern within one or more files. | `grep "error" log.txt` |
| `find` | Used to search for files and directories based on various criteria like name, size, or modification date. | `find /home -name "*.log"` |
| `sed` | **S**tream **Ed**itor - A powerful tool for editing text directly from the command line, such as replacing specific words. | `sed 's/old/new/g' file.txt` |

<br>

#### Advanced Text Processing Tools

| Command | Description | Example |
|:---|:---|:---|
| `grep -r` | Searches recursively in the current directory and all subdirectories. | `grep -r "config" /etc` |
| `grep -i` | Performs a case-insensitive search. | `grep -i "error" log.txt` |
| `grep -v` | Displays all lines that do **not** match the specified pattern. | `grep -v "debug" log.txt` |
| `awk` | A mini-programming language for text processing, very powerful for handling tabular data. | `awk '{print $1, $NF}' data.txt` (prints the first and last field of each line) |

<a id="shell"></a>
## 🐚 7. Shell Commands
Commands to control the shell environment itself, customize it, and get help.

| Command | Description |
|:---|:---|
| `alias` | Create a shortcut (an alias) for a long command. |
| `unalias` | Remove an alias. |
| `export` | Set an environment variable to make it available to child processes. |
| `env` | Display all current environment variables. |
| `history` | Display the history of executed commands. |
| `which` | Locate the full path of a command's executable. |
| `type` | Determine a command's type (builtin, alias, external file). |
| `source` | Execute commands from a file in the current shell (useful for updating settings). |
| `echo` | Print text or a variable's value to the screen. |
| `set` / `unset` | Set or unset shell options and variables. |
| `man` | **Man**ual - Display the detailed manual pages for a command. |
| `info` | Read documentation in Info format (sometimes more detailed than `man`). |
| `apropos` | Search the names and descriptions of manual pages for a keyword. |
| `clear` | Clear the terminal screen. |
| `exit` | Exit the current shell. |

<a id="scripting"></a>
## 📜 8. Scripting Commands
Scripting is a way to automate repetitive tasks. These commands are the basic building blocks for many scripts.

| Command | Description |
|:---|:---|
| `echo` / `printf` | To print text and variables. `printf` provides more control over formatting. |
| `read` | Read input from the user and store it in a variable. |
| `test` | Check conditions (e.g., `test -f "file.txt"` to check if a file exists). |
| `cut` | Extract sections (columns) from each line of input. |
| `head` / `tail` | Display the first or last lines of a file. |
| `sort` | Sort lines of text files. |
| `uniq` | Remove adjacent duplicate lines from a sorted file. |
| `wc` | **W**ord **C**ount - Count lines, words, and characters. |
| `tr` | **Tr**anslate - Translate or delete characters from a text stream. |
| `tee` | Read from standard input and write to standard output and a file simultaneously. |
| `xargs` | Build and execute command lines from standard input. |
| `diff` | Compare files line by line to show differences. |
| `cron` / `crontab` | Schedule tasks and scripts to run periodically at specified times. |

### Example of a Simple Bash Script

1.  Create a new file named `my_script.sh`.
2.  Add the following content to the file:
    ```bash
    #!/bin/bash
    # This is a simple script to say hello
    NAME="Ali"
    echo "Hello, $NAME! Welcome to scripting."
    ```
3.  Give the file execute permission: `chmod +x my_script.sh`
4.  Run the script: `./my_script.sh`

<a id="development"></a>
## 💻 9. Development Commands
| Command | Description |
|:---|:---|
| `git` | A version control system for managing source code. |
| `gcc` / `g++` | C and C++ compilers from the GNU Compiler Collection. |
| `make` | A tool for automating the process of building software from source code. |
| `cmake` | A cross-platform build system used to generate standard build files (like Makefiles). |
| `ninja` | A small build system with a focus on speed, often used with `cmake`. |
| `docker` | A platform for creating, deploying, and running applications in containers. |
| `gdb` | **G**NU **D**e**b**ugger - The standard debugger for programs. |
| `valgrind` | A tool for memory debugging and profiling. |
| `strace` | Trace system calls and signals for program debugging. |
| `ldd` | Show the shared libraries required by an executable. |
| `perf` | A powerful performance analysis tool for Linux. |
| `python` | The interpreter for the Python programming language. |
| `java` | The Java environment runner for executing Java applications. |

<a id="system-monitoring"></a>
## 🖥️ 10. System Monitoring & Hardware
Commands to learn more about your system's hardware and monitor its health.

| Command | Description | Example |
|:---|:---|:---|
| `dmesg` | Displays kernel messages from boot-up, useful for diagnosing hardware issues. | `dmesg \| grep -i error` |
| `journalctl` | A tool for querying and displaying logs from `journald`, the systemd journal manager. | `journalctl -u sshd.service` |
| `lscpu` | Displays information about the CPU. | `lscpu` |
| `lsblk` | Displays information about block devices (like hard drives and their partitions). | `lsblk` |
| `free` | Displays the amount of used and available RAM in the system. | `free -h` |

<a id="useful-tools"></a>
## ✨ 11. Useful Tools
This is a list of additional tools (often not installed by default) that greatly enhance the command-line experience. You can install them using your distribution's package manager.

| Tool | Description |
|:---|:---|
| `htop` | An interactive and colorful alternative to the `top` command for process monitoring. |
| `ncdu` | **NC**urses **D**isk **U**sage - A great tool for analyzing disk space usage with an easy interface. |
| `tldr` | **T**oo **L**ong; **D**idn't **R**ead - Gives you very short and practical examples of how to use a command, simpler than `man`. |
| `bat` | A modern alternative to the `cat` command with syntax highlighting and line numbers. |
| `exa` | A modern alternative to the `ls` command with better colors, a tree view, and icons. |
| `neofetch` | A fun tool to display system information and your distribution's logo artfully in the terminal. |
| `fzf` | **F**u**z**zy **F**inder - An indispensable interactive search tool for the command line, allowing you to find files or commands at lightning speed. |
| `ripgrep` (`rg`) | A very fast alternative to the `grep` command, excellent for searching within software project content. |
