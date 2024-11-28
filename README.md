Here’s a step-by-step guide, **separated for Kali Linux** and **Ubuntu Server**:

---

### **Steps for Kali Linux**
1. **Install Fail2Ban:**
   ```bash
   sudo apt update
   sudo apt install fail2ban -y
   ```

2. **Configure Fail2Ban:**
   - Create a local configuration:
     ```bash
     sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
     ```
   - Edit the file:
     ```bash
     sudo nano /etc/fail2ban/jail.local
     ```
   - Set parameters in `[DEFAULT]`:
     ```ini
     bantime = 1h
     findtime = 10m
     maxretry = 5
     ```
   - Enable SSH jail (and others if needed):
     ```ini
     [sshd]
     enabled = true
     logpath = /var/log/auth.log
     maxretry = 3
     ```

3. **Test and Restart:**
   - Check syntax:
     ```bash
     sudo fail2ban-client -t
     ```
   - Restart the service:
     ```bash
     sudo systemctl restart fail2ban
     ```

4. **Monitor and Manage:**
   - View status:
     ```bash
     sudo fail2ban-client status
     sudo fail2ban-client status sshd
     ```
   - Unban IP if needed:
     ```bash
     sudo fail2ban-client unban <IP_ADDRESS>
     ```

---

### **Steps for Ubuntu Server**
1. **Install Fail2Ban:**
   ```bash
   sudo apt update
   sudo apt install fail2ban -y
   ```

2. **Configure Fail2Ban:**
   - Create a local configuration:
     ```bash
     sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
     ```
   - Edit the file:
     ```bash
     sudo nano /etc/fail2ban/jail.local
     ```
   - Set parameters in `[DEFAULT]`:
     ```ini
     bantime = 1h
     findtime = 10m
     maxretry = 5
     ```
   - Enable SSH jail (and others if needed):
     ```ini
     [sshd]
     enabled = true
     logpath = /var/log/auth.log
     maxretry = 3
     ```

3. **Test and Restart:**
   - Check syntax:
     ```bash
     sudo fail2ban-client -t
     ```
   - Restart the service:
     ```bash
     sudo systemctl restart fail2ban
     ```

4. **Enable Fail2Ban on Boot:**
   ```bash
   sudo systemctl enable fail2ban
   ```

5. **Monitor and Manage:**
   - View status:
     ```bash
     sudo fail2ban-client status
     sudo fail2ban-client status sshd
     ```
   - Unban IP if needed:
     ```bash
     sudo fail2ban-client unban <IP_ADDRESS>
     ```

---

### **Summary**
- **Kali Linux** and **Ubuntu Server** setups are nearly identical.
- For **Kali**, you may focus on protecting SSH, Apache, or other tools you run frequently.
- For **Ubuntu Server**, ensure it protects your server services like OpenSSH or web servers.
