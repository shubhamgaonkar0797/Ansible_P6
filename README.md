# ContentSphere Infrastructure Automation Using Ansible

## Project Overview

ContentSphere is an Infrastructure Automation project that uses Ansible to configure Linux servers and automate AWS resource provisioning. The project demonstrates configuration management, playbooks, variables, Jinja2 templates, handlers, and AWS automation.

## Objectives

- Automate Linux server configuration using Ansible.
- Install and configure Nginx on a managed EC2 instance.
- Deploy a dynamic web page using Jinja2 templates.
- Use handlers to validate and reload Nginx configuration.
- Automate Amazon EC2 instance provisioning.
- Create an Amazon S3 bucket and upload project files.
- Organize automation tasks into reusable playbooks.

## Technologies Used

| Technology | Purpose |
|---|---|
| Ansible | Configuration management and automation |
| AWS EC2 | Hosts the control and managed nodes |
| Amazon S3 | Stores project files |
| Nginx | Web server |
| Ubuntu Linux | Operating system |
| YAML | Ansible playbook configuration |
| Jinja2 | Dynamic configuration and HTML templates |
| Git and GitHub | Version control and project hosting |

## Project Architecture

```text
Developer
   |
   v
GitHub Repository
   |
   v
Ansible Control Node (Ubuntu EC2)
   |
   | SSH
   v
Managed Node (Ubuntu EC2)
   |
   +--> Install and configure Nginx
   +--> Deploy ContentSphere webpage
   +--> Manage files and permissions

Ansible Control Node
   |
   +--> Provision EC2 instances
   +--> Create S3 bucket
   +--> Upload and verify project files
```

## Project Structure

```text
Ansible/
├── README.md
├── ansible.cfg
├── inventory
├── playbooks/
│   ├── contentsphere.yml
│   ├── contentsphere-task4.yml
│   ├── server-setup.yml
│   └── aws-resources.yml
├── templates/
│   ├── index.html.j2
│   └── contentsphere-nginx.conf.j2
├── files/
│   └── contentsphere.txt
└── vars/
    ├── aws.yml
    └── contentsphere.yml
```

## Implementation

### 1. Configure the Ansible Control Node

Install Ansible on the Ubuntu control node and verify the installation.

```bash
ansible --version
```

### 2. Configure Inventory and SSH Connectivity

Define the managed EC2 instance in the inventory file and test connectivity.

```bash
ansible webserver -m ping
```

### 3. Execute Ad-Hoc Commands

Use Ansible ad-hoc commands to gather system information, manage files, and perform basic administrative tasks.

### 4. Configure the Web Server

Execute the ContentSphere playbook to install Nginx, configure the web root, and deploy the application page.

```bash
ansible-playbook playbooks/contentsphere.yml
```

### 5. Use Variables, Templates, and Handlers

Use YAML variables and Jinja2 templates to generate application and Nginx configuration files. Handlers validate and reload Nginx when required.

```bash
ansible-playbook playbooks/contentsphere-task4.yml
```

### 6. Automate AWS Resources

Run the AWS automation playbook to provision an EC2 instance, create an S3 bucket, upload a project file, and verify its contents.

```bash
ansible-playbook playbooks/aws-resources.yml
```

## Verification

- Verify Ansible connectivity to the managed node.
- Confirm that Nginx is active.
- Open the ContentSphere webpage using the managed instance's public IP address.
- Verify that the EC2 instance is running.
- Confirm that the S3 bucket exists and contains `contentsphere.txt`.

## Security Considerations

- Do not commit AWS access keys, secret keys, passwords, private SSH keys, or other credentials.
- Use IAM roles or appropriately secured AWS credentials.
- Restrict SSH and HTTP access using suitable security group rules.
- Avoid storing sensitive values directly in playbooks or variable files.
- Consider Ansible Vault for encrypting sensitive variables.

## Learning Outcomes

This project demonstrates practical experience with Ansible inventory, ad-hoc commands, YAML playbooks, variables, Jinja2 templates, handlers, Linux configuration management, SSH connectivity, and AWS automation.

## Author

**Shubham Gaonkar**

## Repository

[ContentSphere Ansible Project — GitHub](https://github.com/shubhamgaonkar0797/Ansible_P6)
