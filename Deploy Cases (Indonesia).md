# Daftar Masalah Deply

1. Jika mengalami masalah ketika beberapa menu/rute menghasilkan kesalahan 404 Not Found, pastikan file .htaccess sudah di symlink dalam direktori root web (~/public_html atau sebagainya), mungkin file .htaccess ini belum di symlink. Eksekusi perintah berikut : 
```
ln -s ~/folder_laravel_anda/public/.htaccess ~/direktori_root_web
```
2. Jika aplikasi Laravel Anda menggunakan symbolic link untuk penyimpanan Laravel, jangan lupa untuk symlink ~/public/storage ke dalam direktori root web (~/public_html atau sebagainya). Anda dapat menggunakan perintah berikut jika belum dilakukan symlink:
```
ln -s ~/folder_laravel_anda/public/storage ~/direktori_root_web
```
