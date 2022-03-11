# Code Challenge Intro
This repository contains Vagrant-Ansible code to automate centos and Docker Swarm provisioning.

## Achievements
- [Vagrant](https://www.vagrantup.com/) Create two centos 7 virtual machines
- [Ansible](https://www.ansible.com/) Install Docker
- Enable Docker service
- Allow Docker Engine API on local network
- [Travis](https://travis-ci.org/) Set travis ```ansible-lint``` in Continuous Integration
- Create Docker Swarm Master node and set output variable accordingly to the worker token
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
- Secure the Dcoker API access:
    - TLS: https://docs.docker.com/engine/security/protect-access/#use-tls-https-to-protect-the-docker-daemon-socket
    - SSH: https://docs.docker.com/engine/security/protect-access/#use-ssh-to-protect-the-docker-daemon-socket

- Join Docker Swarm Worker
    - FIX ansible_vars global
    - pass worker-token from docker swarm master to worker
- Molecule Tests
