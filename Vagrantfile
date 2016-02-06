Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "10.20.30.40"
  # config.vm.network "public_network"
  # config.vm.synced_folder "shared_data", "/vagrant_data"
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "satinlabs_baseplate"
    vb.memory = "1024"
    vb.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo yum -y install httpd 
    sudo yum -y install mariadb-server
    sudo yum -y install mariadb
    sudo yum -y install php
    sudo yum -y install php-mysql

    sudo echo "<?php phpinfo();" > /var/www/html/info.php

    sudo systemctl start httpd.service
    sudo systemctl enable httpd.service
    sudo systemctl start mariadb
    sudo systemctl enable mariadb.service
  SHELL



  # For Development, install phpMyAdmin
  config.vm.provision "shell", inline: <<-SHELL
    sudo yum -y install epel-release
    sudo yum -y install phpmyadmin
  SHELL

  config.vm.provision "file", source: "./configs/phpmyadmin/phpMyAdmin.conf", destination: "/etc/httpd/conf.d/phpMyAdmin.conf"
  config.vm.provision "file", source: "./configs/phpmyadmin/config.inc.php", destination: "/etc/phpmyadmin/config.inc.php"

  config.vm.provision "shell", inline: <<-SHELL
    sudo systemctl restart httpd.service
  SHELL

end
