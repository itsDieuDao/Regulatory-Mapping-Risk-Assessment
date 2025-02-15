<h1>Regulatory Mapping & Risk Assessment</h1>

 

**Objective**: Learn how to **map regulations to security controls** and implement compliance measures in a home lab.
 <br/>


<h2>🛠 Step 1: Choose a Regulation to Map</h2>
  <br/>  
  
🔹 Select a regulatory framework to work with :  
  - <b>**GDPR** (Data Protection & Privacy - good for EU focus)</b> 
   - <b>**HIPAA** (Healthcare data security & compliance)</b>
   - <b>**PCI-DSS** (Payment security regulations)</b>
   - <b>**SOX** (Sarbanes-Oxley Act for financial compliance)</b>

  
👉 For this project, we'll use **GDPR (General Data Protection Regulation)** since it applies broadly to data privacy. <br/>  
📄 Download the **GDPR Overview** [HERE](https://gdpr-info.eu/) <br/>  

  
<h2>🛠 Step 2: Identify Key GDPR Security Requirements </h2>  
   GDPR requires organizations to ensure the Confidentiality, Integrity, and Availibility **(CIA)** of personal data.  
   
<h3>🔹 Key Security Controls Required by GDPR </h3>  

  
| **GDPR** Article | Requirement | Implementation in Lab |
| ---------------- | ----------- | --------------------- |
| Art.5            | Data minimization & protection | Encrypt sensitive files & limit access | 
| Art. 25          | Data protection by design | Apply security best practices (firewall, secure coding) |  
| Art. 32          | Security of proccessing | Enable logging & monitoring (SIEM, IDS/IPS) |
| Art. 35          | Data Protection Impact Assessments | Perform risk assessments & documentation | 

 ✅**Goal:** Implement at least **three GDPR security controls** in your home lab.  

   

<h2>🛠 Step 3: Implement GDPR Security Controls</h2>
<h3>🔹Control 1: Encrypt Sensitive Data (Article 5 & 32) </h3>  
  
  🔧 **Linux File Encryption (AES-256)**  
  
    openssl enc -aes-256-cbc -salt -in sensitive_data.txt -out encrypted_data.enc -k YourStrongPassword
    
  🔧 **Decrypt Data**  

    openssl enc -aes-256-cbc -d -in encrypted_data.enc -out decrypted_data.txt -k YourStrongPassword


✅ This ensures personal data is protected in storage.  

<h2>🔹 Control 2: Access Control & User Restrictions (Article 32) </h2>  
  
  **Windows Server: Set Up Least Privilege Access**  
  1. Open **Group Policy Editor (gpedit.msc)** 
  2. Navigate to:  
      ` Computer Configuration > windows Settings > Security Settings > Local Policies > User Rights Asssignment `
  3. Configure "**Deny access to this computer from the network** for unauthorized users.
  4. **Limit Admin Privileges** by creating a standard user with restricted permissions.  
  
  
 **Linux: Use File Access Controls**  
  
  🔧 Set File Permissions  
  
        chmod 600 sensitive_data.txt
        chown root:root sensitive_data.txt
 
  - This will generate a **security report** based on NIST controls.
  
  2. **Set Up Basic Firewall Rules (UFW)**

         sudo ufw enable
         sudo ufw allow OpenSSH
         sudo ufw allow 443/tcp
         sudo ufw status verbose
  - This ensures only secure traffic is allowed.  

<h2>🛠 Step 5: Compliance Validation & Reporting  <br/>  
     
🔹 Generate a Compliance Report  </h2>  
  
 1. **Windows: Check compliance settings**  
  
        Get-GPOReport -All -ReportType HTML -Path C:\GPO_Report.html
    - This exports a **Group Policy** compliance report.
  
2. *Linux: Review Lynis Report**

       cat /var/log/lynis-report.dat
    - Look for **security misconfigurations**

3. **Analyze Security Logs with Splunk/Wazuh**
    - If you set up **Splunk**, create a **dashboard** to track compliance events.

<h2>🛠 Step 6: Write a Compliance Summary Report</h2>  

🎯 Your Deliverable: A **1-Page Compliance Report** summarizing:  

✅ Controls Implemented  
✅ Findings from Compliance Tools  
✅ Areas for Improvement  
✅ Next Steps  

<h3> 📄 Example Summary: </h3>  

**Security Compliance Report - NIST CSF Implementation in Home Lab**  
**Date:** \[Your Date]  
**Compliance Framework:** NIST Cybersecurity Framework (CSF) 

<h3> 🔹 Summary of Controls Implemented </h3>  

✅ Access Control (Windows & Linux GPOs) → PROTECT  
✅ Security Logging Enabled (Splunk/Wazuh) → DETECT  
✅ Firewall Rules (UFW, pfSense) → PROTECT  
✅ Audit Logs Reviewed → DETECT & RESPOND  

<h3> 🔹 Findings </h3>  

📌 **Windows Server Compliance Scan**: Passed 8/10 controls (Weak password policy detected)  
📌 **Linux Security Audit (Lynis)**: Hardening score 85/100 (Need SSH restriction improvement)  
📌 **Splunk Logs**: Detected 3 failed login attempts (Possible brute force)  
  
<h3> 🔹 Areas for Improvement </h3>  

  - Enforce **MFA** for **Windows Login**  
  - Implement **automatic remidiation scripts** for failed login detection

<h3> 🔹 Next Steps </h3>  

   1. Set up **Automated Compliance Monitoring** (e.g., Wazuh SIEM rules)
   2. Perform **Continuous Auditing** (Scheduled CIS Benchmark scans)

  


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
