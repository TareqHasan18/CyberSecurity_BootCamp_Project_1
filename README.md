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

Load balancing ensures that the application will be highly functional, in addition to restricting high-trafficing to the network.

- What aspect of security do load balancers protect? 
  - It helps prevent overloading servers as well as optimizes productivity and maximizes uptime.
  - It also adds resiliency by rerouting live traffic from one server to another causing it to eliminate single points of failure from attacks such as DDoS attack.
  
- What is the advantage of a jump box?
  - Jump-box are highly secured computers that are never used for non-admin tasks. -Throughout the years, jump-box has improved into an even more     comprehensive/lock-down secure admin workstation to decrease the chances of hackers/malware infection.
  
  Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
  
- What does Filebeat watch for?
  - It monitors the log files/locations that you specify and forwards them to Elasticsearch/Logstash for indexing.
  
- What does Metricbeat record?
  - It records metrics/statistics data and transports them to the output that you specifics thru Elasticsearch/Logstash.
  
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box Provisioner | Gateway  | 10.0.0.4(Private)//40.87.111.46(Public)   | Linux            |
| Web-1     |   Server       |      10.0.0.9(Private)      |     Linux             |
| Web-2     |    Server      |      10.0.0.10(Private)      |      Linux            |
| Web-3     |    Server      |      10.2.0.4(Private)      |        Linux          |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

- Only the Jump-Box-Provisioner machine can accept connections from the Internet. 
- Access to this machine is only allowed from the following IP addresses:
    - _67.243.194.160 (LocalHost IP address)_

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Which machine did you allow to access your ELK VM?
  - Jump-Box-Provisoner
- What was its IP address?
  - 10.0.0.4 (Private)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | 67.243.194.160   |
|  Web-1*        |  No                   |  10.0.0.9                    |
|   Web-2*       |   No                  |   10.0.0.10                   |
|  Web-3(ELK )*  |NO                   |10.2.0.4|
- All these VMs can only be accessed from the Jump-Box-Provissioner.
