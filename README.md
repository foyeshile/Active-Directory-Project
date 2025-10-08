# 🖥️ Active Directory Project: by Fuad Eniola Oyeshile


## 📘 Overview

This project demonstrates my ability to deploy and manage a Windows Server Active Directory environment, configure user accounts and group policies, and get an understansing of how Active Directory, Group Policy, and File Sharing within Domains operates. The goal was to simulate real-world IT Support and System Administration tasks focused on user management, security, and system efficiency.

---

## ⚙️ Objectives

- Build a functional **Active Directory domain** in a virtualized environment.
- Create and manage **users, groups, and organizational units (OUs)**.
- Configure and apply **Group Policy Objects (GPOs)** for security and compliance.
- Document the process to mirror **real-world IT administrative practices**.

---

## 🧰 Tools & Technologies

- **Windows Server ISO**

- **Windows 10/11 ISO (for clients)**

- **Virtualization software: VirtualBox, VMware, Hyper-V, or Azure VMs**

- **(Optional) Azure AD Connect**

---

## 🏗️ Setup Steps

### 1. Environment Configuration
When creating this Active Directory setup, I had to figure out a cost-effective way to utilize the Windows Server and Workstation file that I was getting ready to create. After looking through multiple resources, **VirtualBox** seemed to be the best alternative to be able to bring this project together. I then began the process of creating the Virtual Machine.

Keeping allocations and naming simple, I prepared the VM with _**Windows Server 2022 (64-bit)**_ and 50GB of allocation size, to make sure that the server had ample space to function correctly.

<img width="956" height="557" alt="image" src="https://github.com/user-attachments/assets/c377a2c2-8339-4a1d-9f3b-2b8c394ae474" />

After, I confirmed the Windows 2022 Server was configured correctly to the created VM through my storage settings.

<img width="953" height="556" alt="image" src="https://github.com/user-attachments/assets/09646a3f-d3fe-49d5-b07e-63cda6872d00" />

Finally, I was able to confirm that my VM was working and reading the .iso correctly.

<img width="1000" height="750" alt="image" src="https://github.com/user-attachments/assets/cbb9cc00-1cf0-4918-bd3f-58cd56e4e0a7" />

Specifically for setting up this homelab, I focused on using the _**Windows Server 2022 Standard Evaluation (Desktop Experience)**_ because this instance is being used as a homelab / testing enviroment. There is the option to use the _**Windows Server 2022 Datacenter Evaluation (Desktop Experience)**_ for more features and accessibility, but it was not needed for this project.

<img width="1021" height="760" alt="image" src="https://github.com/user-attachments/assets/6264a55c-9b20-491e-b303-749880ef0535" />

After installing the Microsoft Server Operating System, I continued to create an Administrator account, and proceeded to get to the login screen successfully. Once logged in, I could confirm that the Server Manager was present and available.

<img width="1014" height="771" alt="image" src="https://github.com/user-attachments/assets/ff51f92a-dc7c-49d7-a616-3d0f789a3371" />


After the Server Manager was confirmed, I began to get started with creating an Active Directory Domain Controller. By starting with renaming the instance PC, I would then save the changes to restart and continue to create the controller.

<img width="1015" height="765" alt="image" src="https://github.com/user-attachments/assets/4d58b0c2-f19a-4ed4-ac96-c37d93bc6176" />

Post-restart, I proceeded to add Roles and Features...

<img width="1015" height="760" alt="image" src="https://github.com/user-attachments/assets/8211659d-6fcb-478c-b85f-eb386f9f1b0f" />

...and selected _**Role-based or feature based installation**_ > Select the renamed Server VM (WindowsVM in this circumstance) > Select Active Directory Domain Services > Click "Next" on Features > Click "Next" on AD DS > Enable _**Restart the Destination Server Automatically If Required**_ > Proceed to install.

Once the install is finished, the server must be promoted to a domain controller:

<img width="1015" height="760" alt="image" src="https://github.com/user-attachments/assets/96f4085c-51de-4148-a376-b70124f204c0" />

After clicking, I selected _**Add A New Forest**_ and created a passowrd for the forest as well.

<img width="1015" height="768" alt="image" src="https://github.com/user-attachments/assets/47e715bb-5318-465a-962e-204cd62ee59e" />

After this, I continued to the Additional Options of the configuration, and verified that the NetBIOS name was automatically created (by default the name should be populated, but can be changed).

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/21cf4a19-ccc4-42e8-b4d0-b982854cdf96" />

Once finished, I proceeded to the **_Prerequisites Check_** to confirm that the checks were passed successfully. The check confirmed that everything was correct, and I proceeded with the installation.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/0c37f609-77be-4c22-889a-2319addf5403" />

The server had to be restarted, and once done, I could successfully login to the server again.

<img width="1018" height="764" alt="image" src="https://github.com/user-attachments/assets/44b48e04-17f5-4732-aa79-2c278b538814" />

### 2. User & Group Management

From here, the Active Directory Domain Controller has been successfully created; I then wanted to create users that could be managed through network computers. This step primarily confirms that users are able to log into the ADDC, and can be created through the _**Active Directory Users and Computers Tool**_ for creating groups, users, etc.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/98b0bc0d-84ee-4b82-9914-1e5443beb030" />

Through the tool, I was able to create a new user by right-clicking _**Users**_ > New > User.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/8a841219-1a8f-4d9e-b82a-e39adecdd296" />

As a test, I created an IT Support user login to test the newly created user, set up a password for the account, verified the information, and continued.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/8b70151c-1dc2-4d27-ae4c-f2c197f8a717" />

Once this was confirmed, I deleted the previous user, then created different _**Organizational Units**_ to specify users and what groups they belonged to. In this circumstance, I made an IT, Sales, and HR group. In those groups, I made users to replicate a distribution of users.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/e7efdf26-c04a-4ad8-a425-dc89606878f8" />

Each Group had a user that was dedicated to a task (IT, Sales, HR) and would proceed to be the test units for the rest of this project. Proceeding with this, I decided to make _**Security Groups**_ for these Organizational Units. This option is necessary in order to change Read/Write/Modify options, and can be configured to groups that may need / not need the access to certain permissions. IT Support will have _**Full Control**_, HR will have _**Modify(or Change)**_, and Sales will have _**Read Only**_ permissions.
To start, these Groups can be created by **Right-clicking the Organizational Unit > New > Group**.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/33b39c6c-6302-4903-acdc-e4c6b30a0daf" />

The Group Scope is set to **Global**, and the Group Type is set to **Security**. The scope and type can vary depending on the type of group that needs to be made. Once the group is made, the users can be added towards the group by selecting **Members > Add.**

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/539f3562-f790-4489-a25b-50529f15286e" />

The username of the account needed must be added to the "Object Names to Select" box; once entered, click **Check Names** to auto-populate the box with the user account, and click **OK**, then **Apply**.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/d52cccfb-e7fe-400e-bb81-ded676799a09" />

The Security Groups have been successfuly created. I then decided to create _**Group Permissions**_ for given reseources. This can be done in a couple different ways, but for this project, I decided to create it through the GUI. To begin, I navigated to the **C Drive Main Directory**, and created starting folders for each of the groups that were created. I made a main folder titled **Deparment Shares**, and within that folder, created three seperate folders: **HR, IT, and Sales**.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/650a0831-0f04-47b0-a254-4ba573ff8c53" />

Each folder needed to be configured to have permissions towards acess: I did so by **Right-clicking the folder > Properties > Sharing > Advanced Sharing.** I enabled **"Share this folder"** and named it correspondingly: **ITShare for IT, HRShare for HR, and SalesShare for Sales.**

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/5651038c-8f6e-400e-bf55-c42b0c2144cb" />

Once done, select **Permissions** and remove the **"Everyone"** group. This will be replaced for the corresponding group that needs access, and once replaced, will look as such: 

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/8e63f54f-fb56-43c3-9545-90f2d7a82744" />

In this circumstance, HR will have **Change and Read** controls. This will be repeated for the other two folders as well, and correspond to what permissions are needed with files in them. After that is done, I made sure to change the permissions within the **Security** tab.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/3462532b-3bcc-492b-8866-e94b04b2883e" />

**HR-Team** had to be added towards the Groups, and then given the same permissions for the files. After confirming, I did the same for the remaining two groups, **IT and Sales.** After confirming the permissions, I then proceeded to move onto **Group Policy and Implementation.**

### 3. Group Policy Implementation
For Group Policy, I know that the system needed some form of administration over computer settings (i.e. screen locking, password restrictions, etc.) to be used across the existing domain for the example corporation. Creating the group policy is similar to how one could use tools to create users and the like from the Domain Controller, but in a different tab. I was able to access it from the Server Manager by going to _**Tools > Group Policy Management**_.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/a72f8949-5570-4d23-86db-63300573ce7a" />

Once there, I navigated to the **Corporation.local** tab, fully expanded the tab and navigated to Group Policy Objects. Once there, I had to create a new policy, with three of them being focused on different aspects:

- Password Policy
- Screen Lock Policy
- Drive Mapping - Department Shares

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/95dd7488-25cf-4dfa-bfa4-71fbabc29b5a" />

Editing these policies are navigated by **Right-Clicking the created policy > Edit > Navigate toward the specific location that your policy is based in**: 

- Password Policy: _**Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy**_
- Screen Lock Policy: _**User Configuration → Policies → Administrative Templates → Control Panel → Personalization**_
- Drive Mapping: _**User Configuration → Preferences → Windows Settings → Drive Maps**_

For **Password Policy**, I went for specific secure standards, changing some of the policies to standard-known, and others to own preference:

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/27aedf66-144b-4c6f-a3a6-b206d632154d" />

- Minimum password length: 10
- Password must meet complexity requirements: Enabled
- Maximum password age: 60 days **(changes the Minimum Password Age default to 30 days)**
- Enforce password history: 5

For **Screen Lock Policy**, I changed the active timeout for a screensaver to **600 seconds**, and to **lock the screen with password** when the timeout occurs.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/0f0da9a2-c925-4132-a077-8126cd9458cf" />

It is important to note that _**the Group Policy Object has to be linked towards the Organizational Unit**_ in order to take effect. This can be done by dragging the policy directly to the Oganizational Unit that is requested. You will then be met with a confirmation- select **Yes** to confirm it.  

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/79475055-bcb9-4c2a-bf1b-5d138d764d1e" />

Finally, I wanted to create one more policy for **C Drive Mapping** for the shared folders. I navigated towards the location for the policy for Drive Mapping, and then proceeded to create a new mapping that would coordinate with the given Organizational Units: _**I: for IT, H: for HR, S: for Sales**_.

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/7f760383-3af2-4b06-930c-742dde07d600" />

There are a couple of things that I had to configure to make sure the drive was connected:
- **Location** would be set as the location of the shared folder for the drive that you want to re-organize, in this case, it was the **_ITShare_** folder.
- **Reconnect** had to be enabled
- The **Drive Letter** had to be assigned as I had planned out before
- I had to make sure that the users in the enabled group got the correct drive, by navigating to **Common > Enabling Item-level targeting > Selecting "Targeting..." > adding the Security Group for the specific drive (in this case, IT-Support).**

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/a54c7ee4-c59a-4d13-9287-c60ce534080f" />


This same scenario must be done for each of the drives, and when finished, will look like so:

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/a0f8f1b4-74fa-4178-9129-cb021e6393c3" />

Aftet this was all done, I confirmed that each one of the Organizational Units had the policies instilled on each other:

<img width="1018" height="765" alt="image" src="https://github.com/user-attachments/assets/0116cb44-e7fc-4205-87c0-6fef8bf6ca9c" />

So as seen, each one of the OU's contains:
- A **Screen Lock Policy** to confirm that the screen times out after a specified amount of time, and locks
- A **Drive Mapping Policy** to navigate drives towards specified groups.
- A **Password Policy** by default for all users, for security reasons.

And with that, the project comes to a close (for now).

---

## 📊 Results & Impact

Throughout the project, I developed a fully functional Active Directory domain (corporation.local) which mimicked a live enterprise environment. I established distinct Organizational Units for departments (IT, HR, Sales), configured security groups, as well as utilized role-based access control to manage permissions to utilize shared network resources. I created and secured department-specific shared folders and mapped drives while enforcing the same password and lockout policies using Group Policy Objects (GPOs). Overall, this experience enhanced my understanding of working within a corporate IT infrastructure by administering systems, provisioning accounts, and managing access.

## 💡 Key Learnings

From this project, I had the opportunity to engage with Active Directory (AD) on a practical level such as user provisioning, OU navigation, role-based permissions, and general management. I also learned how to leverage Group Policy Objects (GPOs) to create consistent configurations and security configurations across the domain. In regards to secure data access, I enhanced my understanding working with network file sharing and NTFS permissions. I used the GUI  interface to develop technical agility, but would also like to learn PowerShell scripting to benefit that as well. Overall, I improved documenting and communicating complex processes clearly and effectively through the system.

## 🧠 Future Enhancements

In the future, I aim to build on this project by onboarding Microsoft 365 leveraging Azure AD Connect to sync on-prem users and enable hybrid identity with single sign-on. I will also implement Microsoft Intune for endpoint management to enforce compliance, automate software delivery, and greatly enhance remote management. I will also introduce PowerShell scripts to automate user onboarding, permission assignment, and reporting, improving efficiency and scalability.

---
