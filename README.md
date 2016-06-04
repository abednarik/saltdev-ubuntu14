Salt Development Environment in Vagrant
=======================================

Personal Vagrantfile for SaltStack Development in Ubuntu 14.04 LTS

Instructions
------------

1. Run the following commands in a terminal. Git, VirtualBox and Vagrant must
already be installed.

    ```
    git clone git@github.com:abednarik/saltdev-ubuntu.git
    cd saltdev-ubuntu
    ```

2. Edit Vagrantfile to update your local salt repository path and launch
ubuntu instance
    
    ```
    vagrant up
    ```
    
3. Finally login as vagrant user and install salt using pip in editable module

    ```
    vagrant ssh
    sudo su -
    cd salt  
    pip install -e .
    ```
    
4. For developing and debugging I use tmux to run salt-master and salt-minion
in foreground in error mode [ I mostly add log.error when I want to debug something ]

    ```
    sudo salt-master -l error
    sudo salt-minion -l error
    ```

5. Remember to accept minion keys after first minion run.

    ```
    salt-keys -A
    ```

There is a placeholder state in /srv/salt called *default.sls*. Just put the content
you want to test and run

    salt 'salt' state.apply default

This is heavily based on [salt-vagrant-demo](https://github.com/UtahDave/salt-vagrant-demo) following
official [Salt Development Docs](https://docs.saltstack.com/en/develop/topics/development/index.html)
