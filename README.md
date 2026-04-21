# 🛡️ SOC Home Lab: Detecting and Blocking SSH Brute Force Attacks using Wazuh

![Platform](https://img.shields.io/badge/Platform-Ubuntu-blue)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh-purple)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

## 📌 Overview

This project demonstrates a hands-on Security Operations Center (SOC) lab using Wazuh to detect and respond to SSH brute force attacks.

The lab simulates repeated failed SSH login attempts from an attacker system and uses Wazuh to:

- Detect brute force activity  
- Generate security alerts  
- Monitor authentication failures  
- Trigger active response  
- Automatically block attacker IP addresses  

This simulates a real-world detection and response workflow used by blue teams.

---

## 🎯 Objectives

- Simulate SSH brute force activity
- Detect repeated authentication failures
- Generate alerts in Wazuh
- Implement automated response to block attackers

---

## 🏗️ Lab Architecture

```text
Kali Attacker
     |
SSH Brute Force Attempts
     |
Ubuntu Target (Wazuh Agent)
     |
Auth Logs Generated
     |
Wazuh Detection
     |
Active Response
     |
Attacker IP Blocked
```

---

## 🛠️ Technologies Used

- Wazuh SIEM
- Ubuntu Linux
- OpenSSH
- Active Response
- Linux Authentication Logs
- iptables

---

## ⚙️ SSH Log Monitoring

Configured Wazuh Agent to monitor:

```xml
<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/auth.log</location>
</localfile>
```

Restarted agent:

```bash
sudo systemctl restart wazuh-agent
```

---

## ⚔️ Attack Simulation

Repeated failed SSH attempts:

```bash
ssh fakeuser@192.168.28.133
```

Generated authentication failures:

```text
Failed password for invalid user
```

---

## 🚨 Detection Results

Wazuh generated alerts for:

- Multiple failed SSH logins
- Brute force behavior
- Suspicious authentication activity

---

## 🔥 Active Response Configuration

Configured automatic blocking:

```xml
<active-response>
  <command>firewall-drop</command>
  <location>local</location>
  <rules_id>5710</rules_id>
  <timeout>600</timeout>
</active-response>
```

---

## 🧱 Response Validation

Verified attacker IP block using:

```bash
sudo iptables -L
```

---

## 📊 Security Use Cases

This lab helps detect:

- Password spraying
- SSH brute force attacks
- Unauthorized access attempts
- Automated attack activity

---

## 🧪 MITRE ATT&CK Mapping

| Technique | ID |
|----------|----|
| Brute Force | T1110 |
| Valid Accounts | T1078 |

---

## 📸 Screenshots

Add your screenshots:

```text
screenshots/
├── failed-auth-log.png
├── wazuh-bruteforce-alert.png
└── attacker-ip-blocked.png
```

Example:

```md
![Failed Auth Log](screenshots/failed-auth-log.png)

![Wazuh Alert](screenshots/wazuh-bruteforce-alert.png)

![IP Blocked](screenshots/attacker-ip-blocked.png)
```

---

## 📂 Repository Structure

```text
soc-ssh-bruteforce-detection-response-lab/
├── README.md
├── screenshots/
```

---

## 🧠 Skills Demonstrated

- Threat Detection
- Security Monitoring
- Incident Response
- Active Response Automation
- SSH Attack Detection
- Linux Security Operations

---

## 🚀 Future Improvements

- Add Hydra brute force testing
- Add geo-IP enrichment
- Add automated alerting
- Add threat intelligence integration

---

## 👨‍💻 Author

Nitesh Vishwakarma

---

## ⭐ Project Outcome

Successfully built a detection and response lab using Wazuh to identify and automatically block SSH brute force attacks in a SOC-style workflow.
