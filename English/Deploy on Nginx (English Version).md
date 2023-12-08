# Tutorial

## Steps:
1. Ensure that php, php-fpm, and php-mysql are already installed on your application. To check, use the following command line:
   ```bash
   1. apt search php[your php version], for example, apt search php8.1 << the goal is to check if the package is available in the repositories of your operating system. If not, try using a public repository for the installation process.
   2. apt-get install php8.1 -y << this is an example command to install php with version 8.1, you can adjust according to the php version needed for your Laravel application.

   Repeat step 2 to install php-mysql and php-fpm.
   Note: apt-get install [package to be installed] -y
   ```
   Once installed, check if php-fpm is running with the following command:
   ```bash
   systemctl status php8.1-fpm

   Expected result:
   php8.1-[your php version].service - PHP 8.1 FastCGI Process Manager FPM for [Server OS]
       Loaded: loaded (/lib/systemd/system/php[your php version]-fpm.service)
       Active: active (php-fpm running)
   ```
   If it's not running, try starting it with systemctl start php-fpm.
2. Update the default configuration of Nginx. By default, the Nginx configuration file is located at /etc/nginx/sites-available/ with the filename default. Update the configuration file using a text editor, for example, with the nano command: nano /etc/nginx/sites-available/default.
Example Configuration:
<img width="807" alt="gambar" src="https://github.com/RNando1337/Laravel-Deploy-Methods/assets/60562868/06a6b8d2-9e11-44f1-86e4-c71ecebbe7cd">
