Ansible Role: SSH Permissions
=============================

This role setup allowed ssh users for specified hosts.

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/k8s-community/cluster-deploy/issues)

Requirements
------------

No special requirements.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

Add ssh access for specified users and allowed hosts
```yaml
addmission_group: {}
```

Example Playbook
----------------

	- hosts: all:!localhost
	  remote_user: initcloud
	  become: true

      roles:
        - role: permissions
	      addmission_group:
	        - name: devops
	          ips:
	            - 1.1.1.1
	            - 2.2.2.2
	        - name: dev
	          ips:
	            - 3.3.3.3

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
