## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![https://drive.google.com/file/d/1SI6ueuh6J1M40yEGrOJx_PATwl25TeYt/view?usp=sharing](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ the file is on the other folder that are submitted.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly ___balanced__, in addition to restricting _malicious traffic____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
The Load balancers  protect against a distributed denial-of-service (DDoS) attaks.
The jump box allowed to managed devices in separate security zone. It serves as a liason to provide access between them.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network_____ and system _health____.
- _TODO: What does Filebeat watch for? Monitored the logs file or location,collects log events, and forwards them for indexing.
- _TODO: What does Metricbeat record?_ Metricbeat record system metrics file.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | Gateway  | 10.0.0.5   | Linux            |    
| Web-2    | Gateway  | 10.0.0.8   | Linux            |
| Web-3    | Gateway  | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box_____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: Private IP
- _TODO: Private IP

Machines within the network can only be accessed by _SSH________.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
 The Jump Box and the IP is 52.152.174.169
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |            
| Web-1    | No                  | 10.0.0.5             |    
| Web-2    | No                  | 10.0.0.8             | 
| Web-3    | No                  | 10.0.0.7             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_It s simple to learn,puthon language, and No dependency on agents.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... First, using apt to install docker.io
      Second, install pip3 to get  python
	  Use pip to install docker
- Set systemctl module to set up memory
     Download image sebp/elk:761 and launch docker elk container
	 Set up all the ports:- 5601:5601
          - 9200:9200
          - 5044:5044

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: ](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_10.0.0.5, 10.0.0.8, 10.0.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ filebeat system

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
      Filebeat collects container logs, log files,or log events Which we used to monitor system health.
	  Heatbeat collects Uptime information whichwe used to track machine running time.
### Using the Playbook
In order to use the playbook, you will need to have an
 Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the source: /etc/ansible/files/filebeat-config.yml_____ file to _DVWA VMs
- Update the configuration_____ file to include...servers
- Run the playbook, and navigate to _kibana___ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_filebeat-playbook.yml.copy from the source:  /etc/ansible/files/filebeat-config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
 We update the filebeat-config.yml
 We specify the machines by adding the webservers lists in the host files.
  
  
- _Which URL do you navigate to in order to check that the ELK server is running? 
  http://[my ip]:5601/app/kibana

_As a                                                                                      **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook filebeat-playbook.yml.
