# Miniconda role for Ansible

An Ansible role for deploying and managing miniconda.

## Description

By default this role installs miniconda to the deploy users home directory and creates one or more conda based Python environements.

## Variables

All role variables start with `miniconda_`.

### roles/miniconda/defaults/main.yml

```shell
---
# file: roles/miniconda/defaults/main.yml

## miniconda states

miniconda_state      : 'present' # 'present', 'absent', 'purged'
miniconda_envs_state : 'present' # 'present', 'absent', 'purged'

## Target miniconda version

miniconda_platform: 'Linux-x86_64'
miniconda_installer_sh: 'Miniconda2-4.3.11-{{ miniconda_platform }}.sh'
miniconda_installer_sh_checksum: d573980fe3b5cdf80485add2466463f5
miniconda_url: >
  'https://repo.continuum.io/miniconda/{{ miniconda_installer_sh }}'

## directories

miniconda_parent_dir  : '{{ ansible_env.HOME }}'
miniconda_home        : '{{ miniconda_parent_dir }}/miniconda'
miniconda_resource_dir: '{{ miniconda_parent_dir }}/sys/sw/miniconda'

## environments

### conda environment(s)

miniconda_add_condarc: yes

miniconda_environments:
  - name: prod
    python_version: 2.7
    pkgs: 'pip'
  - name: stage
    python_version: 3.4
    pkgs: 'pip'
  - name: dev
    python_version: 3.4
    pkgs: 'pip'

### shell environment

miniconda_modify_path: yes
miniconda_rcfile: '~/.bashrc'
```

## ansible-playbook command example

```shell
ansible-playbook -i inventory/dev systems.yml
```

## Role development and testing

### Supplimental software

* conda (via miniconda)
* a conda created Python Ansible environment
* Vagrant
* VirtualBox

### activate (conda) python environment

Example of a command prompt with no active conda environments.

```shell
user01@workstation-001:~$
```
```shell
source activate ansible
```
Example of command prompt with an active conda environment called "ansible"

```shell
(ansible) user01@workstation-001:~$
```

### vagrant up

This will run the playbook as the **vagrant** user in a virtual machine.

```shell
cd roles/minicond
vagrant up
```

### Connect to Vagrant created test VM

Connect and activate a conda test environment called dev
```shell
vagrant ssh
which python
source activate dev
which python
```


## Contributors
- Christopher Steel ([github.com/cjsteel]( https://github.com/cjsteel )

## Credits and resources
Inspiration:

- [robinandeer/ansible-miniconda](https://github.com/robinandeer/ansible-miniconda.git)

