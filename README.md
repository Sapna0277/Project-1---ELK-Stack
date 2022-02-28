## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/Sapna0277/Project-1---ELK-Stack/blob/main/Diagrams/azure%20network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the etc/ansible/install-elk-playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file: etc/ansible/install-elk-playbook

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? They protect systems from DDOS attacks. What is the advantage of a jump box? To give the user access from a single node that can be secured and monitored and is the origination point for launching tasks. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- _TODO: What does Filebeat watch for? Information in any file system that has been changed
- _TODO: What does Metricbeat record? Takes the metric and statistic information that it collects and transport it to the specified output.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Elk      | Gateway  |40.78.4.255 | Linux            |
| Web 1    | LBalancer| FTE-IP     | Linux            |
| Web 3    | LBalancer| FTE-IP     | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses? 73.136.252.160

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? Jumpbox VM  What was its IP address? 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                    | 10.0.0.4           |
| Web 1    | No                    | 10.0.0.5           |
| Web 2    | No                    | 10.0.0.6           |
| Web 3    | No                    | 10.0.0.7           |
| Elk VM   | No                    | 10.1.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? It allows you to deploy to multiple servers using a single playbook.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... Install docker.io
- ... Install Python-pip
- ... Install docker container
- ... Launch docker container: elk
- ... Command: sysctl -w


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)
![Docker PS.JPEG](https://github.com/Sapna0277/Project-1---ELK-Stack/blob/a9a10281f6e852b85e9757204710cfc3f5fa526a/Docker%20PS.JPG)

azadmin@Elk-VM:~$ sudo docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED      STATUS        PORTS                                                                              NAMES
4c38ca3c9825   sebp/elk:761   "/usr/local/bin/star…"   7 days ago   Up 29 hours   0.0.0.0:5044->5044/tcp, 0.0.0.0:5601->5601/tcp, 0.0.0.0:9200->9200/tcp, 9300/tcp   elk
azadmin@Elk-VM:~$



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
- Web 1 (10.0.0.5)
- Web 2 (10.0.0.6)
- Web 3 (10.0.0.7)

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed: Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
- Filebeat monitors the log files or locations that you specify, collects log events and forwards them to Elasticsearch or Logstash for indexing
- Metricbeat collects metrics and stastics that it collects and ships them to the specified ouput.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to etc/ansible.
- Update the config file to include the VM webservers and ELK
- Run the playbook, and navigate to ELK  VM to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? /etc/ansible/file/filebeat   Where do you copy it? config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? etc/ansible/hosts file   How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.

ssh azadmin@(private IP address)
sudo docker (name) 
sudo docker attach (name)
cd /etc/ansible/roles
ls
nano (name of file) ansible-playbook.yml


