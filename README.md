# UCI-Project1
Project 1 Files
The files in this repository were used to configure the network depicted below.

Network-diagram-project1

These files have been tested and used to generate a live ELK deployment on AWS. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yaml file may be used to install only certain pieces of it, such as Filebeat.

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load Balancers protect organizations from distributed denial-of-service (DDoS) attacks by off-loading the data from the organization's server to a cloud server. Jump boxes provide organizations with a clear and straightforward starting server, where they can then securely access other servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics. Filebeat watches for log files or locations ultimately for forwarding and centralizing them. Metricbeat records metrics from the operating system and services on the server and sends them to an output.

The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System
Jump Box	Gateway	172.31.41.120	Linux- AMI
Webserver1	Server	172.31.42.2	Linux- AMI
Webserver2	Server	172.31.22.245	Linux- AMI
ELK	Server	172.31.37.23	Linux- Ubuntu
Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the Personal Home IP.

Machines within the network can only be accessed by Jump Box, IP 172.31.41.120.

A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump Box	Yes	Personal Home IP
Webserver1	No	172.31.41.120
Webserver2	No	172.31.41.120
ELK	No	172.31.41.120
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the process of configuring the ELK machine became faster, IT admins have time to focus on other aspects for success, and everything is configured the same way every time.

The playbook implements the following tasks:

The first step of the playbook is to install docker.io with a present state.
The second step of the playbook is to increase virtual memory with the command sysctl -w vm.max_map_count=262144.
The third step of the playbook is to install pip with a present state.
The fourth step of the playbook is to install docker python module with a present state.
The fifth step of the playbook is to download and launch a docker web container with the image sebp/elk:761, a started state, and published ports of 5601, 9200, and 5044.
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

Docker-ps-output

Target Machines & Beats
This ELK server is configured to monitor the following machines:

Webserver1, IP 172.31.42.2
Webserver2, IP 172.31.22.245
We have installed the following Beats on these machines:

Filebeat
Metricbeat
These Beats allow us to collect the following information from each machine:

Filebeat collects log events from the log files and locations that it monitored. An example of what I expect to see is logs from MySQL.
Metricbeat collects metrics from the operating system and services on the server. An example of what I expect to see is CPU usage logs.
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the playbook file to your ansible directory.
Update the config file to include your ELK's private IP address.
Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.
