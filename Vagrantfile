# -*- mode: ruby -*-
# vi: set ft=ruby :

host_cache_path = File.expand_path("../.cache", __FILE__)
guest_cache_path = "/tmp/vagrant-cache"

# ensure the cache path exists
FileUtils.mkdir(host_cache_path) unless File.exist?(host_cache_path)

# unused right now; putting these here so that we can build in
# additional functionality
SOLUM_BRANCH          = ENV['SOLUM_BRANCH']          ||= "master"
SOLUM_REPO            = ENV['SOLUM_REPO']            ||= "https://github.com/stackforge/solum.git"
SOLUMCLIENT_BRANCH    = ENV['SOLUMCLIENT_BRANCH']    ||= "master"
SOLUMCLIENT_REPO      = ENV['SOLUMCLIENT_REPO']      ||= "https://github.com/stackforge/python-solumclient.git"
SOLUM_IMAGE_FORMAT    = ENV['SOLUM_IMAGE_FORMAT']    ||= "docker"


# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu-12.04-development"
  #config.vm.box_url = 'http://55e99fc2f9b7a4001bc8-51d789ac964757728410a7d1f622e9af.r39.cf1.rackcdn.com/ubuntu-12.04-amd64-vbox.box'
  config.vm.box_url = 'https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box'

  #config.vm.customize ["modifyvm", :id, "--name", "solum-development-vm"]

  if ENV['SOLUM']
    config.vm.synced_folder ENV['SOLUM'], "/solum"
  end

  if ENV['SOLUMCLIENT']
    config.vm.synced_folder ENV['SOLUMCLIENT'], "/python-solumclient"
  end

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
     # Don't boot with headless mode
     #vb.gui = true
     vb.name = "solum-development-vm"
  
     # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # Install the required packages for Python development
  config.vm.provision :shell, :inline => <<-SCRIPT
    apt-get update
    apt-get -y install git socat curl wget build-essential python-mysqldb \
        python-dev libssl-dev python-pip git-core libxml2-dev libxslt-dev \
        python-pip libmysqlclient-dev vim screen libffi-dev \
        python-software-properties 

    add-apt-repository ppa:fkrull/deadsnakes

    apt-get update

    apt-get install python3.3

    pip install virtualenv
    pip install tox==1.6.1
    pip install setuptools
    SCRIPT

end
