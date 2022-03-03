# Requirements 
- **pyvmomi** via ```pip install```
- [**Vagrant**](https://www.vagrantup.com/)
- Packages
    - ansible
    - vagrant
    - libvirt
    - virtualbox

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