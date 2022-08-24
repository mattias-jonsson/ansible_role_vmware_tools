Ansible Role: ansible_role_vmware_tools
=========

Installs/upgrades/configures VMware Tools on the following Operating Systems:

<ul>
<li> Windows Server 2012
<li> Windows Server 2016
<li> Windows Server 2019
</ul>

Requirements
------------

This role is dependent on the following Ansible collections:

`ansible.windows`, `community.windows`

Role Variables
--------------

Available variables are listed below, along with default values where applicable (see `defaults/main.yml`):


    ansible_role_vmware_tools_installer_file:

Name of installer file as named on https://packages.vmware.com/tools/releases

    ansible_role_vmware_tools_installer_arch:

Architecture, acceptable values are x86 or x64.

    ansible_role_vmware_tools_installer_sha1sum:

Sha1sum of installer file.

    ansible_role_vmware_tools_product_id:

 Product GUID as seen under HKLM:SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

    ansible_role_vmware_tools_remove_features:

List of VMware Tools features to remove when installing.

    ansible_role_vmware_tools_time_sync: true

Boolean, enable or disable the VMware tools built-in timesync feature.


Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------

    - hosts: servers

      vars:
        ansible_role_vmware_tools_installer_file: VMware-tools-11.3.0-18090558-x86_64.exe
        ansible_role_vmware_tools_installer_arch: x64
        ansible_role_vmware_tools_installer_sha1sum: 56ef3c8beb4e3abd2095aade17ccaafc5ac5a132
        ansible_role_vmware_tools_product_id: '{4FE02FF2-2194-4E1D-8B04-F934655966F9}'
        ansible_role_vmware_tools_remove_features: 
        - BootCamp
        - Hgfs
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
