# Tutorial

Langkah-Langkah :
1. Pastikan php, php-fpm, dan php-mysql sudah terinstal pada aplikasimu, untuk mengeceknya dapat menggunakan command line berikut :
   ```php
   1. apt search php[versi php mu], misal apt search php8.1 << tujuannya untuk mengecek apakah paket tersedia pada repositori di sistem operasi yang kamu gunakan. Jika tidak ada coba gunakan repositori publik untuk proses instalasi.
   2. apt-get install php8.1 -y << ini adalah contoh command untuk menginstall php dengan versi 8.1, kamu dapat menysesuaikan kebutuhan dari versi php dari laravel yang akan kamu gunakan.

   Lakukan langkah pada step 2 untuk menginstall php-mysql dan php-fpmnya
   Catatan : apt-get install [paket yang akan kamu install] -y
   ```
   Jika sudah diinstalasi, cek apakah php-fpm sudah dijalankan dengan cara dibawah ini 
   ```
   systemctl status php[versi php]-fpm

   Ekspektasi hasil :
   php8.1-[versi php].service - PHP [versi php] FastCGI Process Manager FPM for [Server OS]
      Loaded: loaded (/lib/systemd/system/php[versi phpmu]-fpm.service)
      Active: active (php-fpm running)
   ```
   Jika belum berjalan coba running dengan `systemctl start php-fpm`
2. Update konfigurasi default dari Nginx. Secara default file konfigurasi Nginx berada pada path `/etc/nginx/sites-available/` dengan nama file `default`, jadi lakukan update konfigurasi file tersebut dengan text editor, untuk konfigurasi saya menggunakan perintah nano : `nano /etc/nginx/sites-available/default`
   Contoh Konfugrasi :
   <img width="807" alt="gambar" src="https://github.com/RNando1337/Laravel-Deploy-Methods/assets/60562868/06a6b8d2-9e11-44f1-86e4-c71ecebbe7cd">
Pastikan kode seperti yang saya tandai pada gamabar diatas tidak tidak dimatikan/dikomentar.
Penjelasan :
- Poin No. 1 merupakan kode untuk mengatur direktori root dari server. Jadi arahakan folder `/publik` dari aplikasi laravel kamu untuk dijadikan root direktori server
- Poin No. 2 merupakan blok konfigurasi untuk mengatur cara server menangani permintaan ke URL utama (root),
  ```bash
  location / {
       try_files $uri $uri/ /index.php$is_args$args;
   }
  ```
  Dimana kode diatas mencoba menemukan file yang sesuai dengan URI yang diminta jika tidak ditemukan baik direktori atau apapun itu akan diarahkan ke `index.php` dengan menyertakan argumen yang mungkin ada
- Poin No. 3,4,5 secara default masih dimatikan/atau dikomentari jadi hapus tanda pagar yang ada didepan kode yang saya tandai tersebut.
  ```bash
   fastcgi_pass unix:/var/run/php/php[versi php mu]-fpm.sock;
  ```
  sesuaikan versi dari php soket unik yang kamu gunakan
- Poin No. 6, merupakan blok kode yang melarang akses ke file .htaccess, hal ini bertujuan untuk mencegah akses tidak sah ke file konfigurasi yang ada di folder public atau sebagainya. 
3. Setelah selesai mengupdate konfigurasi, langkah selanjutnya cek konfigurasi apakah ada error atau tidak dengan cara melakukan command `nginx -t`
Ekspektasi hasil : 
```bash
nginx php config: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx php-fpm config: configuration file /etc/nginx/nginx.conf test is successful
```
4. Kemudian jalankan ulang server dengan cara `systemctl restart nginx`
5. Selesai!

# Masalah Deploy
- Jika kamu menghadapi error permission dari file/folder, coba untuk melakukan chmod dari folder yang harus diberikan permission misalnya
  ```bash
  chmod -R 777 ./storage ./bootstrap
  ```
