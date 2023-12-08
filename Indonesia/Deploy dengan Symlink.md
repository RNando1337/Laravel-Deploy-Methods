# Tutorial

Langkah-langkah:
1. Mulailah dengan mengunggah aplikasi Laravel Anda di luar direktori akar web. Misalnya, jika direktori akar web adalah (~/public_html atau sebagainya), tempatkan aplikasi Laravel Anda di luar direktori tersebut. Struktur folder harus seperti berikut:
```
   ├── public_html (direktori root web)
   │   ├── folder apa pun..
   │   │   └── file-file apa pun
   │   └── file apa pun
   └── aplikasi_laravel_anda
       ├── public
       ├── app
       ├── routes
       └── dll
```
2. Setelah Anda membuat folder aplikasi Laravel, langkah berikutnya adalah membuat symlink untuk mencerminkan aplikasi publik Laravel ke dalam direktori akar web. Gunakan perintah berikut untuk membuat symlink:

```
ln -s ~/aplikasi_laravel_anda/public/ ~/public_html
```

3. Setelah membuat symlink, pastikan untuk memeriksa file .env dan menjalankan composer install. Jika Anda lupa mengunggah vendor atau file .env saat mengunggah aplikasi Laravel, atau jika file vendor dan .env diabaikan saat pull dari Git, periksa dengan teliti file dan folder aplikasi Laravel Anda.
4. Setelah itu, ubah izin untuk folder public, storage, dan bootstrap menggunakan perintah seperti berikut:

```
   chmod 755 public/
   chmod 777 -R storage/ bootstrap/
```

5. Selesai!

# Daftar Masalah Deploy

1. Jika mengalami masalah ketika beberapa menu/rute menghasilkan kesalahan 404 Not Found, pastikan file .htaccess sudah di symlink dalam direktori root web (~/public_html atau lainnya), mungkin file .htaccess ini belum di symlink. Eksekusi perintah berikut : 
```
ln -s ~/folder_laravel_anda/public/.htaccess ~/direktori_root_web
```
2. Jika aplikasi Laravel Anda menggunakan symbolic link untuk penyimpanan Laravel, jangan lupa untuk symlink `~/public/storage` ke dalam direktori root web (`~/public_html atau lainnya`). Anda dapat menggunakan perintah berikut jika belum dilakukan symlink:
```
ln -s ~/folder_laravel_anda/public/storage ~/direktori_root_web
```
