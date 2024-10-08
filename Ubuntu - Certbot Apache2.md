# How to Install Certbot in Apache2

### Installation

- Install certbot
```
sudo apt install certbot python3-certbot-apache
```

- Make sure your configurations are all correct and have A records that target your public IP address

- Install certbot apache
```
sudo certbot --apache

OR

sudo certbot --apache -d <your_domain> -d <your_sub_domain>
```



- Once installation is done, Enable the SSL Module
```
sudo a2enmod ssl
```

- Set up your updated configuration to redirect your HTTP request to HTTPS.
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName <DOMAIN.COM>
    ServerAlias www.<DOMAIN.COM>
    DocumentRoot "/var/www/html/<FOLDER_PATH>/public_html"

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</VirtualHost>

<VirtualHost *:443>
    ServerAdmin webmaster@localhost
    ServerName <DOMAIN.COM>
    ServerAlias www.<DOMAIN.COM>
    DocumentRoot "/var/www/html/<FOLDER_PATH>/public_html"

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    SSLEngine on
    SSLCertificateFile /etc/letsencrypt/live/<FOLDER_PATH>/fullchain.pem
    SSLCertificateKeyFile /etc/letsencrypt/live/<FOLDER_PATH>/privkey.pem
</VirtualHost>
```

### Certbot Certification

- Check Certificate Expiration
```
certbot certificates
```

- Manually Renew Certificates
```
certbot renew
```

- If you want to force a renewal _even if the certificate is not near its expiration date_
```
certbot renew --force-renewal
```

### Set Up Automatic Renewal
Certbot installs a cron job or a systemd timer that runs twice a day to renew any certificate within 90 days of expiration automatically. You can check the cron job or systemd timer to ensure it is set up correctly.

- To check the cron job, you can view the cron configuration file
```
cat /etc/cron.d/certbot
```
it should be look like this
```
0 */12 * * * root certbot renew --quiet
or
0 */12 * * * root test -x /usr/bin/certbot -a \! -d /run/systemd/system &amp;&amp; perl -e 'sleep int(rand(43200))' &amp;&amp; certbot -q renew
```

- To check the systemd timer
```
systemctl list-timers | grep certbot
```

- This should show you the status of the Certbot timer. To see more details
```
systemctl status certbot.timer
```

- To test the renewal process without actually renewing the certificates
```
certbot renew --dry-run
```

### Additional syntax
- Check the Configuration File for Syntax Errors `sudo apachectl configtest`
