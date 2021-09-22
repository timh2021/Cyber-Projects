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
- Description of the Topology
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

 Jump Box VM Public IP is 138.91.177.129 and Private IP is 10.0.0.4 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | 138.91.177.129    |
| Web-1    |  Yes (Port 80)      |        138.91.177.129              |
|  Web-2   |   Yes (Port 80)      |       138.91.177.129               |
| ElKStack |   Yes (Port 5601)      |138.91.177.129
| Load Balancer  |  Yes (Port 80)|  138.91.177.129

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allowes for ELK to be installed on multiple servers from a single ansible session, resulting in a more streamlined process and a uniform install across the servers. It also allowes version control or updates without having to manually check each server.

- What is the main advantage of automating configuration with Ansible?

By using Ansible this made it possible to configure mulitple servers with identical services without having to manually configure each server individually which saves time and ensures consistent services are provided throughout the servers.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

-  Docker.io installed and marked for present to ensure most current version
-  Install python3-pip and marked for presnt to ensure the most current version
-  Install Docker Module and marked for present to ensure that most current version
-  sysctl module to use more memory value of 262144 state marked present to en
-  Download and launch a docker elk container image sebp/elk:761 state of started and restart policy of always

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Update the path with the name of your screenshot of docker ps output](https://github.com/timh2021/Cyber-Projects/blob/main/Images/Screen%20shots/metricbeat-playbook-launch.jpg)
![Update the path with the name of your screenshot of docker ps output](https://github.com/timh2021/Cyber-Projects/blob/main/Images/Screen%20shots/filebeat-kibana-launch.jpg)
![Update the path with the name of your screenshot of docker ps output](https://github.com/timh2021/Cyber-Projects/blob/main/Images/Screen%20shots/metricbeat-kibana-launch.jpg)
![Update the path with the name of your screenshot of docker ps output](https://github.com/timh2021/Cyber-Projects/blob/main/Images/Screen%20shots/metricbeat-kibana-Desktop.jpg)
![Update the path with the name of your screenshot of docker ps output](https://github.com/timh2021/Cyber-Projects/blob/main/Images/Screen%20shots/filebeat-kibana-Dashboard.jpg)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.

Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. EG: For visual see above

Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. EG: For visual see above

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/roles/install-filebeat/files/filebeat-config.yml.
- Update the filebeat-config.yml file to include host "10.1.0.4:9200" with username "elastic" and password "changeme" and setup.Kibana host to "10.1.0.4:5601" (this needs to be the IP address of your ELk server).
- Run the playbook, and navigate to Kibana (Elk GUI interface) and click "Check Data" to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook? 

   filebeat-config.yml
 
- Where do you copy it?

  /etc/ansible/roles/install-filebeat/tasks/filebeat-playbook.yml

- Which file do you update to make Ansible run the playbook on a specific machine? 

   Ansible.cfg and Host

- How do I specify which machine to install the ELK server on versus which to install Filebeat on?

  filebeat-config.yml

- Which URL do you navigate to in order to check that the ELK server is running?

  http://20.85.236.65:5601/app/kibana   The link will not be active because the system is not running

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

You will need to have an Azure account and set up the required VM's and NSG setups.
From there to set up the DVWA playbook in your Bash account. 

Gain access to your jump server. The next step is to access the Ansible
  These are following command:
   :sudo docker container list -a
   :sudo docker start <use the name that comes form the container list>
   :sudo docker attach <name>
 if done correctly you should now be in Ansible
 
  To move to the Playbooks you will to need to do the following:
  
  cd /etc/ansible   then once in do  ls
  
  The DVWA playbook will not be there more than likely. So you will need to create one. You initiate the work with either Nano, VI or VIM
  
  The VI is the editor command I use. 
  Type VI  and the name you will be naming this playbook. It must follow this format. Here is an example (my-playbook.yml)  The name must  have .yml at the very end.   
  Once in hit I to insert, then enter the below items
  
---
- name: my-playbook.yml
  hosts: webservers
  become: true
  tasks:
  - name: docker.io
    apt:
     update_cache: yes
     name: docker.io
     state: present
     force_apt_get: yes

  - name: Install pip3
    apt:
     name: python3-pip
     state: present

  - name: Install Docker python module
    pip:
     name: docker
     state: present

  - name: download and launch a docker web container
    docker_container:
     name: dvwa
     image: cyberxsecurity/dvwa
     state: started
     restart_policy: always
     published_ports: 80:80

  - name: Enable docker service
    systemd:
     name: docker
     enabled: yes
  
  Then hit ESC     the press the shift button  and press :wq  and the hit enter
  
  This will bring you back. Now type    ls   and your new playbook will show up
