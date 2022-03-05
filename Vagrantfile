DOCKER_API_PORT = 2375
HOST1_IP = "192.168.56.11"
HOST2_IP = "192.168.56.12"
HOST1_PORT = 52375 # vm1 docker engine port forwarded on localhost
HOST2_PORT = 52376 # vm2 docker engine port forwarded on localhost

Vagrant.configure("2") do |config|

    config.vm.define "centos_local_1" do |centos1|
        centos1.vm.box = "generic/centos7"
        centos1.vm.provision "ansible_local" do |ansible|
            ansible.limit = 'all'
            ansible.inventory_path = 'hosts'
            #ansible.galaxy_command = "ansible-galaxy collection install ansible.posix"
            #ansible.galaxy_role_file = 'requirements.yml'
            ansible.playbook = 'local.yml'
        end
        centos1.vm.synced_folder ".", "/vagrant"
        centos1.vm.network "private_network", ip: HOST1_IP
        centos1.vm.network "forwarded_port", guest: DOCKER_API_PORT, host: HOST1_PORT
    end

    config.vm.define "centos_local_2" do |centos2|
        centos2.vm.box = "generic/centos7"
        centos2.vm.provision "ansible_local" do |ansible|
            ansible.limit = 'all'
            ansible.inventory_path = 'hosts'
            ansible.playbook = 'local.yml'
        end
        centos2.vm.synced_folder ".", "/vagrant"
        centos2.vm.network "private_network", ip: HOST2_IP
        centos2.vm.network "forwarded_port", guest: DOCKER_API_PORT, host: HOST2_PORT
    end

    # TODO testing...
    #config.vm.provision :serverspec do |spec|
    #    spec.pattern = 'test/*_spec.rb' # pattern for spec files
    #end
end

