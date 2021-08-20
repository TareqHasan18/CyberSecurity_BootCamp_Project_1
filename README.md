# CyberSecurity_BootCamp_Project_1


The files in this repository were used to configure the network depicted below.

[Project_1_Network_Diagram](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Diagram/Network%20Diagramm.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Project 1 Red Team Network Diagram file may be used to install only certain pieces of it, such as Filebeat.

[filebeat-playbook.yml](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Ansible/filebeat-playbook.yml.rtf)\
[filebeat-config.yml](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Linux/filebeat-config.yml.rtf)\
[metricbeat-playbook.yml](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Ansible/metricbeat-playbook.yml.rtf)\
[metricbeat-config.yml](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Linux/metricbeat-config.yml.rtf)\
[elk-playbook.yml](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Ansible/elk-playbook.yml.rtf)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
