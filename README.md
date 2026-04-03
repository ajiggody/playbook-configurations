📦 Ansible Playbook Configurations

- A collection of Ansible playbooks for automating common Linux system administration tasks including repository configuration, package management, service enablement, extracting host information, and variable configuration. 

📁 Playbooks

- yum.yml - configures YUM repositories on target hosts. Use this playbook to define and manage the package repositories 
available to your systems.

- packages.yml - installs a list of required packages and upgrades all system packages to their latest versions. 
Ensures target hosts have the necessary software and are fully up to date.

- services.yml - starts and enables system services on target hosts. Ensures critical services are running and set to
automatically start on boot.

- host_info.yml - utilizes [Ansible facts] to extract host information (e.g., IP address, hostname, BIOS version) from each managed node and then redirecting it into a temporary file.

- variables.yml - executes the variables values in my [vars] section of the playbook (e.g., f_name, l_name, age) to my localhost.

- secret_user.yml - creates a user account named jdoe (representing Jane Doe) across all managed nodes, while securely pulling a password from an encrypted vault file. It then displays a secret message stored in that same vault file. 

▶️ How to Run the Playbooks

Make sure you have a valid Ansible inventory file configured before running any playbook: (/home/user/proj-directory/inventory)

Run a specific playbook: (For escalated privileges assign "become: true" at the beginning of your play)

- ansible-playbook yum.yml
- ansible-playbook packages.yml
- ansible-playbook services.yml
- ansible-playbook host_info.yml
- ansible-playbook variables.yml
- ansible-playbook secret_user.yml --ask-vault-pass


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
├── variables.yml
├── secret_user.yml
├── host_info.yml
└── README.md
