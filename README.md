# OU-Structure-and-Access-Control

### Objective
Configured and managed a structured Active Directory environment by designing a departmental OU hierarchy, creating security groups, assigning permissions, and validating access control through mapped drives and share-level security. This project simulates real-world administrative practices for centralized user and resource management.

### Skills Learned
- Designed and implemented a scalable OU structure for department-based administration
- Created and managed security groups for role-based access control (RBAC)
- Applied custom NTFS and share-level permissions to secure resources
- Utilized group membership across OUs to support interdepartmental collaboration
- Performed drive mapping and permission testing on a Windows 11 domain-joined workstation
- Practiced user delegation, group policy planning, and inheritance configuration<br>
  <br>
### Tools Used
- Windows Server 2022 (Active Directory Domain Services, File and Storage Services)
- Active Directory Users and Computers (ADUC)
- Group Management Console
- Windows 11 VM (domain-joined)
- Proxmox VE (for virtualized lab environment)
- NTFS Permissions / Advanced Security Settings
- Server Manager > Shares<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">
  
### Step 1: Access Active Directory Users and Computers

Launched Active Directory Users and Computers from the Server Manager > Tools menu. Expanded the domain structure to reveal the default containers and Organizational Units (OUs), which are part of the Schema DNS. Understanding the default layout helps inform how best to organize and delegate administrative tasks.<br>
<br>
- Opened ADUC to examine domain structure
- Provides visibility into existing hierarchy before customization
- Accessed through Server Manager > Tools > Active Directory Users and Computers<br>

<img src="https://github.com/user-attachments/assets/6e4b6b20-126d-4ba1-bf48-847e84328885" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 2: Create Departmental OUs

Following best practices, created dedicated Organizational Units for each department. Right-clicked on the root domain DOOM.local and selected New > Organizational Unit. Created three new OUs: Engineering, Management, and IT.<br>
<br>
- Created new OUs for departmental structure
- Logical OU structure enables streamlined administration and group policies
- Right-clicked domain > New > Organizational Unit<br>

<img src="https://github.com/user-attachments/assets/96f47e8b-c167-46e8-80e6-39839410c9e1" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/d0e9cc22-c68d-4955-afb5-6f2723f6a90e" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/f16632f6-a6ea-49de-890d-bab2da735278" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 3: Move Users into Relevant OUs
Reorganized user accounts by moving them into their respective OUs:<br>
<br>
Happy and Peter moved to Engineering<br>
Bruce and Bucky moved to Management<br>
Administrator moved to IT

- Organized users by department
- Supports department-specific policy and permission management
- Dragged and dropped users into corresponding OU folders<br>

<img src="https://github.com/user-attachments/assets/b12d5cb1-3dc6-42af-8266-274acf2a86df" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/3d60dbf7-8249-40eb-a28e-12c54ecd9837" width="1000"><br>
<br>
<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 4: Create Sub-OU for Administration
Created a nested OU called Administration within the IT OU for better role separation. Moved the Administrator account into the Administration OU.<br>
<br>
- Added a sub-OU within IT for administrative accounts
- Isolates sensitive accounts for targeted security settings
- Right-clicked IT OU > New > Organizational Unit > Named "Administration"<br>

<img src="https://github.com/user-attachments/assets/b3485bd7-a288-41d2-a045-a63bc0eeea68" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/aed966d2-a8bf-477a-ba91-e505b6a201ff" width="1000"><br>
<br>
<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 5: Create Security Group in Engineering OU
Created a new Security Group named EngineeringShare within the Engineering OU. Chose group type as Security, which is used for assigning permissions. (Distribution groups are only for email distribution lists.)<br>
<br>
- Created a security group for resource access
- Allows centralized management of folder permissions
- Right-clicked Engineering OU > New > Group > Selected "Security"<br>
<br>
<img src="https://github.com/user-attachments/assets/765af03f-f2fa-41e9-a5b6-6d74433e4e9f" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 6: Add Members to Security Group
Opened EngineeringShare group properties. Under the Members tab, added Happy and Peter—users already in the Engineering OU.<br>
<br>
- Populated group with Engineering users
- Enables these users to inherit permissions from the group
- Double-clicked group > Members tab > Add users<br>
<br>
<img src="https://github.com/user-attachments/assets/79cd318d-3f51-4e67-b8f4-78e8ad3bb112" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 7: Cross-OU Group Access
Added Bruce from the Management OU to the EngineeringShare group to reflect cross-department access needs. Cross-OU membership is allowed in Active Directory and helps support collaborative workflows.<br>
<br>
- Added user from another OU to an Engineering group
- Enables access without changing OU structure
- Added Bruce through the same group membership window<br>
<br>
<img src="https://github.com/user-attachments/assets/693b67ed-ab27-47a2-adb6-0c8d863baa74" width="1000"><br>
<br>
<br>
<img src="https://github.com/user-attachments/assets/a308cfe3-8e68-499c-a217-454e8f2971e4" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 8: Initiate Shared Folder Setup

Opened File and Storage Services > Shares in Server Manager. Chose Tasks > New Share to begin shared folder configuration.<br>
<br>
- Began setting up a new file share
- Shared folders allow group-based access to central files
- Navigated to Shares > Tasks > New Share<br>
<br>
<img src="https://github.com/user-attachments/assets/0cc15bd2-1eaf-463f-be40-7e06ea455e4a" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/5223e40e-4c3d-47fe-a312-0aed96d9a45e" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 9: Configure Share Name and Path

In the New Share Wizard: Chose SMB Quick Profile<br>
- Named folder EngineeringShare<br>
- Set path to C:\Shares\EngineeringShare and network path to \\DC01\EngineeringShare<br>
- Accepted default caching setting<br>
<br>
- Set up folder path and name
- Configures the actual share for engineering use
- Followed SMB share creation steps in wizard<br>
<br>
<img src="https://github.com/user-attachments/assets/866350a8-3701-4e25-bd22-4d3395c6eac1" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/fc45fce9-042c-466c-87ed-c901e26eb838" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/486194c7-0e1d-42f8-88c1-cb59b453fa56" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 10: Customize Folder Permissions

In the permissions configuration window:

- Disabled inheritance
- Converted inherited permissions to explicit
- Removed default "Everyone" group to restrict access<br>
<br>
- Restricted access to shared folder
- Ensures only group members can access EngineeringShare
- Disabled inheritance > Converted permissions > Removed "Everyone"<br>
<br>
<img src="https://github.com/user-attachments/assets/5ba244b4-4869-4dba-b3a4-5e15bc31f031" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/59da9012-ef3e-4b1a-af93-204ecee198bc" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/467b32db-b234-4150-8b50-97ab53f9c2c5" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">



