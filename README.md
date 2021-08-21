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


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  - One main advantage would be YAML Playbooks. It is the best alternative for configuration management/automation.
  - It is also able to automate complex multi-tier IT application environemtns.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
  - First I, SSH into the Jump-Box-Provisioner (ssh azadmin@40.87.111.46)
  - Start/Attached to the ansible docker (sudo docker start peaceful_robinson)/(sudo docker attach peaceful_robinson)
  - Went to /etc/ansible/ directory and created the ELK playbook (elk_Playbook.yml)
  - Ran the elk_Playbook.yml in that same directory (ansible-playbook elk_Playbook.yml)
  - Lastly, I SSH into the Web-3(ELK VM) to verify the server is up and running.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Web-3(ELK VM)](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Screenshots/elk-VM%20Docker%20ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring
  - Web-1 (10.0.0.9)
  - Web-2 (10.0.0.10)

- We have installed the following Beats on these machines:
  - [Filebeat Modules Status](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Screenshots/filebeat-syslog-dashboard.png)
  - [Metricbeat Modules Status](https://github.com/TareqHasan18/CyberSecurity_BootCamp_Project_1/blob/main/Screenshots/metrickbeat-docker-dashboard.png)

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
  - Filebeat is used to collect log files from specific files on remote machines.

  - Examples of Filebeats can be files that are generated by Apache, Microsoft Azure tools, the Nginx web server, and MySQl databases.

  - Metricbeat collects machine metrics.

  - It is simply a measurement to tell analysts how healthy it is.

  - Examples of Metricbeat can be CPU usage/Uptime


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

---Filebeat---
  - Copy the filebeat-configuration.yml file to /etc/ansible/files.
  - Update the filebeat-configuration.yml file to include the ELK private IP in lines 1106 and 1806.
  - Run the playbook, and navigate to http://[My.Elk.VM.PublicIP]:5601/app/kibana (ELK-VM public IP) Clicked Add Log Data, Clicked System Logs,
Clicked on the DEB tab under Getting Started and then clciked "Check Data" in step 5 to check that the installation worked as expected.

---Metricbeat---

  - Copy the metricbeat-configuration.yml file to /etc/ansible/roles/files.
  - Update the metricbeat-configuration.yml file to include the ELK private IP in lines 62 and 95.
  - Run the playbook, and navigate to http://[My.Elk.VM.PublicIP]:5601/app/kibana (ELK-VM public IP) Clicked Add Metric Data, Clicked Docker Metrics,
Clicked on the DEB tab under Getting Started and then clciked "Check Data" in step 5 to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook? 
  - filebeat-playbook.yml, metricbeat-playbook.yml, elk-playbook.yml
- Where do you copy it? 
  - /etc/ansible for elk-playbook.yml and /etc/ansible/roles for filebeat-playbook.yml and metricbeat-playbook.yml
- Which file do you update to make Ansible run the playbook on a specific machine? 
  - /etc/ansible/hosts file (IP of the Virtual Machines).
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?
  - I have to specify two separate groups in the etc/ansible/hosts file. One of the groups will be webservers which has the IPs of the VMs that I will install Filebeat to. The other group is named elk which will have the IP of the VM I will install ELK to.
- Which URL do you navigate to in order to check that the ELK server is running?
  - http://[My.Elk.VM.PublicIP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

```- ssh azadmin@40.87.111.46 //to connect with Jump-Box-Provisioner
- sudo docker container ls -a //to check the container list
- sudo docker start peaceful_robinson //to start container
- sudo docker attach peaceful_robinson //to attach container
- curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/filebeat-config.yml //to download filebeat config file.```

```-------Filebeat---------

- To create the filebeat-configuration.yml file: nano filebeat-configuration.yml. For this, I used the filebeat configuration file template.

- To create the playbook: nano filebeat-playbook.yml

  ---
- name: installing and launching filebeat
  hosts: webservers
  become: true
  tasks:


  - name: download filebeat deb
    command: curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.0-amd64.deb
 
  - name: install filebeat deb
    command: sudo dpkg -i filebeat-7.4.0-amd64.deb

  - name: drop in filebeat.yml 
    copy:
      src: /etc/ansible/files/filebeat-config.yml
      dest: /etc/filebeat/filebeat.yml

  - name: enable and configure system module
    command: filebeat modules enable system

  - name: setup filebeat
    command: filebeat setup

  - name: start filebeat service
    command: service filebeat start

  - name: enable service filebeat on boot
    systemd:
      name: filebeat
      enabled: yes

---
-To run the playbook: ansible-playbook filebeat-playbook.yml

* In order to run the playbook, user have to be in the directory the playbook is at, or give the path to it (ansible-playbook /etc/ansible/roles/filebeat-playbook.yml

***The same process for metricbeat as well.```

