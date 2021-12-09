Week 4 Homework Submission File: Linux Systems Administration
Step 1: Ensure/Double Check Permissions on Sensitive Files
Permissions on /etc/shadow should allow only root read and write access.

Command to inspect permissions: ls -l /etc/shadow shows the permissions are set to 640.

Command to set permissions (if needed): sudo chmod 600 /etc/shadow

Permissions on /etc/gshadow should allow only root read and write access.

Command to inspect permissions: ls -l /etc/gshadow shows the permissions are set to 640.

Command to set permissions (if needed): sudo chmod 600 /etc/gshadow

Permissions on /etc/group should allow root read and write access, and allow everyone else read access only.

Command to inspect permissions: ls -l /ect/group shows that the permissions are already set to 644.

Command to set permissions (if needed): sudo chmod 644 /etc/group

Permissions on /etc/passwd should allow root read and write access, and allow everyone else read access only.

Command to inspect permissions: ls -l /etc/passwd shows that the permissions are already set to 644.

Command to set permissions (if needed): sudo chmod 644 /etc/group

Step 2: Create User Accounts
Add user accounts for sam, joe, amy, sara, and admin.

Command to add each user account (include all five users):
sudo useradd sam
sudo useradd joe
sudo useradd amy
sudo useradd sara
sudo useradd admin
sudo grep '!' /etc/shadow
![image](https://user-images.githubusercontent.com/93474690/145323258-6b9aae30-768a-4c41-9c38-48eb3483e973.png)
