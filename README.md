# NTFS vs Shared Permissions – Hands-On Lab (Read-Only Access Scenario)
### Scenario Overview
<img width="1611" height="743" alt="image" src="https://github.com/user-attachments/assets/2b4796a3-5b92-479a-b877-86ddf2085dfb" />

In this lab, I was tasked with granting a Marketing Intern access to the Marketing team’s shared folder. The intern needed to view files only and must not be able to modify, delete, or create any content. This activity demonstrates my understanding of NTFS permissions, Share permissions, and effective permission evaluation in Windows Server.

### Objective
I ensured the intern had read-only access to the Marketing shared folder while enforcing the principle of least privilege.

### Step-by-Step Implementation
  #### 1. Folder Creation 
  * I created a folder named "Marketing" on the file server.
  * This folder was designated as the shared location for the Marketing team.
  #### 2. Share Permissions Configuration
  * I right-clicked the Marketing folder and enabled folder sharing.
  * Under Share permissions, I assigned the Marketing group Read access.
  * This allowed network access while preventing file changes.
    <img width="1918" height="1040" alt="image" src="https://github.com/user-attachments/assets/42c81865-5fb0-4faf-8ede-da5de1467a42" />
  #### 3. NTFS Permissions Configuration
  * I opened the Security tab on the folder properties.
  * I added the intern user or intern security group.
  * I assigned Read & Execute permissions only.
  * I removed Modify and Write permissions to prevent edits and deletions.
    <img width="1920" height="1036" alt="image" src="https://github.com/user-attachments/assets/22636264-ea00-4f1a-9a9d-3bbe20d84c13" />
  #### 4. Permission Evaluation
  * I verified that both Share and NTFS permissions were correctly set.
  * Since Windows applies the most restrictive permission, the intern’s access was limited to read-only.
  #### 5. Testing and Validation
  * I logged in using the Marketing Intern account.
  * I successfully accessed and opened files in the Marketing folder.
  * I attempted to delete and modify files and confirmed the actions were blocked.

### Result
The Marketing Intern could view and open files only, with no ability to edit, delete, or add files. This confirmed that the permissions were correctly implemented.

### Key Takeaways
* Share permissions control network access.
* NTFS permissions control file-level security.
* The most restrictive permission always applies.
* Proper permission configuration prevents accidental or unauthorized data loss.

### Skills Demonstrated
* NTFS permission management
* Shared folder configuration
* Access control and security best practices
* Hands-on Windows Server administration
* Permission testing and validation


# NTFS vs Shared Permissions – Hands-On Lab (HR Secure Folder)
### Scenario Overview
<img width="1920" height="744" alt="image" src="https://github.com/user-attachments/assets/68202d56-1d92-4c85-bcac-2e214608b1c1" />

In this activity, I was required to create a highly secure folder for the HR department named HRGroup. Only HR staff should have access. All other employees must not see or access the folder at all. This lab demonstrates strict access control using NTFS permissions, proper group-based security, and real-world data protection practices.

### Objective
I configured the HRGroup folder so that only authorized HR users could access it, while completely blocking visibility and access for non-HR users.
### Step-by-Step Implementation
### 1. Security Group Preparation
  * I created an Active Directory security group named HRGroup.
  * I added only HR staff accounts to this group.
  * No other users or groups were included.

### 2. Folder Creation
  * I created a folder named HRGroup on the file server.
  * This folder was intended to store confidential HR data.

### 3. Share Permissions Configuration
  * I shared the HRGroup folder.
  * I removed default access such as Everyone.
  * I granted Full Control to the HRGroup security group.
  * No other users or groups were allowed at the Share level.
    <img width="1920" height="1037" alt="image" src="https://github.com/user-attachments/assets/5e286ee3-7fa6-4151-9263-03ec0a81d881" />

### 4. NTFS Permissions Configuration
  * I opened the Security tab on the folder properties.
  * I removed inherited permissions to prevent unintended access.
  * I explicitly granted Full Control to the HRGroup security group.
  * I ensured no other users or groups had permissions assigned.
    <img width="1920" height="1039" alt="image" src="https://github.com/user-attachments/assets/90d104e3-3374-4c41-a9d9-d052b1665d5a" />

### 5. Visibility Control
Because non-HR users had no NTFS or Share permissions, the folder was completely invisible to them when browsing network shares.

### 6. Testing and Validation
* I logged in as an HR user and confirmed full access to the folder.
* I logged in as a non-HR user and verified the folder was not visible or accessible.
* Access attempts from unauthorized users were denied as expected.

### Result
Only HR staff could see and access the HRGroup folder. Non-HR users could not view, open, or detect the folder at all. This confirms proper isolation of sensitive data.

### Key Takeaways
  * NTFS permissions are critical for protecting sensitive folders.
  * Removing inherited permissions prevents accidental access.
  * Group-based access control is scalable and secure.
  * A folder with no permissions is effectively invisible to unauthorized users.

### Skills Demonstrated
  * NTFS permission hardening
  * Secure shared folder configuration
  * Active Directory security group management
  * Least-privilege access enforcement
  * Real-world HR data protection
