# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "ubuntu"

  config.vm.box_check_update = false
  config.vm.network "public_network", ip: "192.168.1.101", bridge: "en0: Wi-Fi (AirPort)"
  config.vm.synced_folder "~/work/code/salt/salt", "/home/vagrant/salt"
  config.vm.synced_folder "~/.vim", "/home/vagrant/.vim"
  config.vm.provision "file", source: "~/.vimrc", destination: ".vimrc"
  config.vm.provision "file", source: "~/.screenrc", destination: ".screenrc"
  config.vm.synced_folder "saltstack/salt/", "/srv/salt"
  config.vm.synced_folder "saltstack/pillar/", "/srv/pillar"
  config.vm.synced_folder "saltstack/etc/", "/etc/salt"

  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa-abednarik_lespaul.pub").first.strip
    s.inline = <<-SHELL
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.name = "ubuntu"
  end

  config.vm.define "ubuntu" do |i|
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y vim screen git rsync python-dev python-setuptools python-pip git-core python-m2crypto
    sudo install pyzmq PyYAML pycrypto msgpack-python jinja2 psutil
  SHELL
end
