## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [elk-setup.yml](Files/elk-setup.yml) file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.
- Load Balancers protect against potential DDoS attacks.
- Jump boxes segment networks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the virtual network and system logs.
- Filebeat records log data that it later forwards and centralizes in kibana.
- Metricbeat records the metrics and statistics of the machine that it is deployed on, forwarding this information to Kibana.

The configuration details of each machine may be found below.

| Name                 | Function | IP Address | Operating System |
|----------------------|----------|------------|------------------|
| Jump Box Provisioner | Gateway  | 10.0.0.3   | Linux            |
| Web-2                | DVWA     | 10.1.0.5   | Linux            |
| Web-3                | DVWA     | 10.1.0.6   | Linux            |
| Web-4                | DVWA     | 10.1.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 108.207.94.236

Machines within the network can only be accessed by the Jump Box.
- 10.0.0.3

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 108.207.94.236       |
| Web-2    | No                  | 10.0.0.3             |
| Web-3    | No                  | 10.0.0.3             |
| Web-4    | No                  | 10.0.0.3             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automation of the Ansible configurations allows for future repeated setups that are all exactly the same. Any errors can be modified and immediately patched to all machines utilizing these configurations.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install and update Docker
- Install python 3
- Install the Docker Module
- Increase and use more virtual memory
- Download and launch an ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps output](Images/elk_running-screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-2 | 10.1.0.5
- Web-3 | 10.1.0.6
- Web-4 | 10.1.0.8

We have installed the following Beats on these machines:
- These machines contain:
  - Filebeat 
  - Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files from the machine, which allows the user to parse through different system logs.
- Metricbeat records statistics and metrics such as CPU usage, memory usage, and diskspace.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/roles.
- Update the filebeat-config.yml file to include ELK server IP address
- Run the playbook, and navigate to 108.207.94.236:5601 to check that the installation worked as expected.
![filebeat module](Images/module status.png)

- For metricbeat setup, complete these tasks with their respective metricbeat configuration and playbook files.

