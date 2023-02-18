# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/ubuntu2004"
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.network "private_network", ip: "192.168.56.19"
  config.vm.provision "shell", inline: <<-SHELL
  sudo apt update
  sudo apt install apache2 \
                ghostscript \
                libapache2-mod-php \
                mysql-server \
                php \
                php-bcmath \
                php-curl \
                php-imagick \
                php-intl \
                php-json \
                php-mbstring \
                php-mysql \
                php-xml \
                php-zip -y
  sudo mkdir -p /srv/www
  sudo chown www-data: /srv/www
  curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
  cp '/vagrant/vagrant-data/wordpress.conf' /etc/apache2/sites-available/wordpress.conf
  sudo a2ensite wordpress
  sudo a2enmod rewrite
  sudo a2dissite 000-default
  sudo systemctl reload apache2

  mysql -u root -e "CREATE DATABASE wordpress;"
  mysql -u root -e "CREATE USER wordpress@localhost IDENTIFIED BY 'admin123';"
  mysql -u root -e "GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO wordpress@localhost;"
  mysql -u root -e "FLUSH PRIVILEGES;"
  sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
  sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
  sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
  sudo -u www-data sed -i 's/password_here/admin123/' /srv/www/wordpress/wp-config.php
  service mysql restart
  SHELL
end
