# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "ldap-serv" do |serv|
    serv.vm.box = "geerlingguy/centos7"
    serv.vm.network "private_network", ip: "192.168.4.5"
    serv.vm.synced_folder "D:/Observ/ldap-ldap", "/vagrant"

    serv.vm.provider "virtualbox" do |vs|
      vs.name = "ldap-serv"
      vs.memory = "512"
      vs.cpus = 2
    end

    serv.vm.provision "shell", inline: <<-SHELL
    /vagrant/server.sh
    SHELL
  end


  
  config.vm.define "client" do |client|
    client.vm.box = "geerlingguy/centos7"
    client.vm.network "private_network", ip: "192.168.4.6"
    client.vm.synced_folder "D:/Observ/ldap-ldap", "/vagrant"

    client.vm.provider "virtualbox" do |vc|
      vc.name = "ldap-client2"
      vc.memory = "512"
    end

    client.vm.provision "shell", inline: <<-SHELL
    /vagrant/client.sh
    SHELL
  end
end