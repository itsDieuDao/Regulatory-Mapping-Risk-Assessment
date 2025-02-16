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
 
  ✅ **This ensures only authorized users can access critical files.**  
    
  
<h2>🔹 Control 3: Enable Logging & Breach Detection (Article 33) </h2> <br/>  
       
 **Windows: Enable Security Logging**    

 🔧 **Powershell Command to Enable Logging**  
        
    auditpol /set /subcategory:"Logon" /success:enable /failure:enable

  - This logs **successful and failed login attempts** for monitoring.

  **Linux: Set Up Intrusion Detection System (IDS)**  

 🔧 **Install & Configure Fail2Ban for SSH Protection**  

     sudo apt install fail2ban -y
     sudo systemctl enable fail2ban  

  - **Fail2Ban** blocks multiple failed login attempts automatically. 



<h2>🛠 Step 4: Compliance Validation & Reporting </h2>  
  
<h3> 🔹 Generate a GDPR Compliance Report </h3>  

  1. Check encrypted files & permissions

         ls -l sensitive_data.enc

 2. Review security logs for failed login attempts  

        Get-EventLog -LogName Security -Newest 10

 3. Simulate a breach & review detection mechanisms


<h3> 📝 Sample GDPR Compliance Report: </h3>  

**Data Protection Compliance Report - GDPR Implementation in Home Lab**  
**Date:** \[2/14/2025]  
**Regulatory Framework:** GDPR

<h3> 🔹 Summary of Controls Implemented </h3>  

✅ Data Encryption (AES-256) → Article 5, 32    
✅ Least Privilege Access (Windows & Linux) → Article 32    
✅ Intrusion Detection & Logging (Fail2Ban, Event Logs) → Article 33    
  

  
<h3> 🔹 Findings </h3>  

📌 **Encrypted Data Check:** Verified AES-256 encryption applied  
📌 **Access Control Check:** Unauthorized users denied access
📌 **Log Review:** Detected 5 failed login attempts, Fail2Ban blocked the attacker  
  
<h3> 🔹 Areas for Improvement </h3>  

  - Implement **automated breach notifications**  
  - Apply **role-based access controls (RBAC) for ore granular security**

<h3> 🔹 Next Steps </h3>  

   1. Automate compliance reporting with **SIEM Dashboards (Splunk, Wazuh)**
   2. Perform **risk assessments (DPIA)** using **threat modeling tools**

  


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
