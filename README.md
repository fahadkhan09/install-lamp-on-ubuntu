
**How to Install LAMP server and PHPMyAdmin on Ubuntu 20.04 LTS**  

Installation Steps with all required commands – 

Update apt tool either by 
1) Software updater
2) Through terminal
 sudo apt update
Enter your System root password
 sudo apt upgrade
Press Y to continue
CHECK once again by entering following commands
sudo apt update
sudo apt upgrade
sudo apt autoremove
Press Y to continue
Don’t forget to reset machine and verify again

**Step -1** 
Install Apache Web Server on ubuntu 20.04 LTS :
 sudo apt install apache2 -y

CHECK : Whether Apache web server is successfully installed or not
So, goto browser and type anyone form following in address bar 
http://localhost/
http://127.0.0.1/
http://your_machine_ip_address/

Enable firewall settings by following commands :
sudo ufw status
sudo ufw enable
sudo ufw app list
sudo ufw allow in "Apache Full"

**Step - 2** 
Install mysql-server on ubuntu 20.04 LTS :
 sudo apt install mysql-server
press Y to continue
CHECK : Login mysql with root user without password with sudo
 sudo mysql

create database db_name;
use db_name;
select database();
exit

**Step - 3.**
Install php and its required libraries:
 sudo apt install php php-mysql libapache2-mod-php   
Press Y to continue
 php -v

Create one sample php file in Apache Web server root directory 
 cd /var/www/html
 sudo gedit file_name.php

Goto browser and run
        http://localhost/file_name.php

PERMISSION for apache root directory
 sudo chown -R $USER:$USER /var/www/html

To enable right click - new document
 touch ~/Templates/Empty Document

Create a php file without sudo through terminal using gedit
 gedit file_name.php

Goto browser and run
        http://localhost/file_name.php


**Step - 4.**
Install PHPMyAdmin
 sudo apt update
 sudo apt install php-mbstring php-zip php-gd php-json php-curl
Press Y to continue
 sudo apt install phpmyadmin
Press Y to continue
Select Apache2 by pressing space and then press tab and OK
Press Yes and set password for dummy user phpMyAdmin
 sudo systemctl restart apache2

CHECK : Whether phpMyAdmin is successfully installed or not
So, goto browser and type  
        http://localhost/phpmyadmin
Default user name : phpMyAdmin
And enter your password


sudo apt update
Set root password and create a new database user with full privileges
 sudo mysql
 SELECT user,authentication_string,plugin,host FROM mysql.user;
 ALTER USER ‘root’@‘localhost’ IDENTIFIED WITH caching_sha2_password BY ‘password’;
 SELECT user,authentication_string,plugin,host FROM mysql.user;
 exit
 sudo mysql -p
Enter your password
 CREATE USER ‘new_user’@‘localhost’ IDENTIFIED WITH caching_sha2_password BY ‘password’; 
 GRANT ALL PRIVILEGES ON *.* TO ‘new_user’@‘localhost’ WITH GRANT OPTION;
 exit


Once again
 sudo systemctl restart apache2
 sudo systemctl restart mysql

Goto web browser and type
        http://localhost/phpmyadmin
Enter new user name and password
And create some databases, table and execute some queries through GUI


Source https://www.youtube.com/watch?v=46_hyK-uBrQ
