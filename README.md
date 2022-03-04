# Overview 
This repository contains Vagrant-Ansible code to:
- create two centos virtual machines
- install docker inside them
- ...

# Requirements 
- **pyvmomi** via ```pip install```
- [**Vagrant**](https://www.vagrantup.com/)
- Packages
    - ansible
    - vagrant
    - libvirt
    - virtualbox
- Current IPv4 addresses of the VMs: 192.168.56.11/12 - Do not choose an IP that overlaps with any other IP space on your system. This can cause the network to not be reachable.

# Environment 
- OS: _Arch Linux_
- Role file tree - ```ansible-galaxy role init centos``` in the proj root


***
# HowTo
## Run demo
- ```vagrant up```

## Editing config
- ```vagrant halt```
- ```vagrant up --provision```