This repository contains a Vagrantfile for helping with Python development.

Specifically, it sets up a Ubuntu 12.04 VM with several Python utilities
required for OpenStack development (Python 2.7 compiler, tox, python-dev, etc.)

I felt the need for this because I felt there was no easy way to create a local
environment for developing and testing Solum code.

We have the vagrant-solum-dev repo (https://github.com/rackerlabs/vagrant-solum-dev).
It installs Devstack  along with all the required development tools.
But it is too heavy weight and time consuming process if you just want a VM to develop code and run unit tests.

That's why I created this.

Usage:
------

git clone 
cd

# environment variables to map the directories on the host
# within the VM
# solum code from your host is mapped to /solum
# python-solumclient code is mapped to /python-solumclient
set SOLUM=<path to local solum code>
set SOLUMCLIENT=<path to local python-solumclient code>


vagrant up

vagrant ssh



Author:
-------
Devdatta Kulkarni


Patches welcome.


