Role Name
=========

This role powers on/off a virtual machine

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
# namespace where VM lives
- project: user0

# The name of the virtual machine
- vm_name: fedora-custom

# The running true will start the virutal machine, running false will stop the virtual machine 
- running: true|false

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

  - import_role:
      name: zer0glitch.ocpv.power
    vars:
      project: user0
      vm_name: fedora-custom
      running: true

```

License
-------

GPLv3

Author Information
------------------

Jamie Whetsell
jamie@zeroglitch.com
