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
  #### 3. NTFS Permissions Configuration
  * I opened the Security tab on the folder properties.
  * I added the intern user or intern security group.
  * I assigned Read & Execute permissions only.
  * I removed Modify and Write permissions to prevent edits and deletions.
  #### 4. Permission Evaluation
  * I verified that both Share and NTFS permissions were correctly set.
  * Since Windows applies the most restrictive permission, the intern’s access was limited to read-only.
    <img width="1920" height="1036" alt="image" src="https://github.com/user-attachments/assets/22636264-ea00-4f1a-9a9d-3bbe20d84c13" />
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
