# List of Cases

1. If you encounter 404 errors for certain menus/routes, ensure that the .htaccess file has been symlinked in the web root directory (~/public_html or similar). It's possible that this .htaccess file hasn't been symlinked yet.

```
ln -s ~/your_laravel_folder/public/.htaccess ~/web_root_directory
```
2. If your Laravel application uses symbolic links for the Laravel storage, don't forget to symlink ~/public/storage to the web root directory (~/public_html or similar). You can use the following command if it hasn't been symlinked already:

```
  ln -s ~/your_laravel_folder/public/storage ~/web_root_directory
```
