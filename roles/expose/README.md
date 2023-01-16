Role Name
=========

This role exposes a port to the virtual machine

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
# The kubevirt domain/name of the server
- kubevirt_domain: "myawesomeserver"

# namespace to operate on
- namespace: user1

# name of the service/route
- name: "ssh"

# optional hostname for the route
- host: "ssh.myserver.com"

# random node port
- port: "51838"

# The target port
- target_port: "22"

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
      name: zer0glitch.ocpv.expose
    vars:
      kubevirt_domain: "myawesomeserver"
      namespace: user1
      name: "ssh"
      host: "ssh.myserver.com"
      port: "51838"
      target_port: "22"


```

License
-------

GPLv3

Author Information
------------------

Jamie Whetsell
jamie@zeroglitch.com
