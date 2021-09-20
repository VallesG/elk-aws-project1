# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/VallesG/elk-aws-project1/blob/main/diagrams/network-diagram.png)



These files have been tested and used to generate a live ELK deployment on AWS. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.
 
 [install-elk.yml](https://github.com/VallesG/elk-aws-project1/blob/main/Ansible/install-elk.yml)
 
 [filebeat-playbook.yml](https://github.com/VallesG/elk-aws-project1/blob/main/Ansible/filebeat-playbook.yml)
 
 [metricbeat-playbook.yml](https://github.com/VallesG/elk-aws-project1/blob/main/Ansible/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network. Load balancers distribute incoming traffic amongst various web servers to achieve high availability. The main advantage of using a Jumpbox is to have one point of access to configure and administer all parts of the network. 

 Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
	
Filebeat monitors logs and watches for specific log directories and files.

 Metricbeat records metric and statistical data from the servers and operating system. 

The configuration details of each machine may be found below.

| Name       | Function       | IP Address    | Operating System |
|------------|----------------|---------------|------------------|
| Jumpbox    | Gateway        | 172.31.25.63  | Amazon Linux     |
| webserver1 | Web Server         | 172.31.26.184 | Amazon Linux     |
| webserver2 | Web Server         | 172.31.94.129 | Amazon Linux     |
| Elk2       | ELK Monitoring | 172.31.46.71  | Linux Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Personal IP Address
	

Machines within the network can only be accessed by the Jumpbox using SSH. .

The ELK server can be accessed using the Jumpbox via SSH and also through a web browser if you know the personal IP address

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible |  Allowed IP Address |
|------------|---------------------|---------------------|
| Jumpbox    | Yes                 | 172.31.25.63        |
| webserver1 | No                  | 172.31.26.184       |
| webserver2 | No                  | 172.31.94.129       |
| Elk2       | No                  | 172.31.46.71        |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because this allows faster configuration, and means less errors because each machine can be configured exactly the same in one instance.
  
The playbook implements the following tasks:

 1. Install docker.io, pip3, and the docker python module

 2. Increase virtual memory
 
 3. Download container image
 
 4. Launch container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/VallesG/elk-aws-project1/blob/main/diagrams/dockerps.png)

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

webserver1 - 172.31.26.184

webserver2 - 172.31.94.129


We have installed the following Beats on these machines:

Filebeat

Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat monitors log files and collects log events for the webserver VMs and sends them to the Elk server.  The log data from filebeat is shown in a GUI using the Elk server.
Metricbeat collects metrics and statistical data from the webservers and sends them to  the Elk server.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

Copy the filebeat-configuration.yml file to /etc/ansible

Update the filebeat_configuration.file to include the private IP address Elk server on lines    1106    and 1806

Run the playbook, and navigate to Kibana(http://[Elk Sever IP]:5601)  to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

Which file is the playbook? filebeat-playbook.yml

Where do you copy it? /etc/ansible

Which file do you update to make Ansible run the playbook on a specific machine? /etc/ansible/hosts

How do you specify which machine to install the ELK server on versus which to install Filebeat on? Editing thr hosts file in /etc/ansible allows you to specify by private IP

Which URL do you navigate to in order to check that the ELK server is running? 
172.31.46.71:5601	



