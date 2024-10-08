# Deploy Laravel application with Apache2

1. **update ubuntu first**
```
sudo apt-get update
sudo apt-get install apache2
```

3. **this is optional, only run if the php requirements are <= 8.2.6**
```
sudo add-apt-repository -y ppa:ondrej/php 
sudo apt-get update
```

4. **install all php package**
```
sudo apt install php php-cli php-mbstring php-xml php-zip php-mysql composer
```
or you can use this command, and install seperately

```
sudo apt install php-fpm php-mysql php-gd php-curl php-xml php-zip php-mbstring php-json php-dom php-xmlrpc
```

```
# Download and install Composer globally
sudo php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

# Remove the temporary installation script
sudo php -r "unlink('composer-setup.php');"
```

5. **search and change ;cgi.fix_pathinfo=1 into cgi.fix_pathinfo=0**
```
sudo nano /etc/php/8.2/apache2/php.ini
sudo nano /etc/php/8.2/cli/php.ini
```

6. **setup customize configuration**
```
sudo nano /etc/apache2/sites-available/laravel.conf
```

```
<VirtualHost *:80>
    ServerAdmin <IP_ADDRESS>
    ServerName <IP_ADDRESS>
    ServerAlias <IP_ADDRESS>
    DocumentRoot "/var/www/html/laravel/public"
    <Directory /var/www/html/laravel/public>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

```
sudo systemctl restart apache2
```

6. **setup laravel.conf as default configuration**
```
sudo a2enmod rewrite
sudo systemctl restart apache2

sudo a2ensite laravel.conf
sudo systemctl restart apache2
```

7. **upload your laravel project**
```
sudo git clone
sudo cp .env.example .env
```

8. **change permission of laravel project**
```
sudo chown -R www-data:www-data /var/www/html/laravel
sudo chmod -R 775 /var/www/html/laravel
sudo chmod -R 775 /var/www/html/laravel/storage
sudo chmod -R 775 /var/www/html/laravel/bootstrap/cache
```

# Situational

- **install Node.js and npm**
```
sudo apt-get install nodejs npm
```

- **install git**
```
sudo apt install git
```

- **to ignore platform PHP requirements**
```
composer install --ignore-platform-reqs
```

- **restart apache 2 server**
```
sudo systemctl restart apache2 | sudo service apache2 restart
```

- **uninstall all package in php including composer**
```
sudo apt-get purge 'php*'
```
- **rename folder**
```
sudo mv old_name new_name
```