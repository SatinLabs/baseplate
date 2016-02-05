Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "10.20.30.40"
  # config.vm.network "public_network"
  config.vm.synced_folder "shared_data", "/vagrant_data"
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "satinlabs_baseplate"
    vb.memory = "1024"
    vb.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y httpd
    sudo apt-get install -y mariadb-server
    sudo apt-get install -y mariadb
    sudo apt-get install -y php
    sudo apt-get install -y php-mysql
  SHELL
end
