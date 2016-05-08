# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  #The box to be used
  config.vm.box = "ubuntu/trusty64"
  # Port forwarding
  # config.vm.network "forwarded_port", guest: 5000, host:5000
  
  #Shell commands
  config.vm.provision "shell", inline: <<-SHELL
     	#General updates
	sudo apt-get update
	sudo apt-get -y install python-pip
	sudo apt-get -y install python3-pip
	
	#install node.js
	curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash - #for 4.0 version
	sudo apt-get -y install nodejs
	sudo apt-get -y install npm
	
	#install npm libraries
	sudo npm install highcharts
	sudo npm install jquery
	sudo npm install --no-bin-links express #if vagrant on windows. otherwise probably not needed.
	 
	#install java 8. Last command doesn't work.
	sudo apt-get install -y python-software-properties
	sudo add-apt-repository -y ppa:webupd8team/java
	sudo apt-get update
	sudo apt-get install -y oracle-java8-installer
	 
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
	 
	#Install redis-driver
	sudo pip install redis
	sudo pip3 install redis
	sudo npm install redis
	 
	#Install mongodb
	sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
	echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
	sudo apt-get update
	sudo apt-get install -y mongodb-org
	 
	#install docker 
	sudo apt-get -y install docker.io
	sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker
	sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker.io
	sudo service docker.io restart
	sudo docker run hello-world
	adduser vagrant
	usermod -aG docker vagrant
	
	#Example addition to .bashrc file
	echo "insert random stuff here" >> /home/vagrant/.bashrc
  SHELL
end
