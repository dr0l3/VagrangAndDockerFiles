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
  # config.vm.network "forwarded_port", guest: 5000, host:5000
  config.vm.provision "shell", inline: <<-SHELL
     #General updates
	 sudo apt-get update
	 sudo apt-get install python-pip
     #install redis
	 sudo apt-get install build-essential
	 sudo apt-get install tcl8.5
	 wget http://download.redis.io/releases/redis-stable.tar.gz
	 tar xzf redis-stable.tar.gz
	 cd redis-stable
	 make
	 make test
	 sudo make install
	 cd utils
	 sudo ./install_server.sh
	 cd ..
	 cd ..
	 #Install python redis-driver
	 sudo pip install redis
	 #install docker 
	 sudo apt-get -y install docker.io
	 sudp ln -sf /usr/bin/docker.io /usr/local/bin/docker
	 sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker.io
	 sudo service docker.io restart
	 sudo docker run hello-world
  SHELL
end
