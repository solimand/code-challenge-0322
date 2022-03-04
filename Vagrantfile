Vagrant.configure("2") do |config|

    config.vm.define "centos_local_1" do |centos1|
        centos1.vm.box = "generic/centos7"
        centos1.vm.provision "ansible_local" do |ansible|
            ansible.limit = 'all'
            ansible.inventory_path = 'hosts'
            ansible.playbook = 'local.yml'
        end
        centos1.vm.synced_folder ".", "/vagrant"
    end

    config.vm.define "centos_local_2" do |centos2|
        centos2.vm.box = "generic/centos7"
        centos2.vm.provision "ansible_local" do |ansible|
            ansible.limit = 'all'
            ansible.inventory_path = 'hosts'
            ansible.playbook = 'local.yml'
        end
        centos2.vm.synced_folder ".", "/vagrant"
    end

    # TODO testing...
    #config.vm.provision :serverspec do |spec|
    #    spec.pattern = 'test/*_spec.rb' # pattern for spec files
    #end
end

