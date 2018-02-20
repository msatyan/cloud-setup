# cloud-setup
Cloud VM setup palybooks

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/openprovider/cloud-setup/issues)

## Requirements

All playbooks require the apache-libcloud module which you can install from pip:

```sh
pip install apache-libcloud
```

Also you can install `Ansible` from pip if it does not installed
```sh
pip install ansible
```

## Playbooks usage

Before using of the playbooks you should change/enter all required vars in `default/group_vars/all.yml`

Prepare cloud components. This is optional action related to infrastructure.
```sh
ansible-playbook playbooks/prepare-cloud.yml
```

## Playbooks credentials

TODO

## Playbooks initial variables

Available variables are listed below, along with default values (see `default/group_vars/all.yml`):

Path to the Inventory hosts file
It should be auto generated during the creating of VM inctances
```yaml
cloud_inventory_file: '{{ inventory_dir }}/hosts'
```

List of groups with VM instance names and machine types
Instance groups let you organize VM instances or use them
in a load-balancing backend service
Nodes contain comma separated list of instance names.
Names must start with a lowercase letter followed by up to 63 lowercase letters,
numbers, or hyphens, and cannot end with a hyphen

Example of setup cloud providers:
```yaml
cloud_providers:
  - name: gce
    zone: europe-west1-b
    type: n1-standard-1
    image: centos-7
    metadata:
      ssh_key: keydata
      timezone: Europe/Amsterdam
    nodes:
      - node-101.cluster-dev.net
      - node-102.cluster-stage.net
  - name: aws
    zone: eu-west-1a
    type: t2.medium
    image: centos-7
    metadata:
      ssh_key: keydata
      timezone: Europe/Amsterdam
    nodes:
      - node-201.cluster-dev.net
      - node-202.cluster-stage.net
```

Account name of user who initialize VM. Ansible will use this user account to ssh into
the managed machines. The user must be able to use sudo without asking for password

Example of define an admin user
```yaml
cloud_ops_superuser: devops
```

List of users who can able to manage system and develop software.
The users must be able to use sudo without asking for password for some utils e.g. (tcpdump, docker)

Example of setup operations an dev users:
```yaml
cloud_ops_users:
  - name: devops
    admin: true
    bashrc:
      - alias la='ls -la'
      - alias l='ls -rtFla'
  - name: dev
    home: /var/www
    bashrc:
      - alias la='ls -la'
    sudoers:
      - /usr/bin/docker
      - /usr/bin/ls
      - /usr/bin/cat
      - /usr/bin/grep
  - name: ops
    bashrc:
      - alias la='ls -la'
    sudoers:
      - /usr/bin/docker
      - /usr/bin/ls
      - /usr/bin/cat
      - /usr/bin/grep
      - /usr/bin/tcpdump
  - name: zabbix
    homeless: true
    create: false
    sudoers:
      - "/usr/sbin/iptables -nL"
      - "/usr/sbin/conntrack -L"
```

List of IPs which allowed to connect via ssh.

Example of define allowed IPs:
```yaml
cloud_ops_allowed_ips:
  - 1.1.1.1
  - 2.2.2.2
```

List of zones that contain allowed/denied ports and services.

Example of setup services access:
```yaml
cloud_services_access:
  - zone: ops
    allow: true
    ports:
      - 2222/tcp
    services:
      - http
      - https
      - ssh
    sources:
      - 1.1.1.1
      - 2.2.2.2
  - zone: public
    allow: false
    services:
      - http
      - https
      - ssh
```

List of NTP servers which can be used as a time source.
```yaml
cloud_ntp_servers: []
```

## Users and services credentials

TODO


## Contributors

All the contributors are welcome. If you would like to be the contributor please accept some rules:
- The pull requests will be accepted only in `develop` branch
- All modifications or additions should be tested

Thank you for your understanding!

## License

[MIT Public License](https://github.com/openprovider/cloud-setup/blob/master/LICENSE)

## Author Information

[Openprovider Authors](https://github.com/openprovider)

