# Elk-Stack-Project## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Miniexadoor/Elk-Stack-Project/blob/main/Project%201%20diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk-Stack Project file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/Miniexadoor/Elk-Stack-Project/blob/main/Filebeat_playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional, in addition to restricting high traffic to the network.

What aspect of security do load balancers protect? 
It eliminates single points of failure and prevents overloading of servers

What is the advantage of a jump box?
It creates a secure point of connection to the rest of the servers that can only be accessed by the admin.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
What does Filebeat watch for?
It monitors log files and indexes them in logstash


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

|        Name        | Function | IP Address | Operating System |   |
|:------------------:|:--------:|:----------:|:----------------:|---|
| JumpBoxProvisioner | Gateway  | 10.0.0.4   | Linux            |   |
| Elk-Server         | Server   | 10.1.0.4   | Linux            |   |
| Web-1              | Server   | 10.0.0.5   | Linux            |   |
| Web-2              | Server   | 10.0.0.6   | Linux            |   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
73.135.54.243

Machines within the network can only be accessed by JumpBoxProvisioner.
Which machine did you allow to access your ELK VM? What was its IP address?_
JumpBoxProvisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses |   |   |
|--------------------|---------------------|----------------------|:-:|---|
| JumpBoxProvisioner | Yes/No              | 73.135.54.243        |   |   |
| Elk-Server         | No                  | 10.0.0.4             |   |   |
| Web-1              | No                  | 10.0.0.4             |   |   |
| Web-2              | No                  | 10.0.0.4             |   |   |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible?
It allows for the configuration and usage of new virtual machines with yml playbooks allowing one to access those machines from a remote desktop.

The playbook implements the following tasks:
- SSH in the jumpboxprovisioner
- Start and attach the ansible docker "laughing_mcclintock
- Create the install-elk.yml in the /etc/ansible directory
- Run the install-elk.yml file in that directory
- SSH into Elk-Server to check if it is running.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring
Web-1 10.0.0.5
Web-2 10.0.0.6

We have installed the following Beats on these machines:
Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files from remote machines. They can be files from Microsoft Azure tools or MQI databases.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible.
- Update the filebeat-playbook.yml file to include the ElK-Server private ip 10.1.0.4
- Run the playbook, and navigate to https://20.210.161.47:5601 to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_

- _Which file is the playbook? Where do you copy it?_
- filebeat-playbook.yml /etc/ansible

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- /etc/ansible/hosts I make 2 seperate groups in the hosts file. One of which will be webservers while the other will be elkservers.

- _Which URL do you navigate to in order to check that the ELK server is running?
- https://20.210.161.47:5601

