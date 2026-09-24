# 🚀 Automated Web Server Deployment with Ansible

---

## 📌 Project Overview

This project demonstrates the use of **Ansible automation** to deploy and manage web servers across two virtual machines.

Instead of manually configuring each machine, Ansible is used to remotely execute deployment tasks from a centralized control system. Both web servers are configured to run on **port 8080**, while each server displays a unique message.

The project was developed as part of **HW #1 – Ansible**.

---

# 🎯 Project Objective

The objective of this assignment is to:

- Configure two virtual machines: **VM1** and **VM2**
- Use **Ansible** to manage both machines remotely
- Deploy a web server on each virtual machine
- Configure both servers to run on **port 8080**
- Display a unique web page on each server
- Provide both **deployment** and **undeployment** functionality
- Maintain the automation code in a **GitHub repository**

---

# 🖥️ Web Server Output

Each virtual machine serves a unique web page.

| Virtual Machine | IP Address | Port | Web Page |
|---|---|---|---|
| **VM1** | `192.168.64.6` | `8080` | `Hello World from SJSU-1` |
| **VM2** | `192.168.64.8` | `8080` | `Hello World from SJSU-2` |

---

# 🏗️ System Architecture


                     ┌───────────────────────┐
                     │   Ansible Control     │
                     │       Machine         │
                     └───────────┬───────────┘
                                 │
                         SSH / Ansible
                                 │
                  ┌──────────────┴──────────────┐
                  │                             │
          ┌───────▼────────┐           ┌────────▼────────┐
          │      VM1       │           │       VM2       │
          │ 192.168.64.6   │           │  192.168.64.8   │
          │   Port 8080    │           │    Port 8080    │
          │                │           │                 │
          │ Hello World    │           │ Hello World     │
          │ from SJSU-1    │           │ from SJSU-2     │
          └────────────────┘           └─────────────────┘

# 🛠️ Technologies Used

Ansible – Infrastructure automation and configuration management  
YAML – Writing the Ansible playbook  
SSH – Remote communication with target machines  
Linux – Virtual machine operating environment  
Python HTTP Server – Serving web content  
Git – Version control  
GitHub – Source code repository  

# 📁 Project Structure

Ansible_Webserver contains the following files:

hosts.ini – Defines the target virtual machines.

playbook.yml – Contains deployment and undeployment tasks.

README.md – Contains the project documentation.

# 📋 Inventory Configuration

The hosts.ini file defines the virtual machines managed by Ansible.

The two target web servers are:

192.168.64.6

192.168.64.8

This inventory allows Ansible to connect to and manage both target virtual machines.

# ⚙️ Ansible Playbook

The playbook.yml file contains the automation logic for managing the web servers.

The playbook supports two primary operations: deployment and undeployment.

## 🚀 Deploy

The deployment process:

- Connects to the target virtual machines.
- Creates the required web server resources.
- Configures the servers to run on port 8080.
- Creates a unique HTML response for each virtual machine.
- Starts the web server process.

## 🗑️ Undeploy

The undeployment process:

- Stops the running web server process.
- Removes the deployed web server resources.
- Cleans up the target virtual machines.

# ▶️ Running the Playbook

## Deploy the Web Servers

Run:

ansible-playbook -i hosts.ini playbook.yml --tags deploy

## Undeploy the Web Servers

Run:

ansible-playbook -i hosts.ini playbook.yml --tags undeploy

# 🌐 Accessing the Web Servers

After successful deployment, the web pages can be accessed through a browser.

## VM1

Address: http://192.168.64.6:8080

Expected output:

Hello World from SJSU-1

## VM2

Address: http://192.168.64.8:8080

Expected output:

Hello World from SJSU-2

# 🧪 Deployment Verification

The Ansible deployment was successfully executed on both virtual machines.

The successful PLAY RECAP showed:

192.168.64.6: ok=2, changed=1, unreachable=0, failed=0, skipped=0

192.168.64.8: ok=2, changed=1, unreachable=0, failed=0, skipped=0

The successful play recap confirms that:

- Both hosts were successfully reached.
- The deployment tasks completed successfully.
- No hosts were unreachable.
- No tasks failed.

# ✨ Key Features

- 🤖 Fully automated deployment using Ansible
- 🖥️ Multi-server configuration
- 🔐 Remote management through SSH
- 🌐 Web servers running on port 8080
- 🔄 Automated deployment and undeployment
- 📝 Infrastructure configuration stored as code
- 📦 Version-controlled using Git and GitHub

# 📚 What This Project Demonstrates

This project demonstrates important DevOps and automation concepts, including:

- Infrastructure as Code
- Configuration Management
- Multi-server Automation
- Remote Server Administration
- Repeatable Deployment
- Automated Resource Cleanup
- Git-based Version Control

------------------------------------------------------------


HW: 5

Jenkins webhook test

