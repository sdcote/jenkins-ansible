# Ansible Role: AWX (open source Ansible Tower)


Installs and configures [AWX](https://github.com/ansible/awx), the open source version of [Ansible Tower](https://www.ansible.com/tower).

## Requirements

Before this role runs, assuming you want the role to completely set up AWX using it's included installer, you need to make sure the following AWX dependencies are installed:

| Dependency                    | Suggested Role           |
| ----------------------------- | ------------------------ |
| Git                           | `git`        |
| Ansible                       | `ansible`    |
| Docker                        | `docker`     |
| Python Pip                    | `pip`        |
| Node.js (6.x)                 | `nodejs`     |


## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    awx_repo: https://github.com/ansible/awx.git
    awx_repo_dir: "~/awx"
    awx_version: devel
    awx_keep_updated: true

Variables to control what version of AWX is checked out and installed.

    awx_run_install_playbook: true

By default, this role will run the installation playbook included with AWX (which builds a set of containers and runs them). You can disable the playbook run by setting this variable to `no`.

## Dependencies

None.

## Example Playbook

    - hosts: awx-centos
      become: true
    
      vars:
        nodejs_version: "6.x"
        pip_install_packages:
          - name: docker-py
    
      roles:
        - repo-epel
        - git
        - ansible
        - docker
        - pip
        - nodejs
        - awx

After AWX is installed, you can log in with the default username `admin` and password `password`.

