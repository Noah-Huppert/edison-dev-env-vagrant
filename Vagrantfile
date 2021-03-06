# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

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
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "./code", "/home/vagrant/code"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    # Install common
    sudo apt-get update
    sudo apt-get install unzip -y
    # Install C build tools
    sudo apt-get install gcc -y
    sudo apt-get install g++ -y
    sudo apt-get install gcc-multilib -y
    sudo apt-get install build-essential -y
    sudo apt-get install make -y
    sudo apt-get install automake -y
    # Install CMake
    mkdir /home/vagrant/downloads
    cd /home/vagrant/downloads
    wget http://www.cmake.org/files/v3.2/cmake-3.2.2-Linux-x86_64.tar.gz
    tar -zxvf cmake-3.2.2-Linux-x86_64.tar.gz
    sudo cp -r --copy-contents cmake-3.2.2-Linux-x86_64 /opt
    echo "PATH=$PATH:/opt/cmake-3.2.2-Linux-x86_64/bin" > /home/vagrant/.profile
    # Install Intel Edison SDK
    cd /home/vagrant/downloads
    wget http://downloadmirror.intel.com/24910/eng/edison-sdk-linux64-ww18-15.zip
    unzip edison-sdk-linux64-ww18-15.zip
    sudo ./poky-edison-eglibc-x86_64-edison-image-core2-32-toolchain-1.6.1.sh -y
    echo "#!/bin/sh\nsource /opt/poky-edison/1.6.1/environment-setup-core2-32-poky-linux;\nexit 0;" > /etc/rc.local
    # source /opt/poky-edison/1.6.1/environment-setup-core2-32-poky-linux
  SHELL
end
