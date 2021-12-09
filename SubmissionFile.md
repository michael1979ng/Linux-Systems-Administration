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

Ensure that only the admin has general sudo access.

Command to add admin to the sudo group: sudo usermod -a -G sudo admin
To check if access is granted: sudo grep sudo /etc/group or sudo groups admin

![image](https://user-images.githubusercontent.com/93474690/145323471-846672b1-9158-4393-861e-4af3ece8d4c9.png)

Step 3: Create User Group and Collaborative Folder
Add an engineers group to the system.

Command to add group: sudo groupadd engineers
Add users sam, joe, amy, and sara to the managed group.

Command to add users to engineers group (include all four users):
sudo usermod -a -G engineers sam
sudo usermod -a -G engineers joe
sudo usermod -a -G engineers amy
sudo usermod -a -G engineers sara

![image](https://user-images.githubusercontent.com/93474690/145323623-6e236408-305e-474b-9912-8594d72e7b3f.png)

Create a shared folder for this group at /home/engineers.

Command to create the shared folder: sudo mkdir -p /home/engineers
Change ownership on the new engineers' shared folder to the engineers group.

Command to change ownership of engineer's shared folder to engineer group: sudo chmod -R 775 /home/engineers

![image](https://user-images.githubusercontent.com/93474690/145323718-7ad6b68a-d7d3-4333-a983-bce44718e4c3.png)

Step 4: Lynis Auditing
Command to install Lynis: sudo apt-get install lynis -y

Command to see documentation and instructions: sudo lynis show commands or sudo lynis --help

![image](https://user-images.githubusercontent.com/93474690/145323807-dcadb78e-b8d6-4d5a-a0cc-4ec5bbf78abd.png)

![image](https://user-images.githubusercontent.com/93474690/145323869-e00fd8a0-93a1-4d15-a755-187361d077b8.png)

![image](https://user-images.githubusercontent.com/93474690/145323930-f1aa30ee-711b-4e5d-bf29-c89cf51f65ed.png)

![image](https://user-images.githubusercontent.com/93474690/145324003-6148a205-744a-41ff-b407-d7d3d3173701.png)

![image](https://user-images.githubusercontent.com/93474690/145324083-8f2d8f7e-4d56-45ad-9c23-e55e7549fe26.png)

Command to run an audit: sudo lynis audit system to run an audit

Provide a report from the Lynis output on what can be done to harden the system.

Screenshot of report output:

![image](https://user-images.githubusercontent.com/93474690/145324183-7e246852-f640-4bc2-ab14-17eca72fb2af.png)

![image](https://user-images.githubusercontent.com/93474690/145324235-90763b53-642c-4ce2-967f-383b59cf7ae5.png)

sudo cat /var/log/lynis.log - to view the logs.
Bonus
Command to install chkrootkit: sudo apt-get update

![image](https://user-images.githubusercontent.com/93474690/145324308-66e1c4ce-04d4-4fab-9df1-5cc33cf2213b.png)

sudo apt install chkrootkit
![image](https://user-images.githubusercontent.com/93474690/145324406-1f56bfa5-4891-4eff-b3be-1981a053c170.png)

sudo chkrootkit -V
![image](https://user-images.githubusercontent.com/93474690/145324505-dc39dff5-3355-4d34-b973-e25d16644f0f.png)


Command to see documentation and instructions: sudo chkrootkit -h
![image](https://user-images.githubusercontent.com/93474690/145324559-b677dd57-b8c0-41cf-98b8-80b858f9f271.png)

Command to run expert mode: sudo chkrootkit -x

Provide a report from the chrootkit output on what can be done to harden the system.

Screenshot of end of sample output:

! root        20688 pts/0  /bin/sh /usr/sbin/chkrootkit -x
! root        21121 pts/0  ./chkutmp
! root        21123 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        21122 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        20687 pts/0  sudo chkrootkit -x
! sysadmin     2928 pts/0  bash
chkutmp: nothing deleted
not tested

![image](https://user-images.githubusercontent.com/93474690/145324656-611d9a4f-f833-42a7-8f0d-979ac1e41aca.png)
