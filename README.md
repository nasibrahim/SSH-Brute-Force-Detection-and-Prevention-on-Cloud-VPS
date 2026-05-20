SSH Brute Force Detection & Prevention on Cloud VPS

 Overview

This project demonstrates how to detect and prevent SSH brute-force attacks on a cloud-hosted Ubuntu server using Fail2Ban.

 Objective

To simulate real-world attack scenarios and implement automated defense mechanisms based on system log analysis.

---

 Architecture

Internet → Ubuntu VM (Azure) → SSH Logs → Fail2Ban → Firewall Block

---

 Technologies Used

 Ubuntu 24.04 (Azure VM)
 Fail2Ban
 SSH
 Linux system logs

---

 Implementation

1. Server Setup

 Deployed Ubuntu VM on Azure
 Connected via SSH

2. Install Fail2Ban

sudo apt update
sudo apt install fail2ban -y

3. Configure SSH Protection

Created "/etc/fail2ban/jail.local":

ssh
enabled = true
port = ssh
logpath = /var/log/auth.log
maxretry = 5
bantime = 600

4. Start Service

sudo systemctl start fail2ban
sudo fail2ban-client status

---

 Testing

 Simulated brute-force attempts using repeated SSH login failures
 Monitored logs:

sudo tail -f /var/log/auth.log

---

 Results

 Multiple failed login attempts detected
Fail2Ban automatically blocked attacker IP

Example:

Banned IP: 2.57.122.238

---

 Key Findings

 Public servers are continuously scanned by bots
 SSH is a primary attack vector
 Automated protection significantly reduces risk

---

 Future Improvements

 Integrate with SIEM (e.g., Sentinel)
 Add alerting system
 Visualize logs using ELK/Grafana
 Implement SSH key authentication

---

 Conclusion

This project demonstrates a practical approach to detecting and mitigating brute-force attacks in a real cloud environment using log-based security tools.
