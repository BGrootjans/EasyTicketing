# EasyTicketing

EasyTicketing provides tools and configurations for setting up, backing up, and restoring ticketing systems. This repository includes Ansible playbooks, configuration files, and setup scripts for managing server environments and integrating monitoring tools like Zabbix. The application itself used for handeling tickets is OTOBO (open-source), more info https://otobo.io/.

## Overview
![Alt text](https://github.com/BGrootjans/EasyTicketing/blob/master/Diagram%20Easyticketing.jpg)

---

## Repository Structure

### **Master Branch**
The `master` branch contains the core repository files, including:
- .env # Environment configuration file for docker containers
- README.md # Project documentation
- zabbix_agentd.conf # Configuration file for Zabbix agent

### **Files Branch**
The `files` branch includes additional resources for deployment and management:
- .env # Environment configuration file for docker containers
- ansible.cfg # Ansible configuration file
- hosts # Ansible inventory file
- palybook_restore_server_on_AWS.yml #Playbook to restore a server on AWS
- playbook_backup_server.yml # Playbook to back up a server
- playbook_client_set_up.yml # Playbook to set up a client
- playbook_restore_database_on_EC2.yml # Playbook to restore a database on EC2
- playbook_set_up_server.yml # Playbook to set up a server
- zabbix_agentd.conf # Updated configuration file for Zabbix agent

## Key Features

- **Server Setup**: Includes playbooks for setting up both servers and clients for the EasyTicketing system.
- **Backup & Restore**: Provides tools for backing up servers and restoring environments on AWS EC2.
- **Monitoring Integration**: Configures Zabbix agents to monitor system health and performance.
- **Environment Configuration**: `.env` file for environment-specific variables and settings.
- **Ansible-Driven Automation**: Fully automated infrastructure management using Ansible.

## How to Use

### Prerequisites
Ensure the following are installed on a Ubuntu LTS:
- **Ansible** (for playbook execution)
- **AWS CLI** (for managing AWS resources)
- **Zabbix server** (for monitoring integration)
- **Fix IP** 192.168.2.100

Ensure following services are available:
- **2 mailaccounts** (for seting up application itself)
- **AWS account** (for restore in the cloud)

### Setup and Configuration
1. Clone the repository:
   ```bash
   git clone --single-branch --branch files https://github.com/BGrootjans/EasyTicketing.git
   cd EasyTicketing
2. Replace Ansible config file with `ansible.cfg`
3. Edit the Ansible host file, use `hosts` as example
4. Run the playbook(s)
5. Go through the installer
      see documentation https://doc.otobo.org/

### Running Playbooks
- Set Up a Server:
  ```bash
  ansible-playbook playbook_set_up_server.yml -i hosts
- Backup a Server:
  ```bash
  ansible-playbook playbook_backup_server.yml -i hosts
- Restore a Server on AWS:
  ```bash
  ansible-playbook palybook_restore_server_on_AWS.yml -i hosts
- Restore a Database on EC2:
  ```bash
  ansible-playbook playbook_restore_database_on_EC2.yml -i hosts
- Set Up a Client
  ```bash
  ansible-playbook playbook_client_set_up.yml -i hosts
  
### Monitoring with Zabbix
The repository includes the `zabbix_agentd.conf` file for integrating with Zabbix monitoring. The necessary steps to deploy the Zabbix configuration and start the Zabbix agent service are automated as part of the `playbook_set_up_server.yml` Ansible playbook.

To set up Zabbix monitoring:
1. Run the server setup playbook:
   ```bash
   ansible-playbook playbook_client_set_up.yml -i hosts
2. Verify that the Zabbix agent service is running on the target server:
   ```bash
   ansible-playbook playbook_client_set_up.yml -i hosts

---

## Contribution
We welcome contributions to the EasyTicketing project. Please:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature
3. Submit a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Support
For any questions or issues, please raise an issue in the repository or contact master@easyticketing.net.




