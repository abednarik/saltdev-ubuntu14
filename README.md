Salt Development Environment in Vagrant
=======================================

Personal Vagrantfile for SaltStack Development in Ubuntu 14 LTS


Instructions
------------

Run the following commands in a terminal. Git, VirtualBox and Vagrant must
already be installed.


    git clone git@github.com:abednarik/saltdev-ubuntu.git
    cd saltdev-ubuntu

Edit Vagrantfile adding/removing desired configuration like vim or screen.
Also make sure to update your current salt source path and public ssh key.
Finally launch ubuntu instance

    vagrant up
