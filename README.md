Role Name
=========

ibmcloud: Ibmcloud

[![Build Status](https://travis-ci.org/cmihai-ansible/ibmcloud.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ibmcloud)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.ibmcloud](https://galaxy.ansible.com/devops-toolbox.ibmcloud)

```bash
ansible-galaxy install devops-toolbox.ibmcloud
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ibmcloud_packages_state: present
ibmcloud_remove_packages: true
ibmcloud_enable_service: true
ibmcloud_enable_selinux: true
ibmcloud_copy_templates: true
ibmcloud_firewall_configure: true
ibmcloud_firewall_rules:
  - service: ssh
  - port: 3389
ibmcloud_users:
  - user: devops
    group: docker
ibmcloud_selinux_booleans:
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
- name: Install ibmcloud on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ibmcloud is configured
      import_role:
        name: devops-toolbox.ibmcloud
      vars:
        ibmcloud_packages_state: present
        ibmcloud_remove_packages: true
        ibmcloud_enable_service: true
        ibmcloud_enable_selinux: true
        ibmcloud_copy_templates: true
        ibmcloud_firewall_configure: true
        ibmcloud_firewall_rules:
          - service: ssh
          - port: 3389
        ibmcloud_users:
          - user: devops
            group: docker
        ibmcloud_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ibmcloud
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
