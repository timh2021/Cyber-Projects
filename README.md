## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/timh2021/Cyber-Projects/blob/main/Diagrams/Network%20diagrams/Network2.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - DVWA_My-playbook.yml.txt
  - Host.txt
  - ansible.cfg.txt
  - filebeat-config.yml.txt
  - filebeat-playbook.yml.txt
  - metricbeat-config.yml.txt
  - metricbeat-playbook.yml.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

- What aspect of security do load balancers protect?

A load balancer intelligently distributes traffic from clients across multiple servers without the clients having to understand how many servers are in use or how they are configured. Because the load balancer sits between the clients and the servers it can enhance the user experience by providing additional security, performance, resilience and simplify scaling your website
 A load balancer can add additional layers of security to your website without any changes to your application.
-- Protect applications from emerging threats
-- Authenticate User Access
-- Protect against DDoS attack
-- Simplify PCI compliance
-- SSL Offload
-- Traffic Compression
-- Traffic Caching
-- HTTP 2.0 Support

- What is the advantage of a jump box?

A jump box limits the access that the public has to your virtual network. Other servers on the network are not directly exposed through a public IP. In order to access the other servers on the network, an individual goes through the jumpbox, and needs the private IPs of the servers. In addition, a jumpbox can allow for more uniformity and better version control for other servers on the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- What does Filebeat watch for?

  Filebeat watches for changes to files and when they occured by looking at log files
  
- What does Metricbeat record?

  Metricbeat records metrics from the Operating System and Services running on the server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway & run Docker w/ Ansible  | 10.0.0.4   | Linux (Ubuntu 18.04)            |
| Web-1     |   Web Server w/DVWA       |    10.0.0.5        |   Linux (Ubuntu 18.04)               |
| Web-2     |   Web Server w/DVWA       |   10.0.0.6         |     Linux (Ubuntu 18.04)             |
| ELKStack    |    Server (ELK Container & Kibana)      |  10.1.0.4          |    Linux (Ubuntu 18.04)              |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- Access to the machine is only allowed from Home IP addres using an SSH input

Machines within the network can only be accessed by Jump Box VM.

- Which machine did you allow to access your ELK VM? 
  
  Jump Box VM

- What was its IP address?

  

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | Home Network Public IP    |
| Web-1    |  Yes (Port 80)      |        Home Network Public IP              |
|  Web-2   |   Yes (Port 80)      |       Home Network Public IP               |
| ElKStack |   Yes (Port 5601)      |Home Network Public IP
| Load Balancer  |  Yes (Port 80)|  Home Network Public IP

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
