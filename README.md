# Active Directory Domain Services Home Lab

A hands-on Windows Server home lab that simulates a small business environment using **Active Directory Domain Services (AD DS)**, **DNS**, **Group Policy**, and a **domain-joined Windows client**.

This project is designed to help build practical skills for **IT Support**, **Help Desk**, **Desktop Support**, **Junior System Administrator**, and **entry-level infrastructure** roles.

---

## Project Goal

Build a small business Active Directory environment in a virtual lab and perform common IT administration and help desk tasks such as:

- creating users and groups
- organizing users into OUs
- joining computers to the domain
- resetting passwords
- unlocking accounts
- applying Group Policy
- managing shared folder permissions
- troubleshooting login, DNS, and policy issues

---

## Why This Project Matters

This lab demonstrates practical experience with:

- Windows Server administration
- Active Directory user and computer management
- Group Policy configuration
- DNS dependency in AD
- domain authentication
- file sharing and NTFS permissions
- troubleshooting common enterprise support issues

Instead of just saying "I studied Active Directory," this project shows that you built and tested a working environment.

---

## Lab Environment

### Virtual Machines

#### 1. Domain Controller
- **Hostname:** `DC01`
- **Operating System:** Windows Server
- **Roles/Services:**
  - Active Directory Domain Services
  - DNS
  - optionally DHCP

#### 2. Client Machine
- **Hostname:** `HR-PC01` or `CLIENT01`
- **Operating System:** Windows 10 or Windows 11
- **Purpose:**
  - join to domain
  - test user logins
  - verify Group Policy
  - test shared folder access

### Suggested Domain Name
- `corp.local`

---

## Project Objectives

This lab is structured around four main objectives:

1. **Build the environment**
2. **Manage users and computers**
3. **Apply policies and permissions**
4. **Perform help desk and troubleshooting tasks**

---

## Phase 1 - Build the Domain Environment

### Objectives
- Install Windows Server in a VM
- Rename the server to `DC01`
- Set a static IP address
- Install AD DS
- Install and configure DNS
- Promote the server to a Domain Controller
- Create the domain `corp.local`

### Skills Demonstrated
- server setup
- Active Directory deployment
- domain creation
- static IP configuration
- DNS awareness

---

## Phase 2 - Create Active Directory Structure

Create a business-style OU structure instead of random users and objects.

### Objectives
- Create Organizational Units (OUs)
- Create user accounts
- Create security groups
- Organize users by department
- Separate admin accounts from standard users

### Example OU Structure

```text
corp.local
├── Corp Users
│   ├── HR
│   ├── Sales
│   └── IT
├── Corp Computers
├── Servers
└── Admin Accounts
```

### Example Users
- `jsmith` - HR
- `mjones` - Sales
- `itadmin` - IT Admin
- `helpdesk1` - Help Desk

### Example Groups
- `HR_Users`
- `Sales_Users`
- `IT_Admins`
- `Helpdesk_Reset`

### Skills Demonstrated
- identity management
- OU planning
- security group organization
- enterprise directory structure

---

## Phase 3 - Join a Client Computer to the Domain

### Objectives
- Install a Windows client VM
- Rename the machine appropriately
- Join the client to the domain
- Log in with domain user accounts
- verify successful authentication

### Tests to Perform
- local login vs domain login
- successful domain login
- failed login when account is disabled
- successful login after password reset or unlock

### Skills Demonstrated
- endpoint management
- domain join process
- user authentication testing

---

## Phase 4 - Simulate Help Desk Tasks

This is one of the strongest sections of the project because it mirrors real support work.

### Objectives
- Reset a user password
- Force password change at next logon
- Unlock a locked account
- Disable an account
- Re-enable an account
- Add a user to a security group
- Remove a user from a security group
- Move a user to another OU

### Example Support Scenarios
- employee forgot password
- employee account is locked out
- employee transferred departments
- terminated employee account needs to be disabled
- user needs access to a department share

### Skills Demonstrated
- account lifecycle management
- common help desk administration
- permissions and access support

---

## Phase 5 - Configure Group Policy

### Objectives
- Create and link GPOs to specific OUs
- Apply user and computer restrictions
- force policy updates
- confirm policies are being applied correctly

### Suggested Starter GPOs
1. **Password Policy**
   - minimum password length
   - password complexity

2. **Account Lockout Policy**
   - failed login threshold
   - lockout duration

3. **Desktop Restriction Policy**
   - disable Control Panel
   - restrict command prompt
   - set lock screen timeout

4. **Mapped Drive Policy**
   - map a shared department drive at login

### Useful Commands
```powershell
gpupdate /force
gpresult /r
```

### Skills Demonstrated
- Group Policy creation
- policy scoping through OUs
- endpoint restriction management
- policy verification and troubleshooting

---

## Phase 6 - Create Shared Folders and Permissions

### Objectives
- Create shared folders on the server
- assign share permissions
- assign NTFS permissions
- test access with different users and groups

### Example Shares
- `\\DC01\HRShare`
- `\\DC01\SalesShare`
- `\\DC01\Public`

### Test Cases
- HR user can access `HRShare`
- Sales user cannot access `HRShare`
- all users can access `Public`
- IT admin can access all shares

### Skills Demonstrated
- file sharing
- access control
- permission assignment
- validation of allowed and denied access

---

## Phase 7 - Troubleshooting

A lab becomes much more valuable when it includes problems you diagnosed and fixed.

### Objectives
- intentionally break something
- diagnose the issue
- fix the issue
- document the cause and solution

### Good Issues to Troubleshoot
- client cannot join the domain
- DNS misconfiguration
- GPO not applying
- access denied to shared folder
- user cannot log in
- account lockout issue
- wrong OU causing wrong policy application

### Skills Demonstrated
- problem-solving
- troubleshooting workflow
- support mindset
- documentation

---

## Lab Checklist

### Environment Setup
- [ ] Install Windows Server VM
- [ ] Rename server to `DC01`
- [ ] Set static IP address
- [ ] Install AD DS
- [ ] Install DNS
- [ ] Promote server to Domain Controller
- [ ] Create the domain `corp.local`

### Active Directory Structure
- [ ] Create OUs for HR, Sales, IT, Computers, and Admin
- [ ] Create 5-10 user accounts
- [ ] Create security groups
- [ ] Add users to the correct groups
- [ ] Move users into appropriate OUs

### Client Deployment
- [ ] Install Windows client VM
- [ ] Rename client machine
- [ ] Join client to the domain
- [ ] Log in with domain user accounts
- [ ] Verify authentication works

### Help Desk Tasks
- [ ] Reset a password
- [ ] Force password change at next logon
- [ ] Unlock a locked account
- [ ] Disable a user account
- [ ] Re-enable a user account
- [ ] Add user to a group
- [ ] Remove user from a group
- [ ] Move user to another OU

### Group Policy Tasks
- [ ] Create password policy
- [ ] Create account lockout policy
- [ ] Create desktop restriction policy
- [ ] Create mapped drive policy
- [ ] Link GPO to an OU
- [ ] Run `gpupdate /force`
- [ ] Confirm policy is applied

### Shared Folders and Permissions
- [ ] Create department shares
- [ ] Assign NTFS permissions
- [ ] Assign share permissions
- [ ] Test allowed access
- [ ] Test denied access

### Troubleshooting
- [ ] Fix failed domain join
- [ ] Fix DNS issue
- [ ] Fix GPO issue
- [ ] Fix shared folder access issue
- [ ] Fix locked-out login issue

---

## Recommended First Version Scope

To keep the project manageable, build **Version 1** with:

- 1 Domain Controller
- 1 Windows client
- 3 departments
- 5 users
- 3 security groups
- 3 GPOs
- 3 shared folders
- 4 help desk simulations

This is enough to make the project resume-worthy without making it too large.

---

## Example Project Deliverables

A strong GitHub repository for this lab could include:

- `README.md` with project overview and objectives
- screenshots folder
- network diagram or simple lab diagram
- step-by-step build notes
- troubleshooting notes
- list of tasks completed
- resume bullet examples

### Suggested Repository Structure

```text
active-directory-home-lab/
├── README.md
├── screenshots/
│   ├── dc-setup.png
│   ├── ou-structure.png
│   ├── group-policy.png
│   └── shared-folder-access.png
├── notes/
│   ├── build-steps.md
│   ├── troubleshooting.md
│   └── lessons-learned.md
└── diagrams/
    └── lab-diagram.png
```

---

## Resume Bullet Examples

- Built a virtualized Windows Server home lab with Active Directory Domain Services, DNS, and domain-joined Windows clients in a simulated business environment.
- Created and managed Organizational Units, user accounts, security groups, and access controls for multiple departments.
- Configured Group Policy Objects to enforce password rules, account lockout settings, desktop restrictions, and mapped network drives.
- Managed shared folders and validated NTFS/share permissions based on role-based access requirements.
- Performed common help desk tasks including password resets, account unlocks, disabled account management, and user access changes.
- Troubleshot domain join, DNS, authentication, and Group Policy issues during lab deployment and testing.

---

## What This Project Shows Employers

This lab helps demonstrate:

- hands-on Windows enterprise administration
- familiarity with AD DS and Group Policy
- common help desk workflows
- troubleshooting ability
- documentation and project ownership
- ability to simulate real IT support tasks

---

## Possible Future Improvements

After finishing Version 1, possible upgrades include:

- adding a second client machine
- adding DHCP
- creating more advanced GPOs
- adding a file server role
- documenting event logs and monitoring
- integrating a ticketing workflow simulation
- adding Microsoft 365 or Entra ID comparison notes

---

## Summary

This Active Directory home lab is a structured project designed to build practical IT support and systems administration experience.

It focuses on:

- domain setup
- user and group management
- Group Policy
- domain logins
- password resets and account recovery
- permissions management
- troubleshooting common enterprise issues

This project is especially valuable for anyone targeting:

- Help Desk
- IT Support
- Desktop Support
- Junior System Administrator
- NOC or infrastructure support roles

