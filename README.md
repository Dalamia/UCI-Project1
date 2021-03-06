# UCI-Project1## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://github.com/Dalamia/UCI-Project1/blob/main/Images/Untitled%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [filebeat-playbook.yaml](https://github.com/Dalamia/UCI-Project1/blob/main/playbooks/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Available, in addition to restricting Access to the network.
- Load balancer help to prevent ddos attacks and seperates web traffic between to keep high efficiency.It allows you to update and control multiple servers 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Data and system Logs.
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
- Metricbeat periodically collect metrics from the operating system and from services running on the server and when it collects that metric and static data ships them to the output that you specify such as Elatsticsearch or Logstash

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway/Node conroller  |  172.31.38.145| Linux  |
| Webserver 1| webserver|  172.31.38.105 | Linux  |
| Webserver 2| webserver|  172.31.2.151 | Linux  |
| ELK     |ELK server host| 172.31.83.200 |Ubuntu|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- It is only allowed access through my personal ip

Machines within the network can only be accessed by Jumpbox
Through ssh connnection 172.31.38.145
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No (SSH)            | My personal IP    |
| Webserver 1 |      yes (HTTP)   |  172.31.38.145                 |
| Webserver 2 |      yes (HTTP)   |  172.31.38.145              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- By automating the configuration of ansible it decreases the time it would take to do it from scratch as well as helping to limit mistakes by user error.

The playbook implements the following tasks:
- installs docker.io
- increases virtual memory
- installs Pip (python 3)
- installs docker python module (docker)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Elk Docker Ps](https://github.com/Dalamia/UCI-Project1/blob/main/Images/Elk%20Docker%20ps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Webserver 1: 172.31.38.105
- Webserver 2: 172.31.2.151
We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects:  audit logs, deprecation logs, gc logs, server logs, and slow logs.
- Metricbeat collects: metric and statistics data.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Intall-elk.yml file to Elk VM.
- Update the hosts file to include webserver 1 and webserver 2
- Run the playbook, and navigate to you browser and enter the public ip/port to open kibana to check that the installation worked as expected (port 5601).

- _Which file is the playbook? Where do you copy it? You have to nano into the /etc/ansible directory and you have your ansible files in there such as Filebeat-playbook.yaml
- You have to nano into the /etc/ansible/hosts file and specify the ip of the machines you want to allow the playbook to run on as well as the filebeat config files.
- Which URL do you navigate to in order to check that the ELK server is running? input elk server public ip then :5601/app/kibana [kibana](http://20.98.114.15:5601/app/kibana)

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
