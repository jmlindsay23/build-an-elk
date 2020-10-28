# build-an-elk
How to build an ELK server environment

Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
ELK Stack Deployment Diagram
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk Playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be capable of handling large amounts of traffic, in addition to restricting access to the network. It helps protect specifically against Denial of Service attacks by routing attack traffic away from the corporate server to a public cloud provider.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.



The configuration details of each machine may be found below.



+---------+---------------+------------+------------------+
|   Name  |    Function   | IP Address | Operating System |
+---------+---------------+------------+------------------+
| JumpBox |    Gateway    |  10.0.0.4  |       Linux      |
+---------+---------------+------------+------------------+
|   EPVM  |   ELK Server  |  10.1.0.4  |       Linux      |
+---------+---------------+------------+------------------+
|  Web-1  | Web Server #1 |  10.0.0.5  |       Linux      |
+---------+---------------+------------+------------------+
|  Web-2  | Web Server #2 |  10.0.0.6  |       Linux      |
+---------+---------------+------------+------------------+
|  Web-3  | Web Server #3 |  10.0.0.7  |       Linux      |
+---------+---------------+------------+------------------+

 ### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the JumpHost machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 72.219.85.153
- 172.17.0.2

Machines within the network can only be accessed by SSH.  The only machine that can access the ELK VM is the JumpHost (IP Address: 10.0.0.4)









A summary of the access policies in place can be found in the table below.

+----------+---------------------+----------------------+
|   Name   | Publicly Accessible | Allowed IP Addresses |
+----------+---------------------+----------------------+
| JumpHost |         Yes         |     72.219.85.153    |
|          |                     |      172.17.0.2      |
|          |                     |       10.0.0.4       |
+----------+---------------------+----------------------+
|   EPVM   |          No         |       10.0.0.4       |
+----------+---------------------+----------------------+
|   Web-1  |          No         |       10.0.0.4       |
+----------+---------------------+----------------------+
|   Web-2  |          No         |       10.0.0.4       |
+----------+---------------------+----------------------+
|   Web-3  |          No         |       10.0.0.4       |
+----------+---------------------+----------------------+

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it limits the amount of time and detail needed to configure the environment.  It also limits the possibility of user error in the setup process.

The playbook implements the following tasks:
-	Install Docker
-	Install Python
-	Use sysctl to increase memory on VM
-	Download and launch a docker elk container
-	Install Filebeat
-	Install Metricbeat
