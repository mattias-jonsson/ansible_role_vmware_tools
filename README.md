Ansible Role: ansible_role_vmware_tools
=========

Installs/upgrades/configures VMware Tools on the following Operating Systems:

<ul>
<li> Windows Server 2012
<li> Windows Server 2016
<li> Windows Server 2019
<li> Windows Server 2022
</ul>

Requirements
------------

This role is dependent on the following Ansible collections:

`ansible.windows`, `community.windows`

Role Variables
--------------

Available variables are listed below, along with default values where applicable (see `defaults/main.yml`):


Role Variables
--------------


| Variable | Required | Default | Comments |
| -------- | -------- | ------- | -------- |
| `ansible_role_vmware_tools_remove_features` | No | [] | A list of features to remove at installation, Please se VMware Tools documentation for list of features. |
| `ansible_role_vmware_tools_sha256sums` | No | `defaults/main.yml` contains a list covering some versions  | A list of sha256 checksums for VMware Tools ISO files, format is version-build: sha256sum. Please verify and update this as needed. |
| `ansible_role_vmware_tools_time_sync` | No | true | Enable timesyncronization through VMware Tools. |
| `ansible_role_vmware_tools_url` | No | `https://packages.vmware.com/tools/releases/{{ ansible_role_vmware_tools_version }}/windows/` | Download URL for VMware Tools ISO files, change this if needed by your environment. |
| `ansible_role_vmware_tools_version` | Yes | 12.1.5 | Version of VMware Tools to install. |


Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

    - hosts: servers

      vars:
        ansible_role_vmware_tools_remove_features: 
          - AppDefense
        ansible_role_vmware_tools_time_sync: true

      roles:
         - ansible_role_vmware_tools

License
-------

MIT

Author Information
------------------

Mattias Jonsson
