Ansible Role: Setup logrotate
============================

This role setup logrotate.

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/openprovider/cloud-setup/issues)

Requirements
------------

No special requirements.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

Example Playbook
----------------

    - hosts: all:!localhost
      remote_user: devops
      become: true

      roles:
        - role: logrotate
          rotate_period_type: weekly
          rotate_period: 1

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
