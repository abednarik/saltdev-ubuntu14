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
    sudo pip install -e .

For developing and debugging I use screen to run salt-master and salt-minion
in foreground in error mode [ I mostly add log.error when I want to debug something ]

    sudo salt-master -l error
    sudo salt-minion -l error

Remember to accept minion keys after first minion run.

   salt-keys -A

There is a placeholder state in /srv/salt called source.sls. Just put the content
you want to test and run

    salt ubuntu state.apply source

This is heavily based on [salt-vagrant-demo](https://github.com/UtahDave/salt-vagrant-demo) following
official [Salt Development Docs](https://docs.saltstack.com/en/develop/topics/development/index.html)
