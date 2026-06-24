# Task 2 – Network Security & Scanning

## Objective

The objective of this task was to perform network reconnaissance, port scanning, vulnerability assessment, and firewall configuration using industry-standard cybersecurity tools.

---

# Environment

| Component             | Details         |
| --------------------- | --------------- |
| Attacker Machine      | Kali Linux      |
| Target Machine        | Metasploitable2 |
| Target IP             | 192.168.56.103  |
| Scanner               | Nmap            |
| Vulnerability Scanner | OpenVAS         |
| Firewall              | iptables        |

---

# 1. Port & Service Scanning

## Nmap Scan

Command Used:

```bash
nmap -sV -O 192.168.56.103
```

### Purpose

* Discover open ports
* Detect running services
* Identify operating system

### Findings

Multiple services were detected including:

* FTP (21)
* SSH (22)
* Telnet (23)
* SMTP (25)
* HTTP (80)
* MySQL (3306)
* PostgreSQL (5432)

The target was identified as Metasploitable2, an intentionally vulnerable Linux machine.

---

# 2. Vulnerability Assessment

## OpenVAS Scan

Scan Profile:

* Full and Fast

Target:

* 192.168.56.103

### Scan Summary

| Item         | Count |
| ------------ | ----- |
| Hosts        | 1     |
| Ports        | 19    |
| Applications | 19    |
| CVEs         | 34    |
| Results      | 68    |

### Severity Distribution

| Severity | Count |
| -------- | ----- |
| Critical | 12    |
| High     | 8     |
| Medium   | 32    |
| Low      | 5     |

---

# Critical Vulnerabilities

## Possible Backdoor: Ingreslock

CVSS: 10.0

A potential backdoor service was detected which may allow unauthorized access.

---

## rlogin Passwordless Login

CVSS: 10.0

The service permits login without secure authentication.

---

## rexec Service Running

CVSS: 10.0

Allows remote command execution and insecure credential transmission.

---

## Distributed Ruby Multiple RCE Vulnerabilities

CVSS: 10.0

Remote attackers may execute arbitrary code.

---

## Apache Tomcat Ghostcat Vulnerability

CVSS: 9.8

May allow file disclosure and remote code execution.

---

## MySQL Default Credentials

CVSS: 9.8

Default database credentials were identified.

---

## vsFTPd Backdoor Vulnerability

CVSS: 9.8

A known backdoored version of vsFTPd was detected.

---

# 3. Firewall Configuration

## iptables Rules Applied

Allow SSH:

```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

Block Telnet:

```bash
sudo iptables -A INPUT -p tcp --dport 23 -j DROP
```

Block HTTP:

```bash
sudo iptables -A INPUT -p tcp --dport 80 -j DROP
```

Verification:

```bash
sudo iptables -L -n -v
```

---

# Firewall Testing

From Metasploitable2:

```bash
nmap -p 22,23,80 192.168.56.102
```

Result:

```text
22/tcp open ssh
23/tcp filtered telnet
80/tcp filtered http
```

This confirms that the firewall successfully blocked access to ports 23 and 80 while allowing SSH access on port 22.

---

# Screenshots

Include the following screenshots in the repository:

* Nmap Scan Results
* OpenVAS Feed Status
* OpenVAS Scan Configuration
* OpenVAS Completed Scan
* Vulnerability Statistics
* Critical Vulnerabilities
* iptables Rules
* Firewall Test Results

---

# Conclusion

Nmap and OpenVAS successfully identified vulnerable services and security weaknesses on the Metasploitable2 target. Firewall controls were implemented using iptables to restrict access to selected ports. The exercise demonstrated practical skills in network scanning, vulnerability assessment, and firewall configuration.
