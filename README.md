## 🧱 **Project: Implementation and Testing of Active Directory, IAM, and Zero Trust Network Architecture**

A virtual enterprise network integrating Active Directory, Keycloak IAM, and Zero Trust Architecture. Designed and implemented in VirtualBox using Windows Server, Ubuntu, and Kali Linux to demonstrate secure authentication and access control.

**Contributor:** *Shadia Rahman Dipty (59958)*  
**Tools & Platforms:** Oracle VirtualBox · Windows Server 2022 · Kali Linux · Ubuntu · Windows 10 · Keycloak · NGINX  

---

### 🧭 **Project Overview**

The objective of this project was to design, configure, and test a secure virtual enterprise environment that integrates **Active Directory (AD)** with **Identity and Access Management (IAM)** and applies **Zero Trust Network Architecture (ZTNA)** principles.  

The project simulated a corporate network using four virtual machines within an isolated internal network to ensure secure communication.

| Virtual Machine | Role | Key Function |
|-----------------|------|---------------|
| **Windows Server 2022** | Directory & DNS Server | Centralized domain management and user authentication |
| **Kali Linux** | IAM Server (Keycloak) | Identity federation and role-based access control |
| **Ubuntu** | Zero Trust Server (NGINX) | Enforced identity-based resource access |
| **Windows 10** | Client Machine | Tested authentication and policy enforcement |

---

### 🏗️ **1. Network Configuration and Topology**

All virtual machines were deployed in **Oracle VirtualBox** using an **Internal Network (SecureNet)** on the `192.168.56.0/24` subnet.  
- The internal network ensured isolation from the internet for secure testing.  
- Each VM was assigned a **static IP address** to maintain consistent DNS mapping.  

**IP Plan Example:**  
| Host | IP Address | Description |
|------|-------------|-------------|
| Directory/DNS Server | 192.168.56.101 | Windows Server 2022 |
| IAM Server | 192.168.56.102 | Kali Linux running Keycloak |
| ZTNA Server | 192.168.56.103 | Ubuntu running NGINX |
| Client | 192.168.56.104 | Windows 10 workstation |

**Network Topology Diagram:**  
![Network Topology] (<img width="792" height="604" alt="image" src="https://github.com/user-attachments/assets/a94ef2fe-f541-47bc-8d2c-bbe030e10504" />
)

---

### ⚙️ **2. Active Directory Configuration (Windows Server 2022)**

**Steps Completed:**
1. Installed **Active Directory Domain Services (AD DS)** and **DNS Server** roles via *Server Manager*.  
2. Configured a new forest with the domain name `syd2.local`.  
3. Verified installation using `nslookup syd2.local` for DNS resolution.  
4. Created **security groups** (e.g., *ZTNA Users*) and **user accounts** for domain authentication.  
5. Configured DNS A Records for all VMs.  
6. Successfully validated communication using `ping` and `nslookup`.

**Outcome:**  
✅ A fully functional **Active Directory domain** providing centralized authentication and DNS name resolution.

---

### 🔐 **3. Identity and Access Management (Kali Linux – Keycloak Server)**

**Implementation Steps:**
1. Configured **Kali Linux** with static IP `192.168.56.102`.  
2. Installed **OpenJDK** and deployed **Keycloak** from the official distribution.  
3. Accessed the **Keycloak Admin Console** at `http://localhost:8080/`.  
4. Created an **Admin account**, configured realms, users, and roles.  
5. Integrated **Keycloak** with **Active Directory** through *User Federation*.  
6. Enabled synchronization to import AD users automatically.  
7. Configured **role mappings** (Admin, User, Manager) for role-based access.

**Outcome:**  
✅ Keycloak successfully integrated with Active Directory for centralized IAM and SSO authentication.

---

### 🛡️ **4. Zero Trust Server (Ubuntu – NGINX)**

**Implementation Steps:**
1. Installed and verified **NGINX** service (`systemctl status nginx`).  
2. Created `/secure` and `/denied` directories for access simulation.  
3. Modified `/etc/nginx/sites-available/default` to enable OIDC authentication via Keycloak.  
4. Protected `/secure` endpoint with Keycloak login and `/admin` with admin-only access.  
5. Reloaded NGINX configuration and verified access control.

**Verification Results:**
- `/secure` redirected users to **Keycloak login** before access.  
- Valid logins displayed secure page content.  
- Unauthorized users received **403 Forbidden** on `/admin`.

**Outcome:**  
✅ NGINX successfully enforced Zero Trust principles with continuous identity verification.

---

### 💻 **5. Client Machine (Windows 10)**

- Configured to **Internal Network (SecureNet)** with static IP `192.168.56.104`.  
- DNS pointed to `192.168.56.101` (Domain Controller).  
- Joined the domain `syd2.local` for centralized authentication.  
- Verified successful login and secure access via Keycloak.

**Outcome:**  
✅ Client successfully authenticated through Keycloak and AD integration.

---

### 🧩 **6. Testing & Verification**

| Test | Purpose | Result |
|------|----------|--------|
| Ping between all hosts | Verify internal connectivity | ✅ Successful |
| `nslookup` for `syd2.local` | Confirm DNS resolution | ✅ Working |
| Keycloak login via `/secure` | Test IAM authentication | ✅ Successful |
| Access `/admin` as unauthorized user | Verify access denial | ✅ 403 Forbidden |

---

### 📊 **7. Results Summary**

- Active Directory enabled **centralized user and DNS management**.  
- Keycloak handled **identity federation and authentication**.  
- NGINX enforced **Zero Trust access policies** through OIDC.  
- Full system verification confirmed secure authentication and access control.

---

### 🏁 **8. Conclusion**

The successful integration of **Active Directory**, **Keycloak IAM**, and **Zero Trust Architecture** demonstrates a practical enterprise-grade security setup.  

This project showcased:
- Centralized authentication using **Active Directory + Keycloak**  
- Policy-based access control with **NGINX**  
- The Zero Trust principle: *“Never trust, always verify”*  

✅ **Final Outcome:**  
A secure, unified virtual network where all users and devices were authenticated, authorized, and continuously validated.

---

### 🖼️ **Screenshots**

1. **Active Directory Configuration**  
[AD & DNS Configuration]

<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/c449ed72-e1ea-4f27-8bba-eec1ba9fd398" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/0198043e-c0c5-4cf5-9796-a09c8e4be911" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/3b35fe2a-6a12-4698-81c1-4d580352e06d" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/a1498510-2da5-4cd9-9a85-217ac62be3cb" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/dc671772-e60b-4eca-8858-21867d4abf58" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/13298695-3fbf-47d0-9c8a-b6ae783a6826" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/6250d652-4226-4248-9118-53450cb5c41e" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/4147e720-dc28-4c3c-bb36-463b606e4012" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/143df083-54ef-434c-b53c-7e9cfdb32057" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/3a44e720-acd4-426e-a051-85b82c089ab3" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/28a30d26-164c-4904-8172-5b199f97ea67" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/5479323f-2977-4583-811c-8f63b9a01512" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/15c5fa4d-38fb-4913-8bcb-a5c91c005eda" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/cac7c8ac-bead-45a8-b479-68da2cc6a739" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/9797ba94-8b5b-4210-8e3d-24c5e68d871f" />
<img width="940" height="524" alt="image" src="https://github.com/user-attachments/assets/4204befe-0948-40a9-936d-a89eb394ceab" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/09ce2bcc-e558-455e-8359-556d579bfd6d" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/8641a77e-f456-44b1-b9d9-6e933a37558f" />
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/fb3d18fc-2abb-4afc-a69a-66198455054b" />




2. **Keycloak IAM Integration**  
   ![Keycloak Integration]
   <img width="940" height="1019" alt="image" src="https://github.com/user- attachments/assets/afbf0b2a-68bc-4a30-b8dc-c944eeacdebb" />
   <img width="940" height="1019" alt="image" src="https://github.com/user-attachments/assets/ca4c4a78-0671-442c-9bbd-0a1a7c418dcf" />
   <img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/677249de-eb74-4b39-a4f4-888301e75bc0" />
<img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/f2cb0996-a362-4571-93d5-b419a9fdb67d" />
<img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/7fdd4b0a-475c-4745-877c-91ff8ea3241d" />
<img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/d47cadf6-ee52-42ed-8201-691c3137fe60" />
<img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/98463532-9388-450c-8c8f-1c8a9adca0e8" />
<img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/cdbc55ea-d9be-42b1-beb2-f5aaf59582eb" />
<img width="940" height="997" alt="image" src="https://github.com/user-attachments/assets/ac43d731-8e81-4a4c-8673-facb6aa112ec" />
   
___

4. **Zero Trust Server Setup**  
   ![ZTNA Setup](https://github.com/shdipty/Nitzutz-app/blob/main/nginx_ztna_setup.png)

5. **Client Authentication Test**  
   ![Client Access](https://github.com/shdipty/Nitzutz-app/blob/main/client_authentication.png)

---

### 💬 **Personal Reflection**

This project deepened my understanding of **enterprise-level network security** and strengthened my hands-on experience in **Active Directory, Keycloak IAM, and Zero Trust principles**.  
It enhanced my practical skills in network design, authentication systems, and secure infrastructure deployment — key areas for a professional career in **cybersecurity and IT infrastructure**.
