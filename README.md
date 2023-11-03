# Laravel Deploy With Symlink Documentation (English - Indonesia)

## English Documentation
Steps:
1. Start by uploading your Laravel application outside the web root directory. For instance, if the web root directory is ~/public_html, place your Laravel application outside of it. The folder structure should resemble the following:

```
   ├── public_html (web root directory)
   │   ├── any folder..
   │   │   ├── any files
   │   ├── any file
   └── your_laravel_application
       ├── public
       ├── app
       ├── routes
       ├── etc
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

## Indonesian Documentation

Langkah-langkah:
1. Mulailah dengan mengunggah aplikasi Laravel Anda di luar direktori akar web. Misalnya, jika direktori akar web adalah ~/public_html, tempatkan aplikasi Laravel Anda di luar direktori tersebut. Struktur folder harus seperti berikut:
```
   ├── public_html (direktori root web)
   │   ├── folder apa pun..
   │   │   ├── file-file apa pun
   │   ├── file apa pun
   └── aplikasi_laravel_anda
       ├── public
       ├── app
       ├── routes
       ├── dll
```
2. Setelah Anda membuat folder aplikasi Laravel, langkah berikutnya adalah membuat symlink untuk mencerminkan aplikasi publik Laravel ke dalam direktori akar web. Gunakan perintah berikut untuk membuat symlink:

```
ln -s ~/your_laravel_application/public/ ~/public_html
```

3. Setelah membuat symlink, pastikan untuk memeriksa file .env dan menjalankan composer install. Jika Anda lupa mengunggah vendor atau file .env saat mengunggah aplikasi Laravel, atau jika file vendor dan .env diabaikan saat menarik dari Git, periksa dengan teliti file dan folder aplikasi Laravel Anda.
4. Setelah itu, ubah izin untuk folder public, storage, dan bootstrap menggunakan perintah seperti berikut:

```
   chmod 755 public/
   chmod 777 -R storage/ bootstrap/
```

5. Selesai!

# Deploy Cases Solution
- If you're facing a problem when deploying a Laravel application, you can read the solution to these deployment cases by clicking this [link](https://github.com/RNando1337/Laravel-Deploy-Symlink/blob/cb9ae20f3025befe12b694e3927dba1025e25c51/Deploy%20Cases.md).

- Jika Anda menghadapi masalah saat mendeploy aplikasi Laravel, Anda dapat membaca solusi kasus-kasus deploy ini dengan mengklik [tautan](https://github.com/RNando1337/Laravel-Deploy-Symlink/blob/cb9ae20f3025befe12b694e3927dba1025e25c51/Deploy%20Cases.md) ini.
