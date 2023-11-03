# Cases List

1. If facing some menus/routes got 404 error not found, make sure that .htaccess file already symlink in web root directory (~/public_html or etc), maybe this .htaccess file isn't symlink yet.
```
ln -s ~/your_laravel_folder/public/.htaccess ~/web_root_directory
```
2. If your laravel application use symbolic link for laravel storage don't forget to symlink ~/public/storage into web root directory (~/public_html or etc). you can use this command symlink isn't already symlink :
```
  ln -s ~/your_laravel_folder/public/storage ~/web_root_directory
```
