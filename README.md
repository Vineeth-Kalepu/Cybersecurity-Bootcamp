# Cybersecurity-Bootcamp
### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Path with the name of my diagram: Diagrams/Diagram_3.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _YML_ file may be used to install only certain pieces of it, such as Filebeat.

Path to ansible playbook file: Ansible/ELK Stack Project Week/elk.yml.pdf

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly _Productive_, in addition to restricting _Traffic_ to the network.

-What aspect of security do load balancers protect? 
- Load Balancers protect against DDOS attacks

-What is the advantage of a jump box?
	- Forces all traffic through a single node, making security easier

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _cloud network_ and system _files_.

-What does Filebeat watch for?
	- Filebeat watches for which files change and when

-What does Metricbeat record?
	- Collects machine metrics, such as uptime

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP_Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | VM       | 10.0.0.5   | Linux            |
| Web-2    | VM       | 10.0.0.6   | Linux            |
| Web-3    | VM       | 10.0.0.7   | Linux            |
| ELKOne   | ELK      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _Virtual_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- My home IP - 173.91.4.119

Machines within the network can only be accessed by _the jump box_.

- Which machine did you allow to access your ELK VM? What was its IP address?_
	-I allowed access from the jump box, it’s IP is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP_Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes                 | 10.0.0.1 10.0.0.2    |
| Web-1    | no                  | 10.0.0.4             |
| Web-2    | no                  | 10.0.0.4             |
| Web-3    | no                  | 10.0.0.4             |
| ELKOne   | yes                 | 10.0.0.4             |

### ELK Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible?_

This drastically reduces human error and reduces time.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image;
	-Install docker.io - 
		- apt is a built in module that abstracts management
		- force_apt_get is to force a download
		- update_cache is used to update the cache
		- name is referring to the package
		- state is used to change a packages state, in this instince to present
	-Install pip - 
		- apt is a built in module that abstracts management
		- force_apt_get is to force a download
		- name is referring to the package
		- state is used to change a packages state, in this instince to present
	-Install docker python module - 
		- apt is a built in module that abstracts management
		- name is referring to the package
		- state is used to change a packages state, in this instince to present

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Path with the name of your screenshot of docker ps output: Diagrams/Docker_ps.jpg

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- 10.0.0.4
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:

- Filebeat
- Metricbeat 

These Beats allow us to collect the following information from each machine:

- Filebeat logs information about the file system like to collect data from very specific files Microsoft azure tools
- Metric beat collects machine metrics like uptime

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _pentest.yml_ file to _/etc/ansible/_.
- Update the _/etc/ansible/hosts_ file to include_VMs you want changed_
- Run the playbook, and navigate to _the affected VMS (in this case 10.0.0.4)_ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

### Bonus 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

