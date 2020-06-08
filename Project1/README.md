## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](images/project1-1.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook (yml) file may be used to install only certain pieces of it, such as Filebeat.

- [elk-playbook](resources/elk-playbook.yml)
- [filebeat-playbook](resources/filebeat-playbook.yml) 
- [metricbeat-playbook](resources/metricbeat-playbook.yml) 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.

| Name       | Function  | IP Address | Operating System |
|------------|-----------|------------|------------------|
| Jump Box   | Gateway   | 10.0.0.4   | Ubuntu Linux     |
| DVWA-VM1   | Web App   | 10.0.0.5   | Ubuntu Linux     |
| DVWA-VM2   | Web App   | 10.0.0.6   | Ubuntu Linux     |
| ELK Server | ELK Stack | 10.0.0.7   | Ubuntu Linux     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 174.65.148.43

Machines within the network can only be accessed by JumpBoxProvisioner.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|----------  |---------------------|----------------------|
| Jump Box   | Yes                 | 174.65.148.43        |
| DVWA-VM1   | No                  | 10.0.0.4             |
| DVWA-VM2   | No                  | 10.0.0.4             |
| ELK Server | Yes                 |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- This drastically reduces the potential for human error and simplifies the process of configuring potentially thousands of machines identically all at once.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker.io (docker engine), python-pip (python software package), docker (python client)
- download docker container called sebp/elk
- run > sysctl -w vm.max_map_count=262144 to configure elk servers to use more memory to improve performance of the elk container running inside
- configure container for port mappings

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](images/project1-2.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: DVWA-VM1 (10.0.0.5), DVWA-VM2 (10.0.0.6)
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines: filebeat & metric beat
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine: filebeat
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