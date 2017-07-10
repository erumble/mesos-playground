# Mesos Playground
About
---
Within this repository are the necessary files to provision a small VM that will run a mesos cluster from Docker.

Requirements
---
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) >= v5.1.18
* [Vagrant](https://www.vagrantup.com/) >= v1.9.3
* [Ansible](http://docs.ansible.com/ansible/intro_installation.html) >= v2.3.1.0

Optional Plugins for Vagrant
---
* [Vagrant::Hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater)
* [Vagrant::VBGuest](https://github.com/dotless-de/vagrant-vbguest)

Usage
---

    vagrant up
    vagrant ssh
    cd src/mesos-playground
    docker-compose up -d
  
Go to [mesos-playground.invalid:5050](http://mesos-playground.invalid:5050) to access the Mesos web interface   
Go to [mesos-playground.invalid:8080](http://mesos-playground.invalid:8080) to access the Marathon web interface

Have fun creating tasks with Marathon

Notes
---
If you decide to use the Vagrant Hostsupdater plugin (which you should), and you are on a Mac running OSX,
you can add the following snippet to a file in your sudoers.d directory to allow the plugin to update /etc/hosts
without requiring a password.  

*It is strongly recommended that you do this by running the following command*  
`sudo visudo -f /etc/sudoers.d/vagrant_hostsupdater`  
then simply copying and pasting the snippet.

    # Allow passwordless startup of Vagrant with vagrant-hostsupdater.
    Cmnd_Alias VAGRANT_HOSTS_ADD = /bin/sh -c echo "*" >> /etc/hosts
    Cmnd_Alias VAGRANT_HOSTS_REMOVE = /usr/bin/sed -i -e /*/ d /etc/hosts
    %admin ALL=(root) NOPASSWD: VAGRANT_HOSTS_ADD, VAGRANT_HOSTS_REMOVE
