# Troubleshooting Scenarios

> Scenario-based questions and structured answers for IT support interviews.

---

## Scenario 1: Server Slow

**Problem:** Users report a Linux server is extremely slow.

**Answer Structure:**

1. **Check resource usage**
   ```bash
   top -bn1 | head -n20
   free -h
   df -h
   ```

2. **Identify the culprit**
   - High CPU: find the process consuming CPU
   - High memory: check for memory leaks
   - High disk I/O: check for runaway logs or swap usage
   - Disk full: clean old logs or expand storage

3. **Check logs**
   ```bash
   sudo journalctl -xe | tail -n50
   ```

4. **Document and resolve**
   - Kill or restart the offending process
   - If disk full, archive old logs and configure log rotation

---

## Scenario 2: Website Down

**Problem:** The company website returns a 502 Bad Gateway.

**Answer Structure:**

1. **Check the web server**
   ```bash
   sudo systemctl status nginx
   sudo systemctl status apache2
   ```

2. **Check upstream service**
   - If using a reverse proxy, check the backend application
   - Test backend directly: `curl localhost:8080`

3. **Check logs**
   ```bash
   sudo tail -n50 /var/log/nginx/error.log
   ```

4. **Check resources**
   - Is the server out of memory?
   - Is the application process running?

5. **Restart if necessary**
   ```bash
   sudo systemctl restart nginx
   sudo systemctl restart app-service
   ```

---

## Scenario 3: User Cannot Log In

**Problem:** A user cannot log in via SSH.

**Answer Structure:**

1. **Check authentication logs**
   ```bash
   sudo tail -n20 /var/log/auth.log
   ```

2. **Verify user account**
   ```bash
   id username
   sudo passwd -S username
   ```

3. **Check SSH service**
   ```bash
   sudo systemctl status sshd
   sudo ss -tlnp | grep :22
   ```

4. **Check firewall**
   ```bash
   sudo iptables -L | grep 22
   sudo firewall-cmd --list-all
   ```

5. **Common causes**
   - Wrong password / expired account
   - SSH key permissions (`~/.ssh` should be 700, `authorized_keys` should be 600)
   - Firewall blocking port 22
   - SELinux or AppArmor restrictions

---

## Scenario 4: No Internet Access

**Problem:** A workstation has no internet connectivity.

**Answer Structure:**

1. Physical layer — cable, Wi-Fi, LEDs
2. `ip addr` — is an IP assigned?
3. `ip route` — is a default gateway set?
4. `ping <gateway>` — can the gateway be reached?
5. `ping 8.8.8.8` — is external connectivity available?
6. `nslookup google.com` — is DNS working?
7. Check proxy settings and browser configuration

---

## Key Framework

Always follow a structured approach:
- Gather information
- Isolate the layer or component
- Form a hypothesis
- Test safely
- Apply fix
- Verify resolution
- Document
