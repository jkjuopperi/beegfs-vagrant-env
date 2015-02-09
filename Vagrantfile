# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "chef/centos-7.0"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.sudo = true
    ansible.groups = {
     "mgmt" => ["mgmt0"],
     "meta" => ["meta0"],
     "storage" => ["storage0"],
     "clients" => ["client0"],
     "all_groups:children" => ["mgmt", "meta", "storage", "clients"]
    }
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "512"
  end
  
  config.vm.define "mgmt0" do |config|
    config.vm.hostname = "mgmt0"
    config.vm.network "private_network", ip: "192.168.44.10"
  end

  config.vm.define "meta0" do |config|
    config.vm.hostname = "meta0"
    config.vm.network "private_network", ip: "192.168.44.20"
  end

  config.vm.define "storage0" do |config|
    config.vm.hostname = "storage0"
    config.vm.network "private_network", ip: "192.168.44.30"
  end

  config.vm.define "client0" do |config|
    config.vm.hostname = "client0"
    config.vm.network "private_network", ip: "192.168.44.40"
  end

end
