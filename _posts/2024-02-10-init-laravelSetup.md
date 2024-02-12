---
date: 2023-12-12T23:12:48+05:45
title: "PHP, Laravel, MySQL InitSetup on Ubuntu"
description : "Docs On Setting Up PHP, Laravel & MySQl on Ubuntu"
categories : ["Setups"]
tags : ["laravel","mySQL","ubuntu","init","setup","blog"]
---

The scripts have been verified on _Ubuntu 22.04 LTS_ :

Apache Setup
```bash
sudo apt update -y; && sudo apt upgrade -y;
sudo apt install apache2;
sudo systemctl enable apache2; && sudo systemctl start apache2;
sudo systemctl status apache2;
```

PHP Setup. Use the PPA of ondrej for installing different versions of PHP later on
```bash
sudo apt install software-properties-common;
sudo add-apt-repository ppa:ondrej/php;
sudo apt update;
sudo apt-get install php php-fpm;
sudo apt-get install php-mysql php-mbstring php-xml php-gd php-curl php-cli php-common php-imap php-redis php-snmp php-zip php-json;

#PHP Version Change
sudo update-alternatives --config php;
```

Composer Setup. It's a dependency manager for PHP
```bash
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer;
composer;

#Laravel Project Init
composer create-project laravel/laravel projectName
```

phpMyAdmin Setup
```bash
wget https://files.phpmyadmin.net/phpMyAdmin/5.2.0/phpMyAdmin-5.2.0-all-languages.zip;
unzip phpMyAdmin-5.2.0-all-languages.zip;
sudo mv phpMyAdmin-5.2.0-all-languages /usr/share/phpmyadmin; 
sudo mkdir /usr/share/phpmyadmin/tmp;
sudo chown -R www-data:www-data /usr/share/phpmyadmin;
sudo chmod 777 /usr/share/phpmyadmin/tmp;
sudo nano /etc/apache2/conf-available/phpmyadmin.conf;
```
_After opening the conf, paste the following:_

```bash
Alias /phpmyadmin /usr/share/phpmyadmin
Alias /phpMyAdmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin/>
   AddDefaultCharset UTF-8
   <IfModule mod_authz_core.c>
      <RequireAny>
      Require all granted
     </RequireAny>
   </IfModule>
</Directory>
 
<Directory /usr/share/phpmyadmin/setup/>
   <IfModule mod_authz_core.c>
     <RequireAny>
       Require all granted
     </RequireAny>
   </IfModule>
</Directory>
```
```bash
#Enable Conf & finish phpmyadmin setup
sudo a2enconf phpmyadmin 
sudo systemctl restart apache2 
```

MySQL Setup
```bash
sudo apt install mysql-server;
sudo mysql;

#Inside mysql prompt setup db & user
CREATE DATABASE phpmadmin;
CREATE USER 'array'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON array.* TO 'array'@'localhost';
FLUSH PRIVILEGES;
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
FLUSH PRIVILEGES;
```

Node Setup
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash;
source ~/.bashrc;
nvm install node;
node --version;
```
