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

git clone https://github.com/devdattakulkarni/minimal-vagrant-for-python.git vagrant-devel

cd vagrant-devel

environment variables to map the directories on the host
within the VM
solum code from your host is mapped to /solum
python-solumclient code is mapped to /python-solumclient

export SOLUM=path to local solum code

export SOLUMCLIENT=path to local python-solumclient code

vagrant up

vagrant ssh

Tested with Vagrant 1.6.3 and Virtualbox 4.3.12 r93733


Author: Devdatta Kulkarni


Patches welcome.


