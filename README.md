This repository contains a Vagrantfile for helping with Python development.

Specifically, it sets up a Ubuntu 12.04 VM with several Python utilities
required for OpenStack development (Python 2.7 compiler, tox, python-dev, etc.)

I felt the need for this because I felt there was no easy way to create a local
environment for developing and testing Solum code.

We have the vagrant-solum-dev repo (https://github.com/rackerlabs/vagrant-solum-dev).
It installs Devstack  along with all the required development tools.
But it is too heavy weight and time consuming process if you just want a VM to develop code and run unit tests.

That's why I created this.

Patches welcome.

Author: Devdatta Kulkarni


