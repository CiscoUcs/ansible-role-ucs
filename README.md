Ansible Role: ucs
=========

An Ansible role to perform configuration on Cisco UCS Manager.  LAN, SAN, Storage, Servers, and other configuration can be performed from this role.

Requirements
------------

This role requires UCS modules from Ansible v2.5.
UCS Ansible modules require the ucsmsdk Python module.

Installation
------------

There are two ways you can test this role:

 1. Install it by cloning the Github repository (ensure CiscoUcs.ucs is is your ANSIBLE_ROLES_PATH)

        git clone https://github.com/ciscoucs/ansible-role-ucs CiscoUcs.ucs

 2. Install it using the ansible-galaxy command

        ansible-galaxy install CiscoUcs.ucs

Role Variables
--------------

Variables in defaults/main.yml for each role (e.g., lan/vlans/defaults.main.yml) are based on the FlexPod Datacenter with Docker Cisco Validated Design (CVD).
The Docker EE CVD is available at https://www.cisco.com/c/en/us/td/docs/unified_computing/ucs/UCS_CVDs/flexpod_docker_deploy_design.html.
Your own role variables can be specified in playbooks, group_vars, or other variable locations used by Ansible.  See the examples for additional information.
Example Playbook
----------------

tests/test.yml is an example of how to use the role:

```yaml
---
- hosts: ucs
  connection: local
  gather_facts: no
  tasks:
  - include_role:
      name: CiscoUcs.ucs
```

If you want to run only a portion of the configuration, you can include a role from a specific subdirectory.  You can also change variables used by the role.

```
---
- hosts: ucs
  connection: local
  gather_facts: no
  tasks:
  - include_role:
      name: CiscoUcs.ucs/lan/vlans
    vars:
      ucs_vlans:
      - name: Native-VLAN
        id: '2'
        native: 'yes'
```

Run the test.yml playbook with the following command:

    ansible-playbook [-i <inventory file>] test.yml

License
-------

Apache 2.0

Author Information
------------------

David Soper (@dsoper2), CiscoUcs (@CiscoUcs)
