# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "nvkmv/rockylinux9"
  config.vm.box_version = "2.0"
  
  config.vm.provision "ansible" do |ansible|
  # ansible.verbose = "v"
   ansible.playbook = "ansible/playbook.yml"
  end  

  config.vm.provider "virtualboxi" do |v|
    v.memory = 256
    v.cpus = 1
  end

  config.vm.define "log" do |log|
    log.vm.hostname = "log"
    log.vm.network "public_network", ip: "192.168.1.67"
    #log.vm.synced_folder "./data", "/home/vagrant/data" 
  end

  config.vm.define "web" do |web|
    web.vm.hostname = "web"
    web.vm.network "public_network", ip: "192.168.1.66"
    #web.vm.synced_folder "./data", "/home/vagrant/data" 
  end
end
