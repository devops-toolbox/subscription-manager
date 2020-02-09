Role Name
=========

subscription-manager: Subscription-manager

[![Build Status](https://travis-ci.org/cmihai-ansible/subscription-manager.svg?branch=master)](https://travis-ci.org/cmihai-ansible/subscription-manager)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.subscription-manager](https://galaxy.ansible.com/devopstoolbox.subscription-manager)

```bash
ansible-galaxy install devopstoolbox.subscription-manager
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
subscription-manager_packages_state: present
subscription-manager_remove_packages: true
subscription-manager_enable_service: true
subscription-manager_enable_selinux: true
subscription-manager_copy_templates: true
subscription-manager_firewall_configure: true
subscription-manager_firewall_rules:
  - service: ssh
  - port: 3389
subscription-manager_users:
  - user: devops
    group: docker
subscription-manager_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install subscription-manager on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: subscription-manager is configured
      import_role:
        name: devopstoolbox.subscription-manager
      vars:
        subscription-manager_packages_state: present
        subscription-manager_remove_packages: true
        subscription-manager_enable_service: true
        subscription-manager_enable_selinux: true
        subscription-manager_copy_templates: true
        subscription-manager_firewall_configure: true
        subscription-manager_firewall_rules:
          - service: ssh
          - port: 3389
        subscription-manager_users:
          - user: devops
            group: docker
        subscription-manager_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: subscription-manager
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
