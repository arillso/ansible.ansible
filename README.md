# Ansible Role: ansible

[![Build Status](https://img.shields.io/travis/arillso/ansible.ansible.svg?branch=master&style=popout-square)](https://travis-ci.org/arillso/ansible.ansible) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=popout-square)](https://sbaerlo.ch/licence) [![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-ansible-blue.svg?style=popout-square)](https://galaxy.ansible.com/arillso/ansible) [![Ansible Role](https://img.shields.io/ansible/role/d/id.svg?style=popout-square)](https://galaxy.ansible.com/arillso/ansible)

## Description

Configure a task schedule that periodically runs ConfigureRemotingForAnsible.ps1 script.

## Installation

```bash
ansible-galaxy install arillso.ansible
```

## Requirements

None

## Role Variables

### ansible_ressource_name

Name of the folder where the data will be stored.

```yml
ansible_ressource_name: "{{ source_of_supply_name | default('Support') }}"
ansible_root_directory: "{{ ansible_env.SystemDrive }}\\{{ ansible_ressource_name }}"
```

### ansible_directory

Whole path where the file should be stored

```yml
ansible_directory: "{{ ansible_root_directory }}\\ansible"
```

## ansible_configure_remoting

Path where the Powershell script is stored.

```yml
ansible_configure_remoting: "{{ ansible_directory }}\\ConfigureRemotingForAnsible.ps1"
```

### ansible_scheduled_task

```yml
ansible_scheduled_task: '-ExecutionPolicy Bypass -File "{{ ansible_configure_remoting }}" -CertValidityDays 3650 -ForceNewSSLCert -EnableCredSSP'
```

## Example Playbook

```yml
- hosts: all
  roles:
    - arillso.ansible
```

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## License

This project is under the MIT License. See the [LICENSE](licence) file for the full license text.

## Copyright

(c) 2020, Arillso
