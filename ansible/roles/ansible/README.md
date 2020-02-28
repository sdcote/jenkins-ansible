# Ansible Role: Ansible

An Ansible Role that installs Ansible on Linux servers.

## Requirements

If using on a RedHat/CentOS-based host, make sure you've added the EPEL repository.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    ansible_install_method: package

Whether to install Ansible via the system `package` manager (`apt`, `yum`, `dnf`, etc.), or via `pip`. If set to `pip`, you need to make sure Pip is installed prior to running this role. You can use the `pip` module to install Pip easily.

    ansible_install_version_pip: ''

If `ansible_install_method` is set to `pip`, the specific Ansible version to be installed via Pip. If not set, the latest version of Ansible will be installed.

## Dependencies

None.

## Example Playbook

Install from the system package manager:

    - hosts: servers
      roles:
        - role: ansible

Install from pip:

    - hosts: servers
      vars:
        ansible_install_method: pip
        ansible_install_version_pip: "2.7.0"
      roles:
        - role: pip
        - role: ansible

