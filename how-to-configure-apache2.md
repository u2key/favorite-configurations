# How to Configure Apache2

## 1. Install Required Packages
```
sudo apt install libapache2-mod-php
```

## 2. Modify Configuration files
```
sudo vim /etc/apache2/apache2.conf
```
```
<Directory /home>
  Options Indexes FollowSymLinks
  AllowOverride None
  Require all granted
</Directory>
```

```
sudo vim /etc/apache2/ports.conf
```
```
Listen 10080
```

```
sudo vim /etc/apache2/sites-available/000-default.conf
```
```
<VirtualHost *:10080>
  # ServerName www.example.com
  ServerAdmin webmaster@localhost
  DocumentRoot /home/
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

```
sudo vim /etc/apache2/envvars
```
```
export APACHE_RUN_USER=momiji
export APACHE_RUN_GROUP=momiji
export APACHE_LOG_DIR=
```
