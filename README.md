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


# NTFS vs Shared Permissions – Hands-On Lab (Vendor Upload Only Access)
### Scenario Overview
<img width="1920" height="766" alt="image" src="https://github.com/user-attachments/assets/30ebff53-b113-47e1-849a-a382e86df58e" />

In this activity, I was required to provide a third-party vendor with temporary access to a folder named VendorFiles. The vendor needed to upload files only. They must not view, open, modify, or delete any existing files. This scenario demonstrates secure external access using NTFS permissions, write-only configuration, and strict access isolation.

### Objective
I configured the VendorFiles folder to allow the vendor to drop files without visibility into folder contents, ensuring data confidentiality and preventing unauthorized access.

### Step-by-Step Implementation
### 1. Security Group Preparation
  * I created an Active Directory security group named Vendors.
  * I added only the vendor user account to this group.
  * No internal users were included.
### 2. Folder Creation
  * I created a folder named VendorFiles on the file server.
  * This folder was intended for temporary vendor uploads only.
### 3. Share Permissions Configuration
  * I shared the VendorFiles folder.
  * I removed default permissions such as Everyone.
  * I granted Change permission to the Vendors group.
  * This allowed file uploads while restricting administrative control.
    <img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/f2a9d2d4-8d3e-4cad-9083-1ccffcc840f7" />

### 4. NTFS Permissions Configuration
  * I opened the Security tab on the VendorFiles folder.
  * I disabled inheritance to prevent unintended access.
  * I assigned the Vendors group the following permissions:
      * Write
      * Create files / write data
  * I explicitly denied or excluded:
      * Read
      * List folder contents
      * Delete
  * This prevented the vendor from seeing or opening any files.
    <img width="1920" height="1041" alt="image" src="https://github.com/user-attachments/assets/0bd5aa77-1672-42a8-b027-462086b1d4fd" />

### 5. Folder Visibility Control
  * Because the vendor lacked Read and List permissions, the folder contents were hidden.
  * The vendor could upload files but could not browse or view existing data.
### 6. Testing and Validation
  * I logged in as the vendor user.
  * I successfully uploaded files to the VendorFiles folder.
  * I confirmed the vendor could not see, open, or delete any files.
  * Access attempts outside the allowed scope were denied.

### Result
The vendor was able to upload files successfully while remaining completely isolated from existing folder contents. This confirms a secure write-only drop folder configuration.

### Key Takeaways
  * NTFS permissions can be used to create write-only access.
  * Removing Read and List permissions hides folder contents.
  * Vendor access should always be isolated and temporary.
  * Proper configuration prevents data leakage from third parties.

### Skills Demonstrated
  * Advanced NTFS permission configuration
  * Secure vendor access management
  * Write-only drop folder implementation
  * Active Directory security group usage
  * Real-world external access control

# NTFS vs Shared Permissions – Hands-On Lab (Tiered IT Access Control)
### Scenario Overview
<img width="1919" height="744" alt="image" src="https://github.com/user-attachments/assets/d49d0edd-6601-477d-992b-9e3d0888da17" />

In this activity, I configured tiered access within the IT department. All IT technicians required access to the Software repository, but only senior IT staff were permitted to access the sensitive Licenses subfolder. This lab demonstrates NTFS inheritance control, subfolder permission isolation, and role-based access.

### Objective
I ensured:
 * All IT staff could access the Software repository.
 * Only senior IT staff could access the Licenses subfolder.
 * Junior IT staff were blocked from viewing or accessing Licenses.

### Step-by-Step Implementation
### 1. Security Group Preparation
  * I created two Active Directory security groups:
     * IT_Techs
     * IT_Senior
  * I added all IT staff to IT_Techs.
  * I added only senior IT staff to IT_Senior.

### 2. Folder Structure Creation
  * I created a parent folder named Software on the file server.
  * Inside Software, I created a subfolder named Licenses.

### 3. Share Permissions Configuration
  * I shared the Software folder.
  * I granted Read or Change access to IT_Techs at the Share level.
  * I avoided assigning permissions directly to individual users.
    <img width="1920" height="1040" alt="image" src="https://github.com/user-attachments/assets/c59c36db-6127-4c8a-b675-e1b91a618620" />

### 4. NTFS Permissions on Parent Folder (Software)
  * I configured NTFS permissions on the Software folder.
  * I granted Read & Execute access to IT_Techs.
  * This allowed all IT staff to browse and access general software files.
    <img width="1920" height="1036" alt="image" src="https://github.com/user-attachments/assets/b37021bb-dee2-4bc3-be80-b80be843a24d" />

### 5. NTFS Permissions on Subfolder (Licenses)
  * I opened the Security tab on the Licenses subfolder.
  * I disabled inheritance to prevent automatic permission carryover.
  * I removed IT_Techs permissions.
  * I granted Full Control to the IT_Senior group only.
    <img width="1920" height="1040" alt="image" src="https://github.com/user-attachments/assets/8c57a07c-b43f-487b-88c5-c95ea4bdfb9a" />

### 6. Testing and Validation
  * I logged in as a junior IT user and confirmed access to Software but denial to Licenses.
  * I logged in as a senior IT user and confirmed full access to both folders.
  * Access behavior matched the intended security design.
    <img width="1920" height="1036" alt="image" src="https://github.com/user-attachments/assets/64c2bd1d-4de4-4c17-853f-ec5f6015cd82" />

### Result
All IT staff could access the Software repository, while only senior IT staff could access the Licenses subfolder. Junior IT staff could not view or open the Licenses folder.

### Key Takeaways
 * NTFS inheritance must be controlled at the subfolder level.
 * Role-based access prevents overexposure of sensitive data.
 * Parent and child folders can enforce different security rules.
 * This setup mirrors real enterprise software license management.

### Skills Demonstrated
 * NTFS inheritance management
 * Subfolder permission isolation
 * Role-based access control
 * Active Directory security group design
 * Enterprise IT file security implementation

