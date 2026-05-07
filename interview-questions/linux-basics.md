# Linux Basics — Interview Questions

> Common interview questions and model answers for Linux system administration roles.

---

## 1. File System & Permissions

**Q: Explain the Linux file permission structure.**

**A:** Linux permissions are defined for three groups: owner, group, and others. Each has read (4), write (2), and execute (1) permissions. A file with `755` means the owner has full access (7 = 4+2+1), while group and others have read and execute (5 = 4+1).

**Q: What is the difference between `chmod` and `chown`?**

**A:** `chmod` changes file permissions (who can read, write, execute), while `chown` changes the owner and group of a file.

**Q: Where are system logs typically stored?**

**A:** On Debian/Ubuntu: `/var/log/syslog`. On RHEL/CentOS: `/var/log/messages`. Authentication logs are in `/var/log/auth.log`.

## 2. Process Management

**Q: How do you check running processes and resource usage?**

**A:** `ps aux` lists all processes. `top` and `htop` show real-time resource usage. `free -h` shows memory, and `df -h` shows disk usage.

**Q: What is the difference between `kill` and `kill -9`?**

**A:** `kill` sends SIGTERM (15), allowing graceful shutdown. `kill -9` sends SIGKILL, forcing immediate termination without cleanup.

## 3. Package Management

**Q: What is the difference between `apt` and `dpkg`?**

**A:** `dpkg` installs individual `.deb` packages but does not resolve dependencies. `apt` is a higher-level tool that handles dependencies, repositories, and updates automatically.

**Q: How do you list installed packages on a RHEL system?**

**A:** `rpm -qa` or `dnf list installed`.

## 4. Networking

**Q: How do you check the IP address and routing table?**

**A:** `ip addr` for IP addresses, `ip route` for the routing table. Legacy commands: `ifconfig` and `route -n`.

**Q: What is the purpose of `/etc/resolv.conf`?**

**A:** It specifies the DNS servers the system uses for name resolution.

## 5. Service Management

**Q: How do you start, stop, and enable a service with systemd?**

**A:**
```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl enable nginx  # start at boot
```

**Q: Where do you view service logs?**

**A:** `sudo journalctl -u service-name` or `/var/log/` for legacy systems.

---

## Practice Tip

When answering, structure your response: state the command or concept, explain what it does, and give a practical example.
