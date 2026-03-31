# 🛡️ Microsoft Sentinel SOC Lab – Security Operations Portfolio

## 🧑‍💻 About Me

Hi, my name is **Olatunji Olubi Abel**.

This portfolio showcases hands-on cybersecurity projects aligned with the **Microsoft SC-200 (Security Operations Analyst)** certification.

It documents my journey toward becoming a **SOC Analyst**, with a strong focus on practical, real-world security operations.

---

## 🎯 Skills Demonstrated

- 🔍 Security Monitoring  
- 🛠️ Detection Engineering  
- 🚨 Security Incident Investigation  
- 🧠 Threat Analysis  
- 📊 Log Analysis  
- ☁️ Microsoft Security Tools  

---

## 🛠️ Tools & Technologies

- **Microsoft Sentinel** (SIEM)  
- **KQL (Kusto Query Language)**  
- **Azure Active Directory (Entra ID)**  
- **Microsoft Defender**  
- **Log Analytics Workspace**  
- **Analytics Rules**  
- **Azure Arc** (Hybrid Environment)  
- **Windows Security Events**  

---

## 📂 Portfolio Projects

### 🔹 Project 0: SOC Environment Setup

Foundational project where I built a complete SOC lab environment from scratch.

**What I Did:**
- Configured Microsoft Entra ID (Azure AD) tenant  
- Created Log Analytics Workspace  
- Deployed Microsoft Sentinel (SIEM)  
- Connected Windows Server via Azure Arc  
- Set up data ingestion pipelines  

**Status:** ✅ Completed  

👉 [View Project Details](PROJECT-0-soc-enviroment-setup/README.md)

---

### 🔹 Project 1: Azure AD Brute Force Detection

Detection engineering project using cloud authentication logs.

**What I Did:**
- Analyzed Azure AD sign-in logs for failed authentication patterns  
- Wrote KQL queries to identify suspicious activity  
- Created analytics rule: alert on **10+ failures from same IP within 1 hour**  
- Tested detection using simulated attacks  

**Key Findings:**
- Multiple failed login attempts within a short time window  
- Identified source IP and targeted user account  
- Confirmed brute force attack pattern  

**Status:** ✅ Completed  

👉 [View Project Details](PROJECT-1-detection-engineering/README.md)

---

### 🔹 Project 2: False Positive -Brute Force Detection

Focused on distinguishing real threats from false positives.

**What I Did:**
- Generated failed login events on a Windows workstation  
- Alert triggered for 8+ failed attempts  
- Investigated to validate the alert  

**Investigation Findings:**
- Source: `127.0.0.1` (localhost, not external attacker)  
- Activity: Workstation unlock attempts (**LogonType 7**)  
- Conclusion: User error (incorrect password), not malicious activity  

**Lesson Learned:**
- Not all alerts are real threats  
- Context and investigation are critical in SOC workflows  
- Understanding log data reduces alert fatigue  

**Status:** ✅ Completed  

👉 [View Project Details](PROJECT-2-brute-force-detection/README.md)

---

### 🔹 Project 3: RDP Brute Force Detection & Investigation

Simulated a real-world attack involving multiple failed RDP logins followed by a successful compromise.

**What I Did:**
- Simulated 10+ failed RDP login attempts  
- Successfully logged in after failed attempts  
- Generated Windows Security Events (`4625`, `4624`)  
- Built analytics rule to detect attack pattern  
- Investigated incident using Microsoft Sentinel  

**Key Findings:**
- Failed attempts: **LogonType 3** (network authentication)  
- Successful login: **LogonType 10** (RDP session)  
- Same IP and user account across events  
- Attack occurred within a short time window  

**Outcome:**
- Detection rule successfully triggered  
- Incident created and analyzed in Sentinel  
- Full attack chain visibility achieved  

**Status:** ✅ Completed  

👉 [View Project Details](PROJECT-3-RDP-brute-force-detection/README.md)

---

## 🚀 Key Achievements

- Built a functional SOC lab environment from scratch  
- Simulated and detected real-world attack scenarios  
- Developed detection rules using KQL  
- Performed incident investigation and validation  
- Reduced false positives through proper analysis  
- Worked with multiple log sources (Azure AD & Windows Events)  

---

## 📊 Attack Patterns Detected

| Attack Type               | Project   | Status       |
|--------------------------|----------|-------------|
| Cloud Login Brute Force  | Project 1 | ✅ Complete |
| Local Login Failures     | Project 2 | ✅ Complete |
| RDP Brute Force + Success| Project 3 | ✅ Complete |

---

## 🚀 Coming Next

Planned projects to expand detection coverage:

- **Project 4:** Lateral Movement Detection  
- **Project 5:** Data Exfiltration Detection  
- **Project 6:** Privilege Escalation Detection  

---

## 🎓 SC-200 Alignment

This portfolio demonstrates hands-on experience with:

- Microsoft Sentinel configuration and deployment  
- Log ingestion and data connectors  
- Analytics rule creation  
- Incident investigation workflows  
- KQL query development  
- Windows Security Event analysis  
- Azure AD authentication monitoring  

---

## 📈 Career Goal

To become a **SOC Analyst / Security Operations Engineer**, specializing in:

- Threat detection and analysis  
- Incident response and investigation  
- SIEM operations (Microsoft Sentinel)  
- Log analysis and correlation  
- Attack pattern identification  

---

## 📌 How To Use This Portfolio

**For learners:**
- Start with **Project 0** (environment setup)  
- Move to **Project 1** (detection logic)  
- Study **Project 2** (false positives)  
- Review **Project 3** (full attack investigation)  

**For recruiters:**
- Project 3 demonstrates full SOC workflow  
- Project 2 highlights analytical thinking  
- All projects show practical, hands-on experience  

---

## 📞 Contact

- **Certification:** SC-900 (Azure Fundamentals)  
- **Location:** Nigeria  
- **GitHub:** https://github.com/olatunjiabel231-coder  

---

## ⚠️ Disclaimer

This portfolio is created in a controlled lab environment for learning purposes.  
No real-world systems or organizations were affected.

---

**Last Updated:** March 2026  
**Status:** 🟢 Active (ongoing improvements)

