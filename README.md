# Pemograman Web2 Pertemuan 9

## Profil
| #               | Biodata                      |
| --------------- | ---------------------------- |
| **Nama**        | M. AKMAL AL ABDILAH          |
| **NIM**         | 312110034                    |
| **Kelas**       | TI.21.A.1                    |
| **Mata Kuliah** | Pemrograman Mobile 2         |




<p>Menu about</P>

![Gambar 1](screenshoot/1.JPG)


<p>Menu artikel</P>

![Gambar 2](screenshoot/2.JPG)

<p>Menu kontak</P>

![Gambar 3](screenshoot/3.JPG)




<p>
Catatan yang di atas merupakan gambar harsil dari run dan prosesnya penjelasanya ada di bawah
</p>


<p>
 Dan bagaimana cara untuk membuatnya mari saya jelaskan langkah - langkanhya silakan baca di bawah ini 
</p>



**Instruksi Praktikum**<br>
1. Persiapkan text editor misalnya VSCode.
2. Buat folder baru dengan nama **lab11_php_ci** pada docroot webserver **(htdocs)**
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

**Langkah-langkah Praktikum**<br>
**Persiapan**<br>
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi 
pada webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan 
pengembangan Codeigniter 4.
Berikut beberapa ekstensi yang perlu diaktifkan:
• php-json ekstension untuk bekerja dengan JSON;
• php-mysqlnd native driver untuk MySQL;
• php-xml ekstension untuk bekerja dengan XML;
• php-intl ekstensi untuk membuat aplikasi multibahasa;
• libcurl (opsional), jika ingin pakai Curl.<br>

Untuk mengaktifkan ekstentsi tersebut, melalu **XAMPP Control Panel**, pada bagian 
Apache **klik Config -> PHP.ini**
Untuk menjalankan MySQL Server dari menu XAMPP Contol.
![Gambar 4](screenshoot/4.JPG)

Gambar 01. Konfigurasi PHP

Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan 
diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.

![Gambar 5](screenshoot/5.JPG)!
![Gambar 6](screenshoot/6.JPG)

Gambar 02. Ekstensi PHP

**`Instalasi Codeigniter 4`**

Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara 
manual dan menggunakan **composer**. Pada praktikum ini kita menggunakan cara 
manual.<br>
• Unduh **Codeigniter** dari website https://codeigniter.com/download<br>
• Extrak file zip Codeigniter ke direktori **htdocs/lab11_ci**.<br>
• Ubah nama direktory **framework-4.x.xx** menjadi **ci4**.<br>


![Gambar 7](screenshoot/7.JPG)

Gambar 03. Direktory framework-4 ci4

• Buka browser dengan alamat **http://localhost/lab11_php_ci/ci4/public/**

![Gambar 8](screenshoot/8.JPG)

Gambar 04. Tampilan Codeigniter4

**`Menjalankan CLI (Command Line Interface)`**

Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk 
mengakses CLI buka terminal/command prompt. 

![Gambar 9](screenshoot/9.JPG)

Gambar 05. Tampilan Command Prompt

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat **(xampp/htdocs/lab11_php_ci/ci4/)** 
Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:

~~~
php spark
~~~

![Gambar 10](screenshoot/10.JPG)

Gambar 06. Perintah CLI

lalu jalankan perintah

~~~
php spark serve
~~~

**`Mengaktifkan Mode Debugging`**<br>

Codeigniter 4 menyediakan fitur **debugging** untuk memudahkan developer untuk 
mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.

**Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan
pesan kesalahan seperti berikut.**

![Gambar 11](screenshoot/11.JPG)

Gambar 07. CI Error

Cara mengaktifkannya dengan mengubah nama file **env** menjadi **.env** kemudian buka filenya dan ubah nilai **CI_ENVIRONMENT** menjadi **development.**

![Gambar 12](screenshoot/12.JPG)

Gambar 08. Konfigurasi CI

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file
**app/Controller/Home.php** hilangkan titik koma pada akhir kode.

![Gambar 13](screenshoot/13.JPG)

Gambar 09. Kode Home

Buka browser : http://localhost:8080

![Gambar 14](screenshoot/14.JPG)

Gambar 10. Error

**Membuat Route Baru.**

Tambahkan kode berikut di dalam **Routes.php**
~~~
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
~~~
![Gambar 15](screenshoot/15.JPG)

Gambar 11. Gambar add app config Routes.php

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan
perintah berikut.

`php spark routes`

![Gambar 16](screenshoot/16.JPG)

Gambar 12. Tampilan CLI

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url
http://localhost:8080/about

![Gambar 17](screenshoot/17.JPG)

Gambar 13. Tampilan error page.

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page
tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih
dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

**Membuat Controller**

Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama **page.php** di dalam direktori Controller (/app/Controllers).<br>
Pada direktori Controller kemudian isi kodenya seperti berikut.
~~~
<?php
namespace App\Controllers;
class Page extends BaseController
{
public function about()
{
echo "Ini halaman About";
}
public function contact()
{
echo "Ini halaman Contact";
}
public function faqs()
{
echo "Ini halaman FAQ";
}
}
~~~
![Gambar 18](screenshoot/18.JPG)

Gambar 14. Code Controller Page.php

Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaitu halaman
sudah dapat diakses.

![Gambar 19](screenshoot/19.JPG)

Gambar 14. Tampilan Halaman About

**Auto Routing**
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status
autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true
menjadi false.
~~~
$routes->setAutoRoute(true);
~~~
Tambahkan method baru pada Controller Page seperti berikut.
~~~
public function tos()
{
echo "ini halaman Term of Services";
}
~~~

Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan
alamat: http://localhost:8080/page/tos

![Gambar 20](screenshoot/20.JPG)

Gambar 15. Tampilan autoroute

**Membuat View**

Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file
baru dengan nama **about.php** pada direktori view **(app/view/about.php)** kemudian isi
kodenya seperti berikut.
~~~
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title><?= $title; ?></title>
</head>
<body>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
</body>
</html>
~~~
![Gambar 21](screenshoot/21.JPG)

Gambar 16. Code app view about.php

Ubah **method about** pada class **Controller Page** menjadi seperti berikut:
~~~
public function about()
{
return view('about', [
'title' => 'Halaman Abot',
'content' => 'Ini adalah halaman abaut yang menjelaskan tentang isi
halaman ini.'
]);
}
~~~
![Gambar 22](screenshoot/22.JPG)

Gambar 17. Code Controller Page

Kemudian lakukan refresh pada halaman tersebut.

![Gambar 23](screenshoot/23.JPG)

Gambar 18.Halaman about

**Membuat Layout Web dengan CSS**

Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada
codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset
css dan javascript terletak pada direktori **public**.<br>
Buat file css pada direktori public dengan nama **style.css** (copy file dari praktikum
**lab4_layout**). Kita akan gunakan layout yang pernah dibuat pada praktikum 4.

![Gambar 24](screenshoot/24.JPG)

Gambar 19.Direktori asset

Kemudian buat folder **template** pada direktori **view** kemudian buat file **header.php** dan
**footer.php**<br>
File **app/view/template/header.php**<br>
~~~
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title><?= $title; ?></title>
<link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
<div id="container">
<header>
<h1>Layout Sederhana</h1>
</header>
<nav>
<a href="<?= base_url('/');?>" class="active">Home</a>
<a href="<?= base_url('/artikel');?>">Artikel</a>
<a href="<?= base_url('/about');?>">About</a>
<a href="<?= base_url('/contact');?>">Kontak</a>
</nav>
<section id="wrapper">
<section id="main">
~~~
![Gambar 25](screenshoot/25.JPG)

Gambar 20.Code header.php

File **app/view/template/footer.php**
~~~
</section>
<aside id="sidebar">
<div class="widget-box">
<h3 class="title">Widget Header</h3>
<ul>
<li><a href="#">Widget Link</a></li>
<li><a href="#">Widget Link</a></li>
</ul>
</div>
<div class="widget-box">
<h3 class="title">Widget Text</h3>
<p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada
tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis.
Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
</div>
</aside>
</section>
<footer>
<p>&copy; 2021 - Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>
~~~
![Gambar 26](screenshoot/26.JPG)

Gambar 21.Code footer.php

Kemudian ubah file **app/view/about.php** seperti berikut.
~~~
<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>
~~~
![Gambar 27](screenshoot/27.JPG)

Gambar 22.Code about.php

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![Gambar 28](screenshoot/28.JPG)

Gambar 22.Tampilan web about

<hr>

**`Pertanyaan dan Tugas`**

Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga
semua link pada navigasi header dapat menampilkan tampilan dengan layout yang
sama.
<hr>

 >**Jawab**
 
 
Di atas sudah kita buat Route jadi kita tinggal.
Tambahkan kode **Route artikel** di dalam **Routes.php**

![Gambar 29](screenshoot/29.JPG)

Gambar 23.add_Routes_artikel

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan
perintah berikut.

`php spark routes`

![Gambar 30](screenshoot/30.JPG)

Gambar 24.add_Routes_artikel_CLI

Selanjutnya kita buat Buat dan tambahkan file
baru dengan nama **artikel.php dan contact.php** di **htdocs\lab11_php_ci\ci4\app\Views**


<p>
Oke segitu saja diri saya kurang lebih saya mohon dan saya ucapkan !
</p>

<img src="https://user-images.githubusercontent.com/91085882/222731693-24383140-7623-4e7a-a528-6621380b7be8.gif">