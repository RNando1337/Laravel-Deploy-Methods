# Tutorial

Steps:
1. Start by uploading your Laravel application outside the web root directory. For instance, if the web root directory is (~/public_html or etc), place your Laravel application outside of it. The folder structure should resemble the following:

```
   ├── public_html (web root directory)
   │   ├── any folder..
   │   │   └── any files
   │   └── any file
   └── your_laravel_application
       ├── public
       ├── app
       ├── routes
       └── etc
```

2. Once you've created the Laravel application folder, the next step is to create a symlink to mirror the Laravel public application into the web root directory. Use the following command to create the symlink:

```
ln -s ~/your_laravel_application/public/ ~/public_html
```

3. After creating the symlink, make sure to check for the .env file and perform a composer install. If you forgot to upload the vendor or .env file during the Laravel application upload, or if the vendor and .env files were ignored when pulling from Git, carefully review your Laravel application's files and folders.
4. After that, change the permissions for the public, storage, and bootstrap folders using commands like the following:

```
   chmod 755 public/
   chmod 777 -R storage/ bootstrap/
```

5. You're done!

# Deployment Issues

1. If you encounter 404 errors for certain menus/routes, ensure that the .htaccess file has been symlinked in the web root directory (~/public_html or etc). It's possible that this .htaccess file hasn't been symlinked yet.

```
ln -s ~/your_laravel_folder/public/.htaccess ~/web_root_directory
```
2. If your Laravel application uses symbolic links for the Laravel storage, don't forget to symlink `~/public/storage` to the web root directory (`~/public_html or etc`). You can use the following command if it hasn't been symlinked already:

```
  ln -s ~/your_laravel_folder/public/storage ~/web_root_directory
```
