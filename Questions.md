## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

Enter the playbook file(all playbook files are in images)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundent, in addition to restricting traddic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?
  Load balancers add a layer of redundency to a network, this will help with a networks uptime. The advantage of a jump box is that you can manage multiple servers from one place without have to do said changes to each system.
  
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the servers and system logs.
- What does Filebeat watch for?
  Filebeat moniters log files or locations that you specific and sends the output to elasticsearch/logstash
- What does Metricbeat record?
  Metricbeat moniters statistics from servers/operating systems that you specify and forwards the output to either elasticsearch/logstash

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     |  Function  | IP Address               | Operating System |
|----------|------------|--------------------------|------------------|
| Jump Box | Gateway    | 10.0.0.4/13.68.153.123   | Linux            |
| Web1     | Webserver  | 10.0.0.5                 | Linux            |
| Web2     | Webserver  | 10.0.0.6                 | Linux            |
| Web3     | Webserver  | 10.0.0.7                 | Linux            |
| Elk      | Monitering | 10.1.0.4/104.209.179.115 | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
: Add whitelisted IP addresses
208.100.143.158
10.0.0.4 / 13.68.153.123

Machines within the network can only be accessed by the Jumpbox.
- Which machine did you allow to access your ELK VM? What was its IP address?
My local machine, 208.100.143.158

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses        |
|----------|---------------------|-----------------------------|
| Jump Box | Yes/No              | 208.100.143.158/22          |
| Web1     | No                  | 208.100.143.158/22          |
| Web2     | No                  | 208.100.143.158             |    
| Web3     | No                  | 208.100.143.158             |
| ELK      | Yes/No              | 208.100.143.158/5601        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  You can configure multiple machines in a network within the Ansible container

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install pip3
- Install Python docker module
- Increase Virtual memory 
- Use more memory
- Download and launch docker elk container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
  10.0.0.5
  10.0.0.6
  10.0.0.7

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed
  Filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
  Filebeat collects log data, for example systemlogs, they are used to see if anything has changed on our system
  Metricbeat collects metrics from systems and services, for example CPU/RAM usage on a machine/server

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yaml file to ansible container.
- Update the Configuration file to include the IP adresses and Group 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
  http://104.209.179.115:5601/app/kibana

Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._