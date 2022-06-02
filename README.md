# virtualbox
b1042092 b1042093
### 更新
```
sudo apt update
sudo apt upgrade
```
```
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql
```
```
sudo apt install net-tools
ifconfig
```
```
cd /var/www/html
ls
```
```
sudo apt install vim
sudo vim info.php
```
```
<?php 
      phpinfo();  
?>
:wq!(強制存檔離開
```
```
sudo apt install phpmyadim
```
```
sudo mysql -u root mysql
```
```
UPDATE user SET plugin='mysql_native_password' WHERE User='root';
```
```
FLUSH PRIVILEGES;
```
```
exit
```
```
sudo mysql_secure_installation
```
