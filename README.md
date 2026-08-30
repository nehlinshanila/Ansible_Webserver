Ansible Web Server Deployment
Overview

This project demonstrates the use of Ansible automation to deploy and manage web servers on two virtual machines. The web servers are configured to run on port 8080, and each server displays a unique HTML page.

The project was developed for HW #1 - Ansible.

Project Objective

The objective of this assignment is to configure two virtual machines, VM1 and VM2, and use Ansible to deploy a web server on both machines.

Each server displays a unique message:

VM1: Hello World from SJSU-1
VM2: Hello World from SJSU-2

The assignment also requires the ability to deploy and undeploy the web server resources using Ansible.

Project Architecture
                Ansible Control Machine
                         |
                         | SSH / Ansible
                ---------+---------
                |                 |
                v                 v
              VM1               VM2
        192.168.64.6      192.168.64.8
                |                 |
                v                 v
          Web Server        Web Server
           Port 8080         Port 8080
                |                 |
                v                 v
        Hello World from    Hello World from
             SJSU-1              SJSU-2
Technologies Used
Ansible
YAML
Python HTTP Server
Linux
Virtual Machines
SSH
Git
GitHub
Repository Structure
Ansible_Webserver/
│
├── hosts.ini
├── playbook.yml
└── README.md
Inventory Configuration

The hosts.ini file contains the two target virtual machines managed by Ansible.

[webservers]
192.168.64.6
192.168.64.8
Virtual Machine	IP Address
VM1	192.168.64.6
VM2	192.168.64.8
Deployment Process

The Ansible playbook performs the following tasks:

Connects to both virtual machines.
Gathers system information.
Creates the required web directory.
Creates a custom index.html page.
Starts the web server on port 8080.
Displays a unique message on each virtual machine.
Running the Deployment

To deploy the web server on both virtual machines:

ansible-playbook -i hosts.ini playbook.yml -K --tags deploy

The -K option prompts for the privilege escalation password.

After successful deployment, both web servers should be running on port 8080.

Verifying the Web Servers
VM1
curl http://192.168.64.6:8080

Expected output:

<h1>Hello World from SJSU-1</h1>
VM2
curl http://192.168.64.8:8080

Expected output:

<h1>Hello World from SJSU-2</h1>
Ansible Play Recap

A successful deployment should show both virtual machines as reachable with no failures.

192.168.64.6 : ok=4 changed=1 unreachable=0 failed=0
192.168.64.8 : ok=4 changed=1 unreachable=0 failed=0
Undeployment

The project also supports stopping the web server resources.

Run:

ansible-playbook -i hosts.ini playbook.yml -K --tags undeploy

This stops the web servers on both virtual machines.

Key Features
Automated deployment using Ansible
Management of multiple virtual machines
Custom web page for each server
Web servers running on port 8080
Tag-based deployment and undeployment
Centralized server configuration
Repeatable automation
Easy verification using curl
Version control using Git and GitHub
Ansible Concepts Demonstrated
Inventory Management

The hosts.ini file defines the remote machines that Ansible manages.

Playbooks

The playbook.yml file contains the automation tasks written in YAML.

Tags

Tags allow specific actions to be executed.

--tags deploy

deploys the web server, while:

--tags undeploy

stops the web server.

Privilege Escalation

The -K option allows Ansible to request the necessary privilege escalation password.

Benefits of Ansible

Ansible makes infrastructure management more efficient by providing:

Automation: repetitive tasks are performed automatically.
Consistency: both servers receive the same configuration.
Scalability: additional servers can easily be added.
Repeatability: the playbook can be run whenever needed.
Infrastructure as Code: configurations can be stored, version controlled, and shared.
Conclusion

This project successfully demonstrates how Ansible can automate the deployment and management of web servers across multiple virtual machines. A single playbook is used to configure both VM1 and VM2, deploy custom HTML pages, start web servers on port 8080, and manage the server lifecycle through deployment and undeployment tasks.

