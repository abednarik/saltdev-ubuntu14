# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "ubuntu"

  config.vm.box_check_update = false
  config.vm.synced_folder "saltstack/srv", "/srv"
  config.vm.synced_folder "saltstack/etc", "/etc/salt"
  
  ##  Personal config goes here.
  # - salt source code
  config.vm.synced_folder "~/work/code/salt/salt", "/root/salt"
  # - vim
  config.vm.provision "file", source: "~/.vimrc", destination: ".vimrc"
  config.vm.synced_folder "~/.vim", "/home/vagrant/.vim"


  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
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
    sudo apt-get purge -y chef puppet
    sudo apt-get update
    sudo apt-get dist-upgrade
    sudo apt-get install -y vim tmux git python-dev python-pip git-core virt-what python-m2crypto
    sudo apt-get autoremove -y
    sudo pip install pyzmq PyYAML pycrypto msgpack-python jinja2 psutil
  SHELL
end
