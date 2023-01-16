Role Name
=========

This role will install Openshift Virtualization.  The OCP-v and Hyperconverged operators will be installed.

Requirements
------------

- ansible==2.10
- python module openshift
- python module jsonpath
- python module kubernetes==12.0.0
- The system you are running this from has a valid kubeconfig



Role Variables
--------------

```
- none
```

Dependencies
------------

- kubernetes.core

Example Playbook
----------------

```
---
- name: Install openshift virtualization
  hosts: localhost
  tasks:

  - name: import deploy_cnv
    import_role:
            name: zer0glitch.ocpv.install
```

License
-------

GPLv3

Author Information
------------------

Jamie Whetsell
jamie@zeroglitch.com
