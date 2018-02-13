Ansible Role: Setup firewall
============================

This role setup firewall rules.

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/openprovider/cloud-setup/issues)

Requirements
------------

No special requirements.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

List of firewall zones that contain allowed/denied ports and services.
```yaml
firewall_zones: []
```

Example Playbook
----------------

    - hosts: all:!localhost
      remote_user: devops
      become: true

      roles:
        - role: firewall
          firewall_zones:
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

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
