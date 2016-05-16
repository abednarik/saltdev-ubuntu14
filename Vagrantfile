# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "salt"

  config.vm.synced_folder "saltstack/srv", "/srv"
  config.vm.synced_folder "saltstack/etc", "/etc/salt"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.name = "salt"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get purge -y chef puppet
    sudo apt-get update
    sudo apt-get dist-upgrade
    sudo apt-get install -y vim tmux git python-dev python-pip git-core virt-what python-m2crypto
    sudo apt-get autoremove -y
    sudo pip install pyzmq PyYAML pycrypto msgpack-python jinja2 psutil
  SHELL
end
