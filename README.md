Here’s the content formatted as a GitHub README file:

# Fail2Ban Configuration Guide

This guide explains how to configure **Fail2Ban** to monitor log files and ban IPs showing malicious activity. Steps are provided separately for **Ubuntu Server**.

---

## Steps for Ubuntu Server

### 1. Install Fail2Ban
```bash
sudo apt update
sudo apt install fail2ban -y

2. Configure Fail2Ban

    Create a local configuration:

sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

Edit the configuration file:

sudo nano /etc/fail2ban/jail.local

Set default parameters in [DEFAULT]:

bantime = 1h
findtime = 10m
maxretry = 5

Enable the SSH jail (or others if needed):

    [sshd]
    enabled = true
    logpath = /var/log/auth.log
    maxretry = 3

3. Test and Restart Fail2Ban

    Check syntax:

sudo fail2ban-client -t

Restart the service:

    sudo systemctl restart fail2ban

4. Enable Fail2Ban on Boot

sudo systemctl enable fail2ban

5. Monitor and Manage Fail2Ban

    View status:

sudo fail2ban-client status
sudo fail2ban-client status sshd

Unban an IP (if needed):

sudo fail2ban-client unban <IP_ADDRESS>
