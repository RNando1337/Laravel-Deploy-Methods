# Tutorial

Langkah-Langkah :
1. Pastikan php, php-fpm, dan php-mysql sudah terinstal pada aplikasimu, untuk mengeceknya dapat menggunakan command line berikut :
   ```
   1. apt search php[versi php mu], misal apt search php8.1 << tujuannya untuk mengecek apakah paket tersedia pada repositori di sistem operasi yang kamu gunakan. Jika tidak ada coba gunakan repositori publik untuk proses instalasi.
   2. apt-get install php8.1 -y << ini adalah contoh command untuk menginstall php dengan versi 8.1, kamu dapat menysesuaikan kebutuhan dari versi php dari laravel yang akan kamu gunakan.

   lakukan langkah yang sama pada step 2 untuk menginstall php-mysql dan php-fpmnya
   Catatan : apt-get install [paket yang akan kamu install] -y
   ```
   Jika sudah diinstalasi, cek apakah php-fpm sudah dijalankan dengan cara dibawah ini 
   ```
   systemctl status php8.1-fpm

   Ekspetasi hasil :
   php8.1-[versi phpmu].service - PHP 8.1 FastCGI Process Manager FPM for [Server OS]
      Loaded: loaded (/lib/systemd/system/php[versi phpmu]-fpm.service)
      Active: active (php-fpm running)
   ```
   Jika belum berjalan coba running dengan `systemctl start php-fpm`
2. 
