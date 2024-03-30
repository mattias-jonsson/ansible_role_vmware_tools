Ansible Role: vmware_tools
=========

This Ansible role installs, upgrades, and configures VMware Tools on Windows Server 2016, 2019, 2022, Windows 10 and Windows 11.

Requirements
------------

This role is dependent on the following Ansible collections. If not already installed, you can install it using the following command:

```shell
ansible-galaxy collection install ansible.windows community.windows
```

Role Variables
--------------

Available variables are listed below, along with default values where applicable (see `defaults/main.yml`):


Role Variables
--------------


| Variable | Required | Default | Comments |
| -------- | -------- | ------- | -------- |
| `vmware_tools_remove_features` | No | `[]` | 	A list of VMware Tools features to remove during installation. Check VMware Tools documentation for a comprehensive list of removable features. |
| `vmware_tools_sha256sums` | No | `See defaults/main.yml`	 | A list of SHA256 checksums for verifying the integrity of VMware Tools ISO files. Format: version-build: sha256sum. |
| `vmware_tools_time_sync` | No | `true` | Enables or disables time synchronization between the VMware guest and host. Setting to false disables synchronization. |
| `vmware_tools_url` | No | `https://packages.vmware.com/tools/releases/{{ vmware_tools_version }}/windows/` | The URL from which VMware Tools ISO files are downloaded. This URL should follow the same structural format as the official VMware download site to ensure compatibility. |
| `vmware_tools_version` | No | `Latest version based on vmware_tools_sha256sums` | Specifies the version of VMware Tools to install. Ensure vmware_tools_sha256sums includes the checksum for the version you intend to install. |


Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

```shell
- hosts: servers

  vars:
    vmware_tools_time_sync: true
    vmware_tools_version: '12.4.0'

  roles:
      - vmware_tools
```

License
-------

MIT

Author Information
------------------

Mattias Jonsson
