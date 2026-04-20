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

- httpd_setup.yml - simple playbook using task handlers to start httpd as a service

- create_users_loop.yml - creates users in a list with a basic loop

- create_advanced_users.yml - uses a loop with a list of dictionaries to create users with multiple
attributes. Each dictionary entry includes name, shell, and comment. 

- conditional_hostname.yml - creates the file /etc/special.txt, but only if the host is a
member of the test group

- check_memory.yml - playbook with a task that uses the debug module to display the system's total memory,
but only if the host has more than 1000MB of RAM.

- set_motd.yml - created a Jinja2 template file motd.j2 with an if/else condition, then created a playbook that uses the template module to deploy your [motd.j2] file to /etc/motd on all hosts

- generate_report.yml - Created a Jinja2 template file at system_report.j2 that included the following information
for each host (e.g, hostname, IP address, total memory (MB)), then used template module to deploy the report to
/tmp/system_report.txt on all host

- conditional_httpd_restart.yml - This playbook that combines what I've learned about handlers, templates, and
conditionals & applies it by installing the httpd package on all hosts, using the template module to deploy an Apache config file (apache.conf.j2) to /etc/httpd/conf.d/custom.conf, then restarting the httpd service when notified. The template included The host's ServerName & listens on port 80

▶️ How to Run the Playbooks

Make sure you have a valid Ansible inventory file configured before running any playbook: (/home/user/proj-directory/inventory)

Run a specific playbook: (For escalated privileges assign "become: true" at the beginning of your play)

- ansible-playbook yum.yml
- ansible-playbook packages.yml
- ansible-playbook services.yml
- ansible-playbook host_info.yml
- ansible-playbook variables.yml
- ansible-playbook secret_user.yml --ask-vault-pass
- httpd_setup.yml
- create_users_loop.yml 
- create_advanced_users.yml 
- conditional_hostname.yml 
- check_memory.yml
- set_motd.yml
- generate_report.yml 
- conditional_httpd_restart.yml



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
├── create_users_loop.yml
├── create_advanced_users.yml
├── conditional_hostname.yml
├── check_memory.yml
├── set_motd.yml
├── generate_report.yml
├── conditional_httpd_restart.yml
└── README.md
