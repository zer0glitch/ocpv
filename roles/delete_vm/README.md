Role Name
=========

This role will delete a virtual machine

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
# the name of the vm to delete
- name: "myawesomeserver"

# The namespace you are operating on
- namespace: user1

```

Dependencies
------------

- kubernetes.core

Example Playbook
----------------

```
---
- hosts: localhost
  tasks:

  - name: expose ports
    include_role:
      name: zer0glitch.ocpv.deletevm
    vars:
      name: "myawesomeserver"
      namespace: user1
```

License
-------

GPLv3

Author Information
------------------

Jamie Whetsell
jamie@zeroglitch.com
