# Miniconda role for Ansible

An Ansible role for deploying and managing miniconda.

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

### Requirements

* Vagrant
* VirtualBox

### vagrant up

This will run the playbook as the **vagrant** user in a virtual machine.

```shell
cd roles/minicond
vagrant up
```

## Contributors
- Christopher Steel ([github.com/cjsteel]( https://github.com/cjsteel )

## Credits and resources
Inspiration:

- ​
- [https://github.com/robinandeer/ansible-miniconda.git][robinandeer/ansible-miniconda]

