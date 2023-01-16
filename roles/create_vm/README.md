Role Name
=========

This role will install Openshift Virtualization.  The OCP-v and Hyperconverged operators will be installed.

Requirements
------------

- ansible==2.10
- python module openshift
- python module jsonpath
- python module kubernetes==12.0.0



Role Variables
--------------
# This Server Hostname, and name in OCPv
* vm_name: "{{ server_name }}"

# The project in which this VM will be created
* project: "{{ project_name }}"

# The pvc boot source
* boot_source: fedora

# The type of boot source, pvc or dv
* boot_source_type: pvc

# The size of the root volume
* root_volume_size: 30

# The number of cpus
* cores: 1

# The number of sockets for the cpu
* sockets: 1

# The number of threads for the cpu
* threads: 1

# system memory in Gigabytes
* memory: 2

# Wait on the system to become active before continuing
* wait: True

# List of additional interfaces
* network_interfaces:
* - name: eth1
    bridge_name: br1
    wait: True

# List of additional drives
* data_volumes:
  - name: drive1
    size: 10Gi
  - name: drive2
    size: 20Gi

# Cloud init configution ignored with client_init_secret is present
* cloud_init: |
        #cloud-config
        users:
        - name: jamie
          gecos: Ansible User
          groups: users,admin,wheel
          sudo: ALL=(ALL) NOPASSWD:ALL
          shell: /bin/bash
          lock_passwd: false
          passwd: "{{ 'redhat' | password_hash('sha512') }}"
          ssh_authorized_keys:
          - "{{ lookup('file', '~/.ssh/id_rsa.pub') }}"

# Will store the cloud init in a secret.  This would be a cloud init definition
* cloud_init_secret:


Dependencies
------------

- kubernetes.core

Example Playbook
----------------

  - include_role:
      name: zer0glitch.ocpv.create_vm
    vars:
      vm_name: "{{ server_name }}"
      project: "{{ project_name }}"
      boot_source: fedora
      boot_source_type: pvc
      root_volume_size: 30
      cores: 1
      sockets: 1
      threads: 1
      memory: 2
      password: r3dh4t1!
      wait: True
      network_interfaces:
      - name: eth1
        bridge_name: br1
        wait: True
      data_volumes:
      - name: drive1
        size: 10Gi
      - name: drive2
        size: 20Gi
      cloud_init: |
              #cloud-config
              users:
              - name: jamie
                gecos: Ansible User
                groups: users,admin,wheel
                sudo: ALL=(ALL) NOPASSWD:ALL
                shell: /bin/bash
                lock_passwd: false
                passwd: "{{ 'redhat' | password_hash('sha512') }}"
                ssh_authorized_keys:
                - "{{ lookup('file', '~/.ssh/id_rsa.pub') }}"


License
-------

GPLv3

Author Information
------------------

Jamie Whetsell
jamie@zeroglitch.com
