# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define :lb1, autostart: false do |lb1|
    lb1.vm.box = "ubuntu/vivid64"
    lb1.vm.network "private_network", ip: "10.11.1.100"
    lb1.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
    lb1.vm.network "forwarded_port", guest: 22, host: 2200

  end

  config.vm.define :www1 do |www1|
    www1.vm.box = "ubuntu/vivid64"
    www1.vm.network "private_network", ip: "10.11.1.101"
    www1.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
    www1.vm.network "forwarded_port", guest: 22, host: 2201

  end

  config.vm.define :www2, autostart: false do |www2|
    www2.vm.box = "ubuntu/vivid64"
    www2.vm.network "private_network", ip: "10.11.1.102"
    www2.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
    www2.vm.network "forwarded_port", guest: 22, host: 2202

  end

  config.vm.define :db1 do |db1|
    db1.vm.box = "hashicorp/precise64"
    db1.vm.network "private_network", ip: "10.11.1.103"
    db1.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
    db1.vm.network "forwarded_port", guest: 22, host: 2203

  end

  config.vm.define :db2, autostart: false do |db2|
    db2.vm.box = "hashicorp/precise64"
    db2.vm.network "private_network", ip: "10.11.1.104"
    db2.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
    db2.vm.network "forwarded_port", guest: 22, host: 2204

  end

  config.vm.define :control do |control|
    control.vm.box = "mjp182/CentOS_6.6"
    control.vm.network "private_network", ip: "10.11.1.105"
    control.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
    control.vm.network "forwarded_port", guest: 22, host: 2205
    control.vm.synced_folder "ansible/", "/home/vagrant/ansible"
    control.vm.synced_folder ".vagrant/", "/home/vagrant/.v"
    control.vm.provision "shell", inline: "sudo yum -y install epel-release; sudo yum -y install ansible"
  end



end
