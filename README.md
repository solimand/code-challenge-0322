# Code Challenge 
This repository contains Vagrant-Ansible code to:
- [Vagrant](https://www.vagrantup.com/) Create two centos 7 virtual machines
- [Ansible](https://www.ansible.com/) Install Docker
- Enable Docker service
- Allow Docker Engine API on local network
- [Travis](https://travis-ci.org/) Set travis ```ansible-lint``` in Continuous Integration
- ...

## Requirements 
- I used a Python virtual environment: ```python3 -m venv env```. I installed following packages:
    - molecule
    - ansible-core
    - pyvmomi
- [Vagrant]
- OS Packages
    - ansible
    - vagrant
    - libvirt
    - virtualbox
    - ansible-lint
- Current IPv4 addresses of the VMs: 192.168.56.11/12 - Do not choose an IP that overlaps with any other IP space on your system. This can cause the network to not be reachable
- Check Vagrantfile for forwarded ports. Avoid collisions with other localhost services

## Environment 
- OS: _Arch Linux_
- Python3

***
## HowTo
- ```vagrant up```
- set ports in Vagrantfile
    - ```curl -X GET "http://localhost:52375/containers/json?all=1"```
    - ```curl -X GET "http://localhost:52376/containers/json?all=1"```

In case you want to edit the vagrantfile, the suggested steps to restart the cluster are the following: ```vagrant halt``` > ```vagrant destroy``` > ```vagrant up --provision```

# TODOs
- Secure the API:
    - TLS: https://docs.docker.com/engine/security/protect-access/#use-tls-https-to-protect-the-docker-daemon-socket
    - SSH: https://docs.docker.com/engine/security/protect-access/#use-ssh-to-protect-the-docker-daemon-socket

- Install Docker Swarm
- Molecule Tests
    - molecule init scenario -r centos [inside ansible role folder]