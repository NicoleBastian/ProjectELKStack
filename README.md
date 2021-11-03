# ProjectELKStack
ELK STack
## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

 ![image](https://user-images.githubusercontent.com/86977549/139712575-6846e42e-70f9-434f-97e2-7802b5ed6d28.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.
  - elk1.yml
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
-What aspect of security do load balancers protect?
Load balancers defend against DDOS and system overload.
-What is the advantage of a jump box?_ 
A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration and system files.
-What does Filebeat watch for?
Log files or log events
-What does Metricbeat record?
Metrics from running services
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | Webserver| 10.0.0.5   | Linux            |
| Web-2    | Webserver| 10.0.0.6   | Linux            |
|ELK-SERVER| Webserver| 10.1.0.4   | Linux            |
### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.21.5.203
Machines within the network can only be accessed by the JumpBox.
- Which machine did you allow to access your ELK VM? What was its IP address?_
My personal computer at 24.21.5.103
A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
| Web-1/2  | No                  | 24.21.5.103          |
|ELK-SERVER| No                  | 24.21.5.103          |
### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-What is the main advantage of automating configuration with Ansible?
Changes can be made easily and with any of the attached VMs.
The playbook implements the following tasks:
-In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install python3-pip
-Install Docker Python Module
-Download and launch a Docker web container
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 ![image](https://user-images.githubusercontent.com/86977549/139712703-d3d1671b-3206-4833-bcd0-53e1d9da74fd.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.5
-10.0.0.6
We have installed the following Beats on these machines:
-Filebeat
-Metricbeat
These Beats allow us to collect the following information from each machine:
- Filebeat forwards and centralizes log data. This information is forwarded to Elasticsearch/Logstash.
- Metricbeat provides a way to provide information such as metrics from the operating system and from services running on a server. Metricbeat collects this data and sends it to either Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the Roles file to /etc/ansible/Roles.
- Update the hosts file to include the webservers Ips and the ELK-SERVER IP.
- Run the playbook, and navigate to  http://40.83.128.214:5601 to check that the installation worked as expected.
- _Which file is the playbook? Where do you copy it?
/etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ 
Edit the /etc/ansible/hosts file to add webserver/elkserver ip addresses- _Which URL do you navigate to in order to check that the ELK server is running?
http://40.83.128.214:5601
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
-curl https://github.com/benjhaddock/CyberSecurityP1/blob/main/Ansible/elk_install.yml > /etc/ansible/roles/elk_install.yml
- nano hosts
-ansible-playbook elk.yml
-do-release-upgrade


