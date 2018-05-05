# LEARN SASS

## INSTALL SASS


Sebelum menginstall `SASS` yang harus kita lakukan adalah menginstall `Ruby` jalan kan perintah berikut di terminal

> sudo apt-get install ruby-full  

kemudian install sass dengan menjalankan perintah berikut

> sudo gem install sass

untuk mengecek jalankan perintah

> sass -v

## Perintah di terminal

Buat folder project misal `belajar-sass` selanjutnya buat file bernama `style.scss` kemudian buka terminal dan masuk ke folder project. Kemudian jalankan perintah di bahawah ini untuk menjalakan sass

> sass style.scss output.css

secara otomatis akan tebuat file `output.css` sebagai output dari `style.scss` tetapi jika ada perubahan di file `style.scss` file output tidak akan berubah dan harus menjalankan perintah diatas untuk merender ulang. Untuk mengatasi masalah ini jalankan perintah

> sass --watch style.scss:output.css

Maka otomatis setiap ada perubahan di file `style.scss` dan disimpan file `output.css` akan berubah seperti struktur `style.scss`. Tapi jika kita mengedit lebih dari satu file maka file yang satu tidak akan ada perubahan. Misal ada file `style.scss` dan `style.admin.css` saat mengedit file `style.scss` maka file `output.css` akan berubah sedangkan jika mengedit file `style.admin.css` tidak akan berubah. Karena perintah diatas hanya menunjuk file `style.scss` sebagai file yang diedit dan `output.css` sebagai hasil dari `style.scss`. Jika melakukan lebih dari satu pengeditan file `.scss`.

Buat folder dengan nama `sass` dan `css`. pindahkan file `style.scss` kedalam folder `sass` otomatis file `output.css` akan terhapus. Jalankan perintah berikut agar bisa otomatis merender file di dalam folder `sass` dan outputnya di folder `css`.

> sass --watch sass:css  

Maka secara otomatis akan tebuat file `style.css` di folder `css`. Pindahkan file `style.admin.scss` maka otomatis akan tebuat file `style.admin.css` di folder `css`.

Untuk membuat file css lebih mudah dibaca tambahkan style di sass kita ada 4 style yang digunakan di dalam sass yaitu:

1. Nested

Nested adalah style default yang digunakan sass.

> sass --watch sass:css --style nested

2. Compact

Compact adalah style menjadikan penulisan css perbaris
```css
body { color: red; }

.box1 { -webkit-transition: 320ms ease; -moz-transition: 320ms ease; -ms-transition: 320ms ease; -o-transition: 320ms ease; transition: 320ms ease; }
```

> sass --watch sass:css --style compact

3. Compressed

Compressed adalah membuat file menjadi minified atau satubaris css

> sass --watch sass:css --style comressed

4. Expanded

Expanded adalah style seperti penulisan css manual yang rapi seperti tidak ada nested dan tutup kurung kurawal di baris baru. Expanded adalah style yang paling mudah dibaca

> sass --watch sass:css --style nested

## Script yang digunakan dalam css






// test
