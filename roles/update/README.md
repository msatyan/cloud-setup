Ansible Role: Update OS
=======================

This role update VM instance on Cloudstack/Google/Amazone.

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
        - update

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
