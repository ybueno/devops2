# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.box_check_update = false
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  # config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "public_network"

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
  end
  
  (1..2).each do |i|
    config.vm.define "ubuntu#{i}" do |node|
      node.vm.hostname = "ubuntu#{i}"
      node.vm.provision "shell", inline: <<-SHELL
        apt clean all
        apt update
        
      SHELL
    end
  end

  (1..2).each do |i|
    config.vm.define "centos#{i}" do |node|
      node.vm.hostname = "centos#{i}"
      node.vm.provision "shell", inline: <<-SHELL
        yum update -y
      SHELL
    end
  end
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
