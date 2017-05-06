This is a playbook for Plesk Single and Multi Server deployment
---------------------------------------------------------------

To use this you should deploy Linux servers and add their IPs to hosts file.
One server to [management-node] section, one or more to [service-node] section.
  
Then simply run
	plesk-multi-server-deploy.sh 

or
        ansible-playbook --ssh-common-args "-i qatools_ssh_private.key" -i hosts plesk-multi-server.yml

If you need some other configuration, i.e. just management or service node, or even Plesk single, you should use corresponding .yml file in the command line above.

You can also play with global variables defined in `group_vars/all` file.

Here "password", which will be set up as Plesk admin password and `extore_url` and URLs for Management and Service node extensions.
