Installation requirements :

- ffmpeg
- nginx
- php-fpm
- mysql-server

How to configure nginx, php-fpm and mysql-server :

https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-ubuntu-18-04

File configuration must be edited with the following : 

- In /etc/php/7.2/fpm/php.ini file, change :

    - post_max_size from 25M to 0M
    - upload_max_filesize from 2M to 512M

- In /etc/nginx/nginx.conf, add :

    - client_max_body_size 512M;

Then, restart services :

sudo systemctl restart php7.2-fpm
sudo systemctl restart nginx

Go to ./backend and create database :

sudo mysql -u root < db.sql

Then, edit ./backend/env/config.php and fill in the correct identifiers for access to the database.

Now, go to http://localhost/Youtube-Multistream-Interface/
