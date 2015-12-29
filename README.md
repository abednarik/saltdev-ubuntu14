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

Finally login as vagrant user and install salt using pip in editable module

    cd salt  
    pip -e .

For developing and debugging I use screen to run salt-master and salt-minion
in foreground in debug module

    sudo salt-master -l debug
    sudo salt-minion -l debug

Remember to accept minion keys after first minion run.

   salt-keys -A
