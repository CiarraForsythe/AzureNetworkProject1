## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/CiarraForsythe/AzureNetworkProject1/blob/master/Diagrams/Untitled%20Diagram.pdf.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK file may be used to install only certain pieces of it, such as Filebeat.

  -https://github.com/CiarraForsythe/AzureNetworkProject1/blob/master/Ansible

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
Load balancing defends against DDoS by shifting the attack traffic from one server to a cloud provider. A Jump Box advantages are that it can monitor different security zones and can provide a way to access between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the services and system logs.

Filbeats monitor the log files and collects log events, it then forwards this information to elasticsear or logstash.

Metricbeat records metrics from the system and services running on the server.

The configuration details of each machine may be found below.

| Name        | Function   | IP Address | Operating System |
|-------------|------------|------------|------------------|
| Jump Box    | Gateway    | 10.0.0.4   | Linux            |
| Web 1       | Web server | 10.0.0.7   | Linux            |
| Web 2       | Web server | 10.0.0.8   | Linux            |
| Web 3       | Web server | 10.0.0.9   | Linux            |
| Elk Project | Elk stack  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 10.0.0.7 
- 10.0.0.8
- 10.0.0.9
- 10.1.0.4 


Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible | Allowed IP Addresses |
|-------------|---------------------|----------------------|
| Jump Box    | Yes                 | 52.188.22.103        |
| Web 1       | NO                  | 40.121.61.150        |
| Web 2       | NO                  | 40.121.61.150        |
| Web 3       | NO                  | 40.121.61.150        |
| Elk Project | Yes                 | 40.118.206.90        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The main advantage of automating configuration with Ansible does not require an agent to be installed.

The playbook implements the following tasks:
- Config Elk VM with docker
- Increase Virtual Memory
- Install Docker
- Install pip3
- Install Docker Python module
- Download and launch a docker elk container
-Enable docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.7
- 10.0.0.8
- 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
-- Filebeat helps to generate and organize log files to send the output to logstash and Elasticsearch.
- Metricbeat  collects metrics and statistics on the system, such as uptime, CPU usage and services running on the server and sends the output to Logstash and Elasticsearch.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ELK playbook file to /etc/ansible/roles.
- Update the hosts file to include the IP addresses and groups that will be automated

- Run the playbook, and navigate to http://40.118.206.90/appl/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- YML file is the playbook? Where do you copy it? /etc/ansible/roles directory has the ansible playbooks
- _Which file do you update to make Ansible run the playbook on a specific machine? /etc/ansible/hosts
How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
In order to use ansible to configure the ELK server you must add it to the list of machines ansible discover and connect to that is stored in the `hosts` text file.  When you run playbooks with Ansible, you specify which machine or group to run them on. This allows you to run certain playbooks on some machines, but not on others.
- _Which URL do you navigate to in order to check that the ELK server is running? Kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
1. Connect to your jumpbox using $ ssh sysadmind@ Jump box external IP
2. Connect to ansible container using $ sudo docker container list -a
$sudo docker start festive_sinoussi (Container name)
$sudo docker attach festive_sinoussi (Container name)
3. To run the playbook use ~#ansible-playbook /etc/ansible/roles/elk_playbook.yml
4. To edit or update the playboook ~#nano /etc/ansible/roles/elk_playbook.yml
