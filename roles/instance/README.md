Ansible Role: Instance
======================

This role install VM instance on Cloudstack/Google/Amazone.

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/k8s-community/cluster-deploy/issues)

Requirements
------------

This role require the apache-libcloud and cloudstack modules which you can install from pip:

```sh
pip install apache-libcloud
pip install cs
```

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

Path to the Inventory hosts file
It should be auto generated during the creating of VM inctances
```yaml
cloud_inventory_file: '{{ inventory_dir }}/hosts'
```

It will be used as DNS discovering.
```yaml
instance_domain: cluster-dev.net
```

Default instance provider (Google Compute Engine)
```yaml
instance_provider: gce
```

A list of instance node names.
Names must start with a lowercase letter followed by up to 63 lowercase letters,
numbers, or hyphens, and cannot end with a hyphen
```yaml
instance_nodes:
  - node-001
  - node-002
```

A zone is an isolated location within a region.
Resources that live in a zone, such as instances,
are referred to as zonal resources
```yaml
instances_zone: europe-west1-b
```

Predefined machine type which managed by Cloudstack:
```yaml
instance_type: n1-standard-1
```

Each instance requires a disk to boot from.
Specify an image when you create an instance.
```yaml
instance_image: centos-7
```

Cloud specific defaults
-----------------------

User data or metadata that specified additional cloud configuration
```yaml
instance_metadata: {}
```

Cloudstack specific defaults
----------------------------

Cloudstack account
```yaml
cloudstack_account: cloudstack
```

Cloudstack hypervisor type
```yaml
cloudstack_hypervisor: KVM
```


Example Playbook
----------------

	- hosts: localhost
	  connection: local
      roles:
        - instance

License
-------

MIT

Author Information
------------------

[Openprovider](https://github.com/openprovider) Authors
