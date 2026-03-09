#📌 Project Overview

This project demonstrates an automated Linux Patch Management System using a Bash Script.
It allows a system administrator to update and patch multiple CentOS servers automatically from a single admin machine using SSH-based automation.

The goal of this project is to simplify patch deployment, reduce manual effort, and maintain security across multiple servers.

---

#🎯 Objectives

- Automate Linux patch updates across multiple servers
- Use Bash scripting for remote system administration
- Implement SSH-based secure communication
- Reduce manual intervention in system patching
- Maintain updated and secure infrastructure

---

#🖥️ System Architecture

Admin Server executes the patch script and connects to multiple client servers via SSH.

            +------------------+
            |   Admin Server   |
            | Patch Script Run |
            +---------+--------+
                      |
        ---------------------------------
        |               |               |
+---------------+ +---------------+ +---------------+
| CentOS Node 1 | | CentOS Node 2 | | CentOS Node 3 |
| 192.168.1.30  | | 192.168.1.31  | | 192.168.1.32  |
+---------------+ +---------------+ +---------------+

---

#⚙️ Technologies Used

- Linux (CentOS 7)
- Bash Scripting
- SSH
- YUM Package Manager
- Virtual Machines / Local Network

---

📋 Project Requirements

Minimum setup required:

Component| Requirement
Admin Machine| Linux / CentOS
Client Servers| 2 or more CentOS systems
Network| Same LAN or reachable IP
SSH| Enabled on all servers

---

#🔑 Step 1: Configure SSH Passwordless Authentication

Generate SSH key on the admin machine:

ssh-keygen

Copy SSH key to client servers:

ssh-copy-id server1@192.168.1.30
ssh-copy-id server1@192.168.1.31
ssh-copy-id server1@192.168.1.32

Test SSH login:

ssh server1@192.168.1.30

If login happens without password, the configuration is successful.

---

#📂 Step 2: Create Server List

Create a file that stores all target server IP addresses.

nano servers.txt

Example:

192.168.1.30
192.168.1.31
192.168.1.32

---

#🧾 Step 3: Create Patch Management Script

Create a Bash script:

nano patch_management.sh

Script:

#!/bin/bash

SERVER_LIST="servers.txt"

echo "Starting Patch Management Process"
echo "---------------------------------"

for SERVER in $(cat $SERVER_LIST)
do
    echo "Connecting to $SERVER"

    ssh -t server1@$SERVER "sudo yum update -y"

    echo "$SERVER patched successfully"
done

echo "All servers patched successfully"

---

#🔐 Step 4: Make Script Executable

chmod +x patch_management.sh

---

#▶️ Step 5: Run the Patch Script

Execute the script:

./patch_management.sh

Expected Output:

Starting Patch Management Process
Connecting to 192.168.1.30
Updating packages...

Connecting to 192.168.1.31
Updating packages...

All servers patched successfully

---

#🔍 Verification

Check if updates are completed:

yum check-update

If no updates appear, the system is fully patched.

Check kernel version:

uname -r

---

#📊 Benefits of This Project

- Automates server patching
- Reduces administrative workload
- Improves system security
- Enables centralized server management
- Demonstrates practical Linux system administration skills

---

#🚀 Future Improvements

Possible enhancements include:

- Logging patch results to a file
- Adding email notification after patching
- Scheduling automatic updates using Cron
- Integrating monitoring dashboards
- Implementing Ansible-based automation

---

#📚 Learning Outcomes

Through this project you will learn:

- Linux system administration
- Bash scripting automation
- Remote server management using SSH
- Package management using YUM
- Infrastructure automation basics

---

#👨‍💻 Author

Shikhar Shukla
