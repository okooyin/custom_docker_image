# custom_docker_image
project explaining the steps to create a Docker image from a running VM using Ansible with roles:

markdown
# Docker Image Creation from a Running VM Using Ansible

This project provides an Ansible playbook and roles to create a Docker image from a running VM. The process involves:
1. SSHing into the VM.
2. Creating a compressed archive (`tar.gz`) of the VM’s filesystem.
3. Transferring the archive to the local machine.
4. Importing the archive as a Docker image on the local machine.

## Directory Structure

Set up the following directory structure for your Ansible project:

```
plaintext
project/
├── inventory/
│   └── hosts.ini
├── playbook.yml
└── roles/
    └── create_docker_image_from_vm/
        ├── tasks/
        │   └── main.yml
        ├── vars/
        │   └── main.yml
        └── files/
```
Step 1: Define the Inventory
In inventory/hosts.ini, define your VM as a host. Replace <public_ip_of_instance> with the actual IP address of your VM:
```
[vm]
<public_ip_of_instance> ansible_user=ubuntu 
```
Step 2: Define the Playbook
Create playbook.yml to run the create_docker_image_from_vm role on your VM.

Step 4: Run the Playbook
Execute the playbook to initiate the process:
```
ansible-playbook -i inventory/hosts.ini playbook.yml
```
After Running the Playbook
After the playbook completes, you’ll have a Docker image named my_custom_image:latest on your local machine. You can verify its existence by running:
```
docker images
```
This completes the creation of a Docker image from a VM using Ansible
