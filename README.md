This is a set of ansible playbooks for various Plesk deployment
===============================================================

Overview
--------
The playbooks allow to deploy Plesk in cases:
  - you already have some server and need to deploy Plesk
  - you want to create VM in DigitalOcean with Plesk pre-installed
  - you want to create VM in Amazon EC2 with Plesk based on Marketplace offer
  - you want to create bare Amazon EC2 VM based on some AMI and auto-deploy Plesk there
  -  (TODO) you want to create VM in Azure with Plesk based on Marketplace offer
  - (TODO) you want to create bare Azure VM based on some AMI and auto-deploy Plesk there
 

You can run ansible in two ways.

The first one directly via CLI. In such case you need to have ansible installed on your machine:

Sample: `ansible-playbook -i hosts plesk-amazon-ec2-from-ami.yml`

The second way is to use Ansible shipped via Docker container. This way is preferred if you already use Docker and don't want to install one more piece of software to your machine because ansible is usually installed via pip, it also can require some additional libs, etc etc etc.

To use this approach, you can just have Docker installed, and you need to run as follows: `./ansible-playbook-viadocker -i hosts plesk-amazon-ec2-from-ami.yml`

That's it.

Inventory files
---------------
Few words about inventory. It has two parts:
 - a main part "group_vars/all.yml" - contains all definitions of settings for all clouds and Plesk general
 - credentials "group_vars/credentials.yml" - contains a definition of credentials to your cloud accounts

Note: Credentials inventory file is not included in a git repo and is added to .gitignore file


FAQ
===
Amazon EC2 asks for authorization while provisioning of VM
----------------------------------------------------------
When you attempt to create VM from AMI published in Marketplace, you can see a message similar to the sample below. All you need to do - just copy the provided link and navigate it in your browser with an active session to your Amazon AWS account. This is required to authorize the script for deployment on behalf of your AWS account from CLI.

TASK [amazon-ec2 : Create EC2 Instance]
***************************************
fatal: [localhost]: FAILED! => {"changed": false, "failed": true, "msg": "Instance creation failed => OptInRequired: In order to use this AWS Marketplace product you need to accept terms and subscribe. To do so please visit http://aws.amazon.com/marketplace/pp?sku=dw81irkz67efb1tr712312313uet"}
