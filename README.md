# cloud-init
Cloud VM deployment palybooks

[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/k8s-community/cluster-deploy/issues)

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

List of groups with VM instance names and machine types
Instance groups let you organize VM instances or use them
in a load-balancing backend service
Nodes contain comma separated list of instance names.
Names must start with a lowercase letter followed by up to 63 lowercase letters,
numbers, or hyphens, and cannot end with a hyphen
```yaml
cloud_providers:
- name: gce
  zone: europe-west1-b
  type: n1-standard-1
  image: centos-7
  nodes:
  - node-101
  - node-102
- name: aws
  zone: eu-west-1a
  type: t2.medium
  image: centos-7
  nodes:
  - node-201
  - node-202
```

## Users and services credentials

TODO


## Contributors

All the contributors are welcome. If you would like to be the contributor please accept some rules:
- The pull requests will be accepted only in `develop` branch
- All modifications or additions should be tested

Thank you for your understanding!

## License

[MIT Public License](https://github.com/openprovider/cloud-init/blob/master/LICENSE)

## Author Information

[Openprovider Authors](https://github.com/openprovider)

