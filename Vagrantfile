# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/xenial64"
    master.vm.hostname = "master"
    master.vm.box_check_update = false
    master.vm.network "private_network", ip: "192.168.33.5"

    master.vm.provider "virtualbox" do |vb|
      vb.cpus   = "2"
      vb.memory = "1024"
    end


    master.vm.provision "shell", inline: <<-SHELL
      apt-get install -y --force-yes apt-transport-https
      wget -O bootstrap_salt.sh https://bootstrap.saltstack.com
      sh bootstrap_salt.sh -M -i master -A 127.0.0.1 stable
    SHELL
  end

  config.vm.define "minion" do |minion|
    minion.vm.box = "ubuntu/xenial64"
    minion.vm.hostname = "minion1"
    minion.vm.box_check_update = false
    minion.vm.network "private_network", ip: "192.168.33.6"

    minion.vm.provider "virtualbox" do |vb|
      vb.cpus   = "2"
      vb.memory = "1024"
    end

    minion.vm.provision "shell", inline: <<-SHELL
      apt-get install -y --force-yes apt-transport-https
      wget -O bootstrap_salt.sh https://bootstrap.saltstack.com
      sh bootstrap_salt.sh -i minion1 -A 192.168.33.5 stable
    SHELL
  end

end
