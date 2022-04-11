# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "server" do |server|
    server.vm.box = "geerlingguy/centos7"
    server.vm.network "private_network", ip: "192.168.4.5"
    server.vm.synced_folder "D:/Observ", "/vagrant"

    server.vm.provider "virtualbox" do |vs|
      vs.name = "server"
      vs.memory = "512"
      vs.cpus = 2
    end

    server.vm.provision "shell", inline: <<-SHELL
    /vagrant/server.sh
    SHELL
  end


  config.vm.define "agent" do |agent|
    agent.vm.box = "geerlingguy/centos7"
    agent.vm.network "private_network", ip: "192.168.4.6"
    agent.vm.synced_folder "D:/Observ", "/vagrant"

    agent.vm.provider "virtualbox" do |va|
        va.name = "agent"
        va.memory = "512"
    end

    agent.vm.provision "shell", inline: <<-SHELL
    /vagrant/agent.sh
    SHELL
  end  
end

