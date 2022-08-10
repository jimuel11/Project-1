# Project-1 
# Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

<!-- images -->
![Markdown Logo](https://github.com/jimuel11/Project-1/blob/main/PJ1%20-%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

filebeatplaybook.yml

 ### This document contains the following details:

* Description of the Topology
* Access Policies
* ELK Configuration
* Beats in Use
* Machines Being Monitored
* How to Use the Ansible Build
* Description of the Topology




The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the servers.
Load balancers protect the servers, they manage and distribute incoming traffic to the servers and may mitigate incoming DoS attacks. The Jumpbox acts as a gateway router between the VM’s we have created. This allows us to easily secure and monitor all the VM’s as we would only need to monitor the jumpbox.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the web servers and system files.
Filebeat is responsible for generating and organizing log information about the file system.
What does Metricbeat record? 





<!-- Tables -->

| Name          | Function      | IP Address | Operating System |
| ------------- |:-------------:| ----------:| ---------------- |
| Jumpbox       | Gateway       | 10.0.0.1   |      Linux       |
| Web Server 1  | Server 1      | 10.0.0.6   |      Linux       |
| Web Server 2  | Server 2      | 10.0.0.7   |      Linux       |
| Elk Server    | Install Elk   | 10.0.1.4   |      Linux       |



## Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox Virtual machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
120.149.104.157

A summary of the access policies in place can be found in the table below.

<!-- Tables --> 
| Name       | Publicly Accesible | Allowed IP Addresses |
| ---------- | :----------------: | :------------------: |
| Jumpbox    | Yes                | 120.149.104.157      |
| Webservers | No                 | 10.10.0.5            |
| ELK        | Yes                | 12.120.104.157       |









## Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you are able to run the created scripts within the command line which will be consistent.
The playbook implements the following tasks:
#### NAME: Configure Elk VM with Docker
* Install docker.io
* Install python3-pip
* Install Docker Module
* Increase Virtual memory to a value of “262144”
* Launch the Elk Image (sebp/elk:761) into the container
* Publish the ports on which Elk is running on : (5601, 9200, 5044)
* Allowing the docker service to be enabled on boot




Target Machines & Beats
This ELK server is configured to monitor the following machines:
Webserver1: 10.0.0..6
Webserver2: 10.0.0.7

We have installed the following Beats on these machines:
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat is responsible for collecting and shipping any log information that occurs in the machines. Filebeat can display the Syslog events and hostnames.
Metricbeat assists the servers we created by collecting metrics from the operating system and services. The information that it collects may be - memory and cpu usage, etc.






## Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the Filebeat-configuration.yml file to the ansible directory (~/etc/ansible).
- Update the hosts file to include web servers 10.0.0..6 10.0.0.7
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

The playbook file  is called the filebeat-playbook.yml and you would need to copy this into the /etc/ansible/roles/.

##### Which file do you update to make Ansible run the playbook on a specific machine? 
You would need to update the Filebeat-config.yml in order for the Ansible to run smoothly : open the .yml file and scroll down to #1106 and replace the IP addresses with the IP address of the ELK machine.

You  would also need to do this for the line #1806.


When creating the playbook yml that will install the ELK, make sure the ‘hosts’ section has the right server on which you intend to install the ELK on.

For configuring where to install Filebeat, you would have to edit the playbook filebeat config file and insert the right IP addresses of the servers you would want it installed on.

This url http://[your.VM.IP]:5601/app/kibana will redirect you to a website in which you can see if the ELk server is running.

 In order to run the playbook use the command - ansible-playbook (the name of the playbook created).
