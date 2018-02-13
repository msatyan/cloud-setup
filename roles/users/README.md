Ansible Role: Setup users
=========================

This role setup users access and environment.

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/k8s-community/cluster-deploy/issues)

Requirements
------------

No special requirements.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):


List of users who can able to connect via ssh. The users must be able to use sudo without asking
for password for some utils e.g. (tcpdump, docker)
```yaml
users_data: {}
```

Example Playbook
----------------

    - hosts: all:!localhost
      remote_user: initcloud
      become: true

      roles:
        - role: users
          users_data:
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

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
