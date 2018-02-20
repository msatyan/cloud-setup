Ansible Role: Chrony date/time synchronization
==============================================

This role setup date/time synchronization.

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/openprovider/cloud-setup/issues)

Requirements
------------

No special requirements.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):


List of NTP servers which can be used as a time source.
```yaml
chrony_ntp_servers: []
```

Example Playbook
----------------

    - hosts: all:!localhost
      remote_user: devops
      become: true

      roles:
        - chrony

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
