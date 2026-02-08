# 🐧 Linux Command Cheat Sheet

---

## 🐧1. Process Management

- `ps aux` : Shows all running processes with CPU, memory, and state.

- `top` : Live view of CPU, memory usage, and running processes.

- `htop` : Enhanced interactive process viewer (if installed).

- `kill <PID>` : Sends a termination signal to a process.

- `kill -9 <PID>` : Forcefully kills a process (use with caution).

- `pkill <name>` : Kills processes by name.

- `nice` : Starts a process with a specific priority.

- `renice` : Changes priority of a running process.

- `pidof` : Finds PID of process by name.

- `uptime` : Shows system running time and load average.

---

## 🐧2. File System

- `df -h` - Displays disk space usage in human-readable format.

- `df -Th` - Shows filesystem type along with disk usage.

- `du -sh <dir>` - Shows total size of a directory.

- `ls -lh` - Lists files with permissions and sizes.

- `mount` - Displays mounted filesystems.

- `lsblk` - Shows block devices and disk layout.

- `find / -size +< size >` - Finds files larger than given size.

- `chmod` - Changes file permissions.

- `chown` - Changes file ownership.

---

## 🐧3. Networking Troubleshooting

- `ip addr` : Displays network interfaces and IP addresses.

- `ip route` : Shows routing table.

- `ping <host>` : Checks network connectivity to a host.

- `ss -tulnp` : Displays listening ports and services.

- `curl -I <url>` : Checks HTTP response headers.

- `dig <domain>` : Performs DNS lookup.

---

## Why these commands are important to hands-on/understand

These Linux commands are the most importanat for the **troubleshooting issues**.

- **Process management commands** helps to identify high CPU/memory usage, control/manage processes.
- **File system commands** helps to prevent outages caused by disk-full issues and permission problems.
- **Networking commands** helps to quickly diagnose connectivity, port, and DNS issues.
