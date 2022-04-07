## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.
  
  - [Ansible Filebeat Config](https://github.com/apellegatta/ElkStack/blob/main/Ansible/ansible/filebeat-config.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available , in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? Availability by shifting traffic which helps defend against denial of service attacks.  What is the advantage of a jump box? having a jumpbox between your local and vm adds another step that an attacker would have to get through before getting to target virtual machines.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the performance and system logs.
- What does Filebeat watch for?_ watches log files on on virutal machines. 
- What does Metricbeat record?_  metrics of the virtual machine's performance.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 20.58.167.26 | Linux           |
| Web1     | VM       |10.1.0.5    |  Linux           |
| Web3     | VM        |10.1.0.6    |  Linux           |
| Elk     |  VM        |20.213.237.110| Linux           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 20.58.167.26

Machines within the network can only be accessed by SSH.
- Jumpbox@20.58.167.26

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.138.238.186       |
| Web1     | no                  |20.58.167.26          |
| Web3     | no                  |20.58.167.26          |
|elk       | no                  |20.58.167.26  

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- eliminates repetitive tasks of manual configuration and saves time

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...create yml playbook to install docker and configure the container 
- ...run the playbook
- ...nano into hosts file and add the IP of the elk vm
- then create playbook to configure elk server and run playbook

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!https://github.com/apellegatta/ElkStack/blob/main/Linux/dockerps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.5
- 10.1.0.6

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat collects log data from the virtual machines which indicates information of logging into the vm. metricbeat collects data such as cpu usage of the virtual machines.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat config  file to Web VM's.
- Update the config file
- Run the playbook, and navigate to check incoming data to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- filebeat download, copied to Web vm's
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? filebeat config
- Which URL do you navigate to in order to check that the ELK server is running? http://20.213.237.110:5601/app/kibana#/management/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
