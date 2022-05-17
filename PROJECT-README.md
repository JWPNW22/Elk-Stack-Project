## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load balancers protect us from DDOS attacks.
The jump-box gives us remote access into our Ansible server.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- _TODO: What does Filebeat watch for?_  Large streams of data to alert of a possible attack
- _TODO: What does Metricbeat record?_   System metrics of the server and services running on the server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|-------------|------------|----------|---------------|
| Jump Box    | Gateway    | 10.0.0.4 | Linux         |
| Web1-1      | Web Server | 10.0.0.5 | Linux         |
| Web-2       | Web Server | 10.0.0.8 | Linux         |
| Elk-Host-VM | Monitoring | 10.1.0.5 | Linux         |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 66.169.249.203

Machines within the network can only be accessed by each other.
- The Web-1 and Web-2 VM's.  IP= 20.239.143.119

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |
| Elk      | No                  | 10.1.0.5             |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.8             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- We can configure and deploy multiple machines very quickly without having to access them.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- install docker module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat will detect any changes to the filesystem and logs them.
- Metricbeat will detect any changes to the system metrics such as failed login attempts or cpu ussage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the hosts file to include elk.
- Run the playbook, and navigate to http://20.213.93.175:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
  pentest.yml  /etc/ansible/

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_


- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ssh <username>@<ip-of-jumpbox>
sudo docker container list -a
sudo docker start <specified-container>
sudo docker attach <specified-container>
#"copy playbook in apropriate directory"
ansible-playbook install-elk.yml
ssh <username>@<ip-for-host-vm>
sudo docker list container -a
sudo docker start <container-name>
then navigate to ur