<div align="center">

<h1>🐧 100 Linux Commands</h1>

<p><strong>100 Commands Every Linux User Should Know</strong></p>

<p>Learn the everyday Linux toolbox: one command, one line, one example at a time.</p>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#contributing)
[![Made with Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg?logo=markdown)](https://commonmark.org/)

</div>

---

## 🎯 Who This Is For

This guide is for beginner-to-intermediate Linux users who want a practical, no-fluff cheat sheet. Skim the table of contents, jump to a category, and copy the examples into your terminal. Everything targets **Ubuntu/Debian** by default; short **Distro note** lines call out where **Fedora** (`dnf`) or **Arch** (`pacman`) differ.

> [!TIP]
> Examples use made-up names like `notes.txt`, `~/projects/blog`, and the user `alice`. Swap in your own files, users, and hostnames before running anything.

## 📚 Table of Contents

1. [Navigation & Files](#navigation-files) (1–10)
2. [Viewing & Editing Text](#viewing-editing-text) (11–18)
3. [Searching](#searching) (19–24)
4. [Text Processing](#text-processing) (25–32)
5. [Permissions & Ownership](#permissions-ownership) (33–38)
6. [Users & Groups](#users-groups) (39–44)
7. [Processes & Jobs](#processes-jobs) (45–51)
8. [System Info](#system-info) (52–58)
9. [Disk & Storage](#disk-storage) (59–66)
10. [Networking](#networking) (67–73)
11. [Package Management](#package-management) (74–77)
12. [Archives & Compression](#archives-compression) (78–83)
13. [Services & Logs (systemd)](#services-logs) (84–88)
14. [SSH & Security](#ssh-security) (89–94)
15. [Shell Productivity](#shell-productivity) (95–100)
16. [Bonus: Keyboard Shortcuts](#keyboard-shortcuts)
17. [Contributing](#contributing)
18. [License](#license)
19. [Star This Repo](#star)

---

<a id="navigation-files"></a>

## 📁 Navigation & Files

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 1 | `pwd` | Shows the directory you are in | `pwd` |
| 2 | `ls` | Lists files and folders | `ls -lah ~/Documents` |
| 3 | `cd` | Moves you to another directory | `cd ~/projects/blog` |
| 4 | `mkdir` | Creates directories | `mkdir -p ~/projects/blog/assets/images` |
| 5 | `touch` | Creates an empty file or updates its timestamp | `touch notes.txt` |
| 6 | `cp` | Copies files or folders | `cp -r ~/projects/blog ~/projects/blog-copy` |
| 7 | `mv` | Moves or renames files | `mv draft.txt final-report.txt` |
| 8 | `rm` | Deletes files | `rm old-notes.txt` |
| 9 | `rmdir` | Removes an empty directory | `rmdir empty-folder` |
| 10 | `ln` | Creates a link to a file | `ln -s ~/projects/blog/config.yml ~/config-link.yml` |

> [!WARNING]
> **`rm -rf` deletes immediately and permanently.** There is no trash can, and a stray space or a wrong variable (for example `rm -rf ~/ projects`) can wipe your home directory. Preview what a pattern matches first, and ask for confirmation when deleting folders:
>
> ```bash
> ls ~/projects/old-site
> rm -ri ~/projects/old-site
> ```

> **Pro tip:** `cd -` jumps back to the previous directory, and `ls -lt` lists the newest files first.

---

<a id="viewing-editing-text"></a>

## 📖 Viewing & Editing Text

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 11 | `cat` | Prints a file to the screen | `cat /etc/os-release` |
| 12 | `less` | Scrolls through a file one page at a time | `less /etc/services` |
| 13 | `head` | Shows the first lines of a file | `head -n 5 access.log` |
| 14 | `tail` | Shows the last lines of a file | `tail -n 20 app.log` |
| 15 | `nano` | Beginner-friendly terminal editor | `nano ~/.bashrc` |
| 16 | `vim` | Powerful modal terminal editor | `vim config.yml` |
| 17 | `wc` | Counts lines, words, or bytes | `wc -l access.log` |
| 18 | `diff` | Shows differences between two files | `diff -u config.old config.new` |

*Distro note:* Ubuntu ships only a minimal `vim`; install the full version with `sudo apt install vim` (Fedora: `sudo dnf install vim-enhanced`, Arch: `sudo pacman -S vim`).

> **Pro tip:** `tail -f app.log` follows a file as it grows. Inside `less`, press `/` to search and `q` to quit.

---

<a id="searching"></a>

## 🔍 Searching

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 19 | `grep` | Finds lines that match a pattern | `grep -rin "error" ~/projects/blog` |
| 20 | `find` | Locates files by name, type, or age | `find ~/Documents -name "*.pdf" -mtime -7` |
| 21 | `locate` | Finds files fast using a prebuilt index | `locate nginx.conf` |
| 22 | `which` | Shows the path of a command | `which python3` |
| 23 | `whereis` | Finds a command's binary and man page | `whereis ssh` |
| 24 | `type` | Tells you if a name is an alias, builtin, or program | `type ls` |

*Distro note:* `locate` needs the `plocate` package and an index. Ubuntu: `sudo apt install plocate`; Fedora: `sudo dnf install plocate`; Arch: `sudo pacman -S plocate`. Then run `sudo updatedb` once.

> **Pro tip:** `grep -rn --include="*.py" "TODO" .` searches only Python files and shows line numbers.

---

<a id="text-processing"></a>

## ✂️ Text Processing

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 25 | `sort` | Sorts lines of text | `sort -n scores.txt` |
| 26 | `uniq` | Collapses or counts repeated adjacent lines | `uniq -c sorted-names.txt` |
| 27 | `cut` | Extracts columns from delimited text | `cut -d',' -f1,3 users.csv` |
| 28 | `tr` | Swaps or deletes characters | `tr 'a-z' 'A-Z' < notes.txt` |
| 29 | `sed` | Find-and-replace on a stream of text | `sed 's/colour/color/g' notes.txt` |
| 30 | `awk` | Picks and transforms fields per line | `awk '{print $1}' access.log` |
| 31 | `xargs` | Turns a list of names into command arguments | `xargs -a filenames.txt wc -l` |
| 32 | `tee` | Writes output to the screen and a file | `ls -l \| tee listing.txt` |

> **Pro tip:** `sort access.log | uniq -c | sort -nr | head` is a classic "top 10 most frequent lines" pipeline. Note that `uniq` only merges *adjacent* duplicates, so sort first.

---

<a id="permissions-ownership"></a>

## 🔐 Permissions & Ownership

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 33 | `chmod` | Changes who can read, write, or run a file | `chmod +x deploy.sh` |
| 34 | `chown` | Changes a file's owner and group | `sudo chown alice:developers report.txt` |
| 35 | `chgrp` | Changes a file's group | `sudo chgrp developers project-notes.txt` |
| 36 | `umask` | Sets default permissions for new files | `umask 022` |
| 37 | `stat` | Shows detailed file info, including permissions | `stat report.txt` |
| 38 | `file` | Identifies what kind of file something is | `file photo.jpg` |

> [!WARNING]
> **`chmod -R 777` (or any `-R` on a broad path) is dangerous.** It makes everything readable, writable, and executable by everyone, and recursive changes on system directories can break your OS. Change only the files you mean to, with sensible modes:
>
> ```bash
> find ~/projects/blog -type f -exec chmod 644 {} +
> find ~/projects/blog -type d -exec chmod 755 {} +
> ```

> **Pro tip:** Symbolic modes are easier to read than numbers: `chmod u+x,g-w script.sh` adds execute for you and removes write from the group.

---

<a id="users-groups"></a>

## 👥 Users & Groups

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 39 | `whoami` | Prints your current username | `whoami` |
| 40 | `id` | Shows a user's ID and group memberships | `id alice` |
| 41 | `sudo` | Runs a command with administrator rights | `sudo apt update` |
| 42 | `su` | Switches to another user | `su - alice` |
| 43 | `useradd` | Creates a new user account | `sudo useradd -m -s /bin/bash alice` |
| 44 | `passwd` | Sets or changes a password | `sudo passwd alice` |

*Distro note:* Debian/Ubuntu also include `adduser`, a friendlier wrapper that asks for the password and details interactively: `sudo adduser alice`.

> **Pro tip:** `sudo -l` lists exactly what you are allowed to run with `sudo`, and `sudo !!` re-runs your previous command with `sudo`.

---

<a id="processes-jobs"></a>

## ⚙️ Processes & Jobs

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 45 | `ps` | Lists running processes | `ps aux` |
| 46 | `top` | Live view of CPU and memory use | `top` |
| 47 | `htop` | Friendlier, colorful version of `top` | `htop` |
| 48 | `kill` | Sends a signal (usually "stop") to a process by PID | `kill 4821` |
| 49 | `pkill` | Signals processes by name | `pkill firefox` |
| 50 | `pgrep` | Finds process IDs by name | `pgrep -l nginx` |
| 51 | `nohup` | Keeps a command running after you log out | `nohup python3 backup.py &` |

> [!WARNING]
> **`kill -9` cannot be caught or cleaned up.** The process dies instantly, so it can leave corrupted files, stale lock files, or orphaned child processes. Start with a polite request and escalate only if needed:
>
> ```bash
> kill 4821       # SIGTERM: lets the program shut down cleanly
> kill -9 4821    # SIGKILL: last resort only
> ```

*Distro note:* `htop` is not preinstalled. Ubuntu: `sudo apt install htop`; Fedora: `sudo dnf install htop`; Arch: `sudo pacman -S htop`.

> **Pro tip:** `ps aux --sort=-%mem` lists processes by memory use, biggest first. Inside `top`, press `q` to quit.

---

<a id="system-info"></a>

## 🖥️ System Info

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 52 | `uname` | Shows kernel and system details | `uname -a` |
| 53 | `uptime` | Shows how long the system has been running | `uptime -p` |
| 54 | `date` | Prints or formats the date and time | `date +"%Y-%m-%d %H:%M"` |
| 55 | `hostname` | Shows the machine's name | `hostname` |
| 56 | `lscpu` | Summarizes your CPU | `lscpu` |
| 57 | `free` | Shows memory and swap usage | `free -h` |
| 58 | `hostnamectl` | Shows OS, kernel, and hostname together | `hostnamectl` |

> **Pro tip:** The `-h` flag ("human-readable") works on many commands, such as `free -h`, `df -h`, and `ls -lh`, and prints sizes like `4.2G` instead of raw bytes.

---

<a id="disk-storage"></a>

## 💾 Disk & Storage

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 59 | `df` | Shows free space on mounted disks | `df -h` |
| 60 | `du` | Shows how much space a folder uses | `du -sh ~/Downloads` |
| 61 | `lsblk` | Lists disks and partitions | `lsblk` |
| 62 | `mount` | Attaches a filesystem to a folder | `sudo mount /dev/sdb1 /mnt/usb` |
| 63 | `umount` | Safely detaches a filesystem | `sudo umount /mnt/usb` |
| 64 | `fdisk` | Views or edits partition tables | `sudo fdisk -l` |
| 65 | `dd` | Copies raw data block by block | `dd if=/dev/zero of=testfile.img bs=1M count=100 status=progress` |
| 66 | `mkfs` | Formats a partition with a filesystem | `sudo mkfs.ext4 -n /dev/sdb1` |

> [!WARNING]
> **`dd` and `mkfs` overwrite data with no confirmation.** One wrong device name (`of=/dev/sda` instead of your USB stick) destroys a whole disk, and `mkfs` erases everything on the target partition. The examples above are safe: the `dd` one writes a harmless 100 MB test file, and `mkfs.ext4 -n` only *simulates* formatting.
>
> Before any real run, identify the device with `lsblk -f` and re-read the command twice. To write an ISO to a USB drive, a GUI tool such as GNOME Disks or balenaEtcher is a safer choice.

> **Pro tip:** `lsblk -f` adds filesystem types, labels, and UUIDs, which helps you pick the right device. `du -h --max-depth=1 ~` shows what is eating your home folder.

---

<a id="networking"></a>

## 🌐 Networking

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 67 | `ping` | Tests whether a host is reachable | `ping -c 4 example.com` |
| 68 | `ip` | Shows and configures network interfaces | `ip -br addr` |
| 69 | `ss` | Lists open ports and connections | `ss -tulpn` |
| 70 | `curl` | Transfers data to or from a URL | `curl -I https://example.com` |
| 71 | `wget` | Downloads files from the web | `wget https://example.com/report.pdf` |
| 72 | `dig` | Looks up DNS records | `dig +short example.com` |
| 73 | `traceroute` | Shows the network hops to a host | `traceroute example.com` |

*Distro note:* `dig` and `traceroute` may need installing. Ubuntu: `sudo apt install dnsutils traceroute`; Fedora: `sudo dnf install bind-utils traceroute`; Arch: `sudo pacman -S bind traceroute`.

> **Pro tip:** Run `sudo ss -tulpn` (with `sudo`) to see *which program* owns each listening port. `curl -L -o setup.sh https://example.com/setup.sh` follows redirects and saves to a file you can read before running.

---

<a id="package-management"></a>

## 📦 Package Management

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 74 | `apt` | Installs and updates software (Debian/Ubuntu) | `sudo apt update && sudo apt install htop` |
| 75 | `dpkg` | Inspects installed `.deb` packages (Debian/Ubuntu) | `dpkg -l htop` |
| 76 | `snap` | Manages Snap packages (Ubuntu) | `snap list` |
| 77 | `flatpak` | Manages Flatpak apps (any distro) | `flatpak search vlc` |

**Distro note: equivalents for everyday tasks**

| Task | Debian/Ubuntu | Fedora | Arch |
|------|---------------|--------|------|
| Update everything | `sudo apt update && sudo apt upgrade` | `sudo dnf upgrade` | `sudo pacman -Syu` |
| Install a package | `sudo apt install htop` | `sudo dnf install htop` | `sudo pacman -S htop` |
| Remove a package | `sudo apt remove htop` | `sudo dnf remove htop` | `sudo pacman -R htop` |
| Search for a package | `apt search htop` | `dnf search htop` | `pacman -Ss htop` |

> **Pro tip:** `apt list --upgradable` previews pending updates before you run `sudo apt upgrade`. On Ubuntu, install Flatpak itself with `sudo apt install flatpak`.

---

<a id="archives-compression"></a>

## 🗜️ Archives & Compression

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 78 | `tar` | Bundles files into one archive | `tar -czf backup.tar.gz ~/Documents` |
| 79 | `gzip` | Compresses a file with gzip | `gzip -k access.log` |
| 80 | `gunzip` | Decompresses `.gz` files | `gunzip access.log.gz` |
| 81 | `zip` | Creates a `.zip` archive | `zip -r project.zip ~/projects/blog` |
| 82 | `unzip` | Extracts a `.zip` archive | `unzip project.zip -d ~/restore` |
| 83 | `xz` | Compresses with a higher ratio than gzip | `xz -k big-dump.sql` |

*Distro note:* `zip` and `unzip` are separate packages on most systems: `sudo apt install zip unzip` (Fedora: `sudo dnf install zip unzip`, Arch: `sudo pacman -S zip unzip`).

> **Pro tip:** Remember tar as **c**reate, **x**tract, **t**est/list: `tar -tzf backup.tar.gz` previews contents, and `tar -xzf backup.tar.gz -C ~/restore` extracts into an existing folder.

---

<a id="services-logs"></a>

## 📜 Services & Logs (systemd)

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 84 | `systemctl` | Starts, stops, and inspects services | `systemctl list-units --type=service --state=running` |
| 85 | `journalctl` | Reads the system log | `journalctl -p err -b` |
| 86 | `service` | Older-style service control (Debian/Ubuntu) | `service --status-all` |
| 87 | `crontab` | Schedules recurring jobs | `crontab -e` |
| 88 | `timedatectl` | Shows or sets time and timezone | `timedatectl` |

A sample `crontab -e` line that runs a backup script every day at 02:00:

```cron
0 2 * * * /home/alice/backup.sh
```

*Distro note:* Service names can differ. The SSH service is `ssh` on Ubuntu/Debian and `sshd` on Fedora/Arch, so `sudo systemctl status ssh` becomes `sudo systemctl status sshd` there.

> **Pro tip:** `journalctl -f -u nginx` follows one service's log live. `sudo systemctl enable --now nginx` starts a service *and* makes it start at boot.

---

<a id="ssh-security"></a>

## 🛡️ SSH & Security

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 89 | `ssh` | Opens a secure shell on another machine | `ssh alice@192.168.1.50` |
| 90 | `scp` | Copies files over SSH | `scp report.pdf alice@192.168.1.50:~/documents/` |
| 91 | `rsync` | Syncs folders efficiently, only sending changes | `rsync -avh --progress ~/projects/blog/ alice@192.168.1.50:~/backup/blog/` |
| 92 | `ssh-keygen` | Generates an SSH key pair | `ssh-keygen -t ed25519 -C "alice@laptop"` |
| 93 | `ssh-copy-id` | Installs your public key on a server | `ssh-copy-id alice@192.168.1.50` |
| 94 | `ufw` | Simple firewall front end (Ubuntu) | `sudo ufw status verbose` |

> [!CAUTION]
> **Do not enable `ufw` over SSH before allowing SSH.** You can lock yourself out of a remote server. Allow it first, then enable:
>
> ```bash
> sudo ufw allow OpenSSH
> sudo ufw enable
> ```

*Distro note:* Fedora uses `firewalld` (`sudo firewall-cmd --list-all`) instead of `ufw`. On Arch, install `ufw` with `sudo pacman -S ufw`.

> **Pro tip:** Add `-n` (`--dry-run`) to `rsync -avh` to preview what would be copied before transferring anything. A trailing `/` on the source copies the folder's *contents*.

---

<a id="shell-productivity"></a>

## 🚀 Shell Productivity

| # | Command | What it does | Example |
|---|---------|--------------|---------|
| 95 | `man` | Opens the manual for a command | `man grep` |
| 96 | `history` | Lists commands you ran before | `history 20` |
| 97 | `alias` | Creates a shortcut for a long command | `alias ll='ls -lah'` |
| 98 | `echo` | Prints text or variable values | `echo "Hello, $USER"` |
| 99 | `export` | Sets an environment variable for child programs | `export EDITOR=nano` |
| 100 | `source` | Reloads a script or config in the current shell | `source ~/.bashrc` |

> **Pro tip:** Aliases and exports vanish when you close the terminal. Add them to `~/.bashrc`, then run `source ~/.bashrc` to apply them right away. Inside `man`, press `/` to search and `q` to quit.

---

<a id="keyboard-shortcuts"></a>

## ⌨️ Bonus: Keyboard Shortcuts

These work in Bash (the default shell on Ubuntu/Debian) and most other shells.

| Shortcut | What it does |
|----------|--------------|
| `Ctrl+R` | Search your command history as you type |
| `Ctrl+C` | Stop the running command |
| `Ctrl+D` | Log out or close the shell (end of input) |
| `Ctrl+Z` | Pause the running command (resume with `fg`) |
| `Ctrl+L` | Clear the screen |
| `Ctrl+A` / `Ctrl+E` | Jump to the start / end of the line |
| `Ctrl+U` / `Ctrl+K` | Delete from the cursor to the start / end of the line |
| `Ctrl+W` | Delete the word before the cursor |
| `Tab` | Autocomplete commands and file names (press twice to list options) |
| `↑` / `↓` | Step through previous commands |
| `!!` | Repeat the last command (for example `sudo !!`) |
| `!$` | Reuse the last argument of the previous command |
| `Alt+.` | Insert the last argument of the previous command |

---

<a id="contributing"></a>

## 🤝 Contributing

Contributions are welcome! To keep the list at exactly 100 commands:

1. Fork the repo and create a branch (`git checkout -b improve-grep-example`).
2. Fix typos, sharpen descriptions, or improve examples. Examples must be safe to copy-paste.
3. To propose a new command, swap it with an existing one and explain why it is more useful.
4. Keep everyday essentials ahead of exotic tools, and label anything distro-specific.
5. Open a pull request with a short summary of your change.

<a id="license"></a>

## 📄 License

This project is released under the [MIT License](https://opensource.org/licenses/MIT). You are free to use, copy, modify, and share it, with attribution.

<a id="star"></a>

## ⭐ Star This Repo

If this guide saved you a trip to the man pages, please give the repo a **star** and share it with a friend who is learning Linux. It helps others find it.

<div align="center">

Happy hacking! 🐧

</div>
