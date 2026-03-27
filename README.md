📦 Ansible Playbook Configurations

A collection of Ansible playbooks for automating common Linux system administration tasks including repository configuration,
package management, and service enablement.

📁 Playbooks

yum.yml - configures YUM repositories on target hosts. Use this playbook to define and manage the package repositories 
available to your systems.

packages.yml - installs a list of required packages and upgrades all system packages to their latest versions. 
Ensures target hosts have the necessary software and are fully up to date.

services.yml - starts and enables system services on target hosts. Ensures critical services are running and set to
automatically start on boot.

▶️ How to Run the Playbooks
Make sure you have a valid Ansible inventory file configured before running any playbook. (/home/user/proj-directory/inventory)
Run a specific playbook: For escalated privileges assign "become: true" at the beginning of your play

- ansible-playbook yum.yml
- ansible-playbook packages.yml
- ansible-playbook services.yml


✅ Requirements & Prerequisites

- Assign managed hosts alias' in /etc/hosts on your local machine
- Ansible 2.9 or higher
- Python 3.6 or higher on the control node
- Target OS: RHEL / CentOS (YUM-based systems)
- A configured inventory file pointing to your target hosts
- SSH key-based authentication set up between the control node and managed hosts
- Sudo/root privileges on target hosts (-b)


🗂️ Repository Structure
playbook-configurations/
├── yum.yml
├── packages.yml
├── services.yml
└── README.md

👤 Author
ajiggody
GitHub: https://github.com/ajiggody
