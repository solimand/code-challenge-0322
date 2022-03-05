# Overview 
This repository contains Vagrant-Ansible code to:
- create two centos virtual machines
- install docker inside them
- enable service Docker
- forward ports to use API Engine

# Requirements 
- **pyvmomi** via ```pip install```
- [**Vagrant**](https://www.vagrantup.com/)
- Packages
    - ansible
    - vagrant
    - libvirt
    - virtualbox
    - ansible-lint
- Current IPv4 addresses of the VMs: 192.168.56.11/12 - Do not choose an IP that overlaps with any other IP space on your system. This can cause the network to not be reachable
- Check Vagrantfile for forwarded ports. Avoid collisions with other localhost services

# Environment 
- OS: _Arch Linux_
- Role file tree - ```ansible-galaxy role init centos``` in the proj root


***
# HowTo
## Run demo
- ```vagrant up```
- set ports accordingly in Vagrantfile
    - ```curl -X GET "http://localhost:52375/containers/json?all=1"```
    - ```curl -X GET "http://localhost:52376/containers/json?all=1"```

## Editing config
- ```vagrant halt```
- ```vagrant up --provision```

# TODOs
- Secure the API:
    - TLS: https://docs.docker.com/engine/security/protect-access/#use-tls-https-to-protect-the-docker-daemon-socket
    - SSH: https://docs.docker.com/engine/security/protect-access/#use-ssh-to-protect-the-docker-daemon-socket

- Install Docker Swarm
- Molecule Tests
- Travis - linting code