This repository contains a Vagrantfile for helping with Python development for Solum.

Specifically, it sets up a Ubuntu 12.04 VM with several Python utilities
required for OpenStack development (Python 2.7 compiler, tox, python-dev, etc.)

I felt the need for this because I felt there was no ** fast ** method to create a local
environment for developing and unit testing Solum code.

We have the vagrant-solum-dev repo (https://github.com/rackerlabs/vagrant-solum-dev).
It installs Devstack  along with all the required development tools.
But it is too heavy weight and time consuming process if you just want a VM to develop code and run unit tests.

That's why I created this. It includes only those Python tools that are required for
development and unit testing. If you need to run functionaltests using Devstack please
use vagrant-solum-dev repo.

--

Usage:

To run tox py27 and pep8 do the following:

git clone https://github.com/devdattakulkarni/minimal-vagrant-for-python.git vagrant-devel

cd vagrant-devel

export SOLUM=path to local solum code

export SOLUMCLIENT=path to local python-solumclient code

vagrant up

vagrant ssh

cd /solum (or cd /python-solumclient)

tox -e py27

source .tox/pep8/bin/activate

flake8

-- 

Tested with Vagrant 1.6.3 and Virtualbox 4.3.12 r93733

--

Author: Devdatta Kulkarni

Patches welcome.


