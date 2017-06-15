This is a playbook for Plesk Single and Multi Server deployment
---------------------------------------------------------------

The playbooks allows to deploy plesk in cases:
 - you already have some server and need to deploy Plesk
 - you want to create VM in DigitalOcean with Plesk pre-installed
 - you want to create VM in Amazon EC2 with Plesk based on Marketplace offer
 - you want to create bare Amazon EC2 VM based on some AMI and auto-deploy Plesk there
 - (TODO) you want to create VM in Azure with Plesk based on Marketplace offer
 - (TODO) you want to create bare Azure VM based on some AMI and auto-deploy Plesk there
 

You can run ansible in two ways.

The first one directly via CLI. In such case you need to habe ansible installed on your machine:

Sample: ansible-playbook -i hosts plesk-amazon-ec2-from-ami.yml

The second way is to use Ansible shipped via Docker container. This way is preferred if you already use Docker and don't want to install one more piece of software to your machine, becase ansible is usually installed via pip, it also can require some additional libs, etc etc etc.

To use this approach you can just have Docker installed and you need to run as follows:

./ansible-playbook-viadocker -i hosts plesk-amazon-ec2-from-ami.yml

That's it.

Few words about inventory. It has two parts:
- main part "group_vars/all.yml" - contains all definitions of settings for all clouds and plesk general
- credentials "group_vars/credentials.yml" - contains a definition of credentials to your cloud accounts

Note: credentials inventory file is not included to a git repo and is added to .gitignore file
