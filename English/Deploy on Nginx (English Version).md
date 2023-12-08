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
   systemctl status php[php version]-fpm

   Expected result:
   php[php version]-fpm.service - PHP [php version] FastCGI Process Manager FPM for [Server OS]
       Loaded: loaded (/lib/systemd/system/php[your php version]-fpm.service)
       Active: active (php-fpm running)
   ```
   If it's not running, try starting it with systemctl start php-fpm.
2. Update the default configuration of Nginx. By default, the Nginx configuration file is located at `/etc/nginx/sites-available/` with the filename `default`. Update the configuration file using a text editor, for example, with the nano command: `nano /etc/nginx/sites-available/default`.
   Example Configuration:
   <img width="807" alt="gambar" src="https://github.com/RNando1337/Laravel-Deploy-Methods/assets/60562868/06a6b8d2-9e11-44f1-86e4-c71ecebbe7cd">

   Ensure that the code marked in the image above is not commented out.
   Explanation:
   - Point No. 1 is the code to set the root directory of the server. Direct the /public folder of your Laravel application to be the root directory of the server.
   - Point No. 2 is a configuration block to handle how the server processes requests to the main URL (root),
     ```bash
     location / {
        try_files $uri $uri/ /index.php$is_args$args;
     }
     ```
     Where the above code attempts to find a file that matches the requested URI. If not found, it redirects to index.php with any possible arguments.
   - Points No. 3, 4, 5 are by default still commented out, so remove the pound sign (#) in front of the marked code.
     ```bash
      fastcgi_pass unix:/var/run/php/php[your php version]-fpm.sock;
     ```
     Adjust the version of the php unique socket you are using.
   - Point No. 6 is a code block that denies access to .htaccess files to prevent unauthorized access to configuration files in the public folder, etc.

3. After updating the configuration, check for errors with the command nginx -t.
   Expected result:
   ```bash
   nginx php config: the configuration file /etc/nginx/nginx.conf syntax is ok
   nginx php-fpm config: configuration file /etc/nginx/nginx.conf test is successful
   ```
4. Restart the server with `systemctl restart nginx`.
5. Done!

# Deployment Issues
- If you encounter permission errors with files/folders, try running chmod on the folder that needs permission, for example,
```bash
chmod -R 777 ./storage ./bootstrap
```
