# nmap-security-assessment
Security assessment using Nmap for vulnerability detection and compliance.
# Security Assessment with Nmap

## 📌 Project Overview
Conducted a security assessment using **Nmap** to identify vulnerabilities in **FTP, SSH, Telnet, and SMB services** across target systems. The assessment aimed to enhance security by ensuring compliance with **ISO 27001** standards and conducting regular risk assessments. Mitigation recommendations were provided to strengthen system security.

## 🚀 Objectives
- Scan for open and vulnerable ports on networked systems.
- Identify security risks in FTP, SSH, Telnet, and SMB services.
- Ensure compliance with **ISO 27001** security standards.
- Provide actionable mitigation recommendations to enhance security posture.

---

## 🛠️ Setup & Configuration

### 1️⃣ Install Nmap
Ensure Nmap is installed on your system:
```sh
sudo apt install nmap  # Ubuntu/Debian
sudo yum install nmap  # CentOS/RHEL
brew install nmap      # macOS
```
Verify installation:
```sh
nmap --version
```

### 2️⃣ Define Target Scope
Identify target systems for scanning:
```sh
export TARGETS="192.168.1.1 192.168.1.2 192.168.1.3"
```
Or scan an entire subnet:
```sh
export TARGETS="192.168.1.0/24"
```

---

## 🔍 Security Assessment with Nmap

### 🔹 1. Scan for Open Ports
```sh
nmap -p 21,22,23,445 -sV -T4 $TARGETS
```
- **`-p 21,22,23,445`** → Scan FTP (21), SSH (22), Telnet (23), SMB (445)
- **`-sV`** → Service version detection
- **`-T4`** → Aggressive timing for faster scanning

### 🔹 2. Detect Vulnerabilities
Use **Nmap Scripts (NSE)** for vulnerability scanning:
```sh
nmap --script vuln -p 21,22,23,445 $TARGETS
```
✅ Identifies known vulnerabilities in services.

Example: Scan for **SMB vulnerabilities**:
```sh
nmap --script smb-vuln* -p 445 $TARGETS
```

### 🔹 3. Comprehensive Security Scan
```sh
nmap -A -T4 $TARGETS
```
- **`-A`** → Enables OS detection, version detection, script scanning, and traceroute.
- **`-T4`** → Faster execution.

---

## 📊 Risk Assessment & Compliance
Ensured compliance with **ISO 27001** security controls:
- **A.12.6.1**: Security Vulnerabilities Management.
- **A.13.1.1**: Network Security Controls.
- **A.18.2.3**: Technical Compliance Review.

### 🔹 Key Findings
| Service | Risk Level | Vulnerabilities Detected |
|---------|-----------|-------------------------|
| FTP (21) | 🔴 High | Anonymous login enabled, outdated version |
| SSH (22) | 🟠 Medium | Weak ciphers detected |
| Telnet (23) | 🔴 High | Clear-text authentication |
| SMB (445) | 🟠 Medium | SMBv1 enabled (vulnerable to EternalBlue) |

### 🔹 Mitigation Recommendations
✅ **Disable FTP anonymous access** and enforce TLS encryption.
✅ **Upgrade SSH** and configure stronger encryption algorithms.
✅ **Disable Telnet** and replace with SSH for secure remote access.
✅ **Disable SMBv1** and enforce SMBv2 or SMBv3.

---

## 🔧 Future Enhancements
✅ Automate scans using a **cron job** for continuous monitoring.
✅ Integrate with **Splunk** for real-time threat detection.
✅ Deploy **OSSEC** for host-based intrusion detection.

---

## 📌 Technologies Used
- **Nmap (Network Mapper)**
- **NSE (Nmap Scripting Engine)**
- **Linux & Windows Security Tools**
- **ISO 27001 Compliance Framework**

---

## 📢 Contribution & Feedback
Feel free to **fork** this repository, contribute by submitting **pull requests**, or suggest improvements via **issues**! 🚀

---

### 🔗 References
- [Nmap Documentation](https://nmap.org/book/man.html)
- [ISO 27001 Security Controls](https://www.iso.org/isoiec-27001-information-security.html)
- [SMB Vulnerability Scanner](https://nmap.org/nsedoc/scripts/smb-vuln-ms17-010.html)
