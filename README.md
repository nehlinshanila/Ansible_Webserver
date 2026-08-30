# 🚀 Ansible Web Server Deployment

<p align="center">
  <b>Automated Multi-VM Web Server Deployment Using Ansible</b>
</p>

<p align="center">

![Ansible](https://img.shields.io/badge/Automation-Ansible-EE0000?logo=ansible&logoColor=white)
![YAML](https://img.shields.io/badge/Configuration-YAML-CB171E?logo=yaml&logoColor=white)
![Linux](https://img.shields.io/badge/Platform-Linux-FCC624?logo=linux&logoColor=black)
![Python](https://img.shields.io/badge/Web_Server-Python-3776AB?logo=python&logoColor=white)
![GitHub](https://img.shields.io/badge/Version_Control-GitHub-181717?logo=github&logoColor=white)

</p>

---

## 📌 Overview

This project demonstrates the use of **Ansible automation** to deploy and manage web servers across multiple virtual machines.

A single Ansible playbook is used to configure two web server instances, **VM1** and **VM2**. Each server runs on **port 8080** and displays a unique web page.

The project also supports both **deployment** and **undeployment** of the web server resources through Ansible tags.

> **Course Assignment:** HW #1 – Ansible Web Server Deployment

---

## 🎯 Project Objective

The objective of this project is to automate the configuration of two virtual machines using Ansible.

The automation performs the following tasks:

- 🔗 Connects to multiple remote virtual machines.
- 📁 Creates the required web directory.
- 📄 Generates a custom `index.html` page.
- 🌐 Starts a web server on port `8080`.
- 🖥️ Displays a unique message on each server.
- 🛑 Stops the web server when undeployment is requested.
- ⚡ Uses a single Ansible playbook to manage multiple machines.

---

## 🏗️ Project Architecture

```text
                    ┌──────────────────────────┐
                    │  Ansible Control Machine │
                    │                          │
                    │   hosts.ini              │
                    │   playbook.yml           │
                    └────────────┬─────────────┘
                                 │
                        SSH / Ansible
                                 │
                ┌────────────────┴────────────────┐
                │                                 │
                ▼                                 ▼
      ┌──────────────────┐              ┌──────────────────┐
      │       VM1        │              │       VM2        │
      │   192.168.64.6   │              │   192.168.64.8   │
      │                  │              │                  │
      │  Web Server      │              │  Web Server      │
      │  Port: 8080      │              │  Port: 8080      │
      └────────┬─────────┘              └────────┬─────────┘
               │                                 │
               ▼                                 ▼
    Hello World from SJSU-1          Hello World from SJSU-2






🛠️ Technologies Used
Technology	Purpose
Ansible	Infrastructure automation
YAML	Playbook configuration
Python	Lightweight HTTP web server
Linux	Virtual machine operating system
SSH	Remote machine communication
Git	Version control
GitHub	Repository hosting
📂 Repository Structure
Ansible_Webserver/
│
├── hosts.ini        # Ansible inventory
├── playbook.yml     # Deployment and undeployment automation
└── README.md        # Project documentation
🖥️ Managed Virtual Machines
Server	IP Address	Web Server Port	Web Page
VM1	192.168.64.6	8080	Hello World from SJSU-1
VM2	192.168.64.8	8080	Hello World from SJSU-2
⚙️ How It Works
1️⃣ Configure the Inventory

The hosts.ini file defines the target machines managed by Ansible.

[webservers]
192.168.64.6
192.168.64.8

This inventory allows Ansible to execute automation tasks on both virtual machines.

2️⃣ Deploy the Web Servers

Run the following command:

ansible-playbook -i hosts.ini playbook.yml -K --tags deploy

The deployment process:

Connects to both virtual machines.
Creates the required web directory.
Creates a unique index.html file.
Starts the web server.
Makes the web page available on port 8080.
3️⃣ Verify the Deployment
🖥️ VM1
curl http://192.168.64.6:8080

Expected output:

<h1>Hello World from SJSU-1</h1>
🖥️ VM2
curl http://192.168.64.8:8080

Expected output:

<h1>Hello World from SJSU-2</h1>
🛑 Undeploy the Web Servers

To stop the web servers, run:

ansible-playbook -i hosts.ini playbook.yml -K --tags undeploy

This stops the web server resources on both virtual machines.

📊 Successful Deployment

A successful Ansible execution should show both servers as reachable with no failures.

PLAY RECAP

192.168.64.6 : ok=4 changed=1 unreachable=0 failed=0 skipped=0
192.168.64.8 : ok=4 changed=1 unreachable=0 failed=0 skipped=0
✅ Deployment Status
VM1 successfully configured
VM2 successfully configured
Web directories created
Custom HTML pages generated
Web servers running on port 8080
Both servers accessible through HTTP
No unreachable hosts
No failed tasks
🔑 Ansible Concepts Demonstrated
📋 Inventory Management

The hosts.ini file defines the remote hosts that Ansible manages.

📜 Playbooks

The playbook.yml file contains the automation instructions written in YAML.

🏷️ Tags

Ansible tags allow specific parts of the playbook to be executed.

--tags deploy

Deploys the web server resources.

--tags undeploy

Stops the web server resources.

🔐 Privilege Escalation

The -K option requests the privilege escalation password when required.

🔄 Infrastructure as Code

The server configuration is stored as code, allowing the infrastructure to be:

Reproducible
Repeatable
Version controlled
Easily modified
Scalable
✨ Key Features
🤖 Automated infrastructure configuration
🖥️ Multi-server management
🌐 Custom web pages for each server
⚡ Deployment on port 8080
🏷️ Tag-based deployment and undeployment
🔄 Repeatable automation
📦 Version-controlled configuration
🔍 Easy verification using curl
📈 Easily scalable to additional servers
📈 Benefits of Using Ansible

Ansible simplifies server management by replacing repetitive manual tasks with automated and reproducible configurations.

Key benefits include:
Consistency — Both virtual machines receive the correct configuration.
Efficiency — Multiple machines can be configured simultaneously.
Scalability — Additional servers can easily be added to the inventory.
Repeatability — The playbook can be executed again whenever needed.
Reliability — Automation reduces manual configuration errors.
Maintainability — Infrastructure configuration is stored as version-controlled code.
🧪 Testing

The deployment was tested by:

Running the Ansible deployment playbook.
Confirming that both virtual machines completed successfully.
Checking the Ansible play recap.
Using curl to access each web server.
Verifying the unique HTML content on each VM.
Running the undeployment tasks to stop the web servers.
🏁 Conclusion

This project successfully demonstrates how Ansible can automate web server deployment across multiple virtual machines.

Using a single control machine and Ansible playbook, two independent web servers were configured and deployed successfully. Each server runs on port 8080 and serves a unique web page.

The project demonstrates the advantages of automation, consistency, scalability, repeatability, and Infrastructure as Code in modern system administration and cloud environments.
