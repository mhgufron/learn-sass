# LEARN SASS

## 1. INSTALL SASS


Sebelum menginstall `SASS` yang harus kita lakukan adalah menginstall `Ruby` jalan kan perintah berikut di terminal

> sudo apt-get install ruby-full  

kemudian install sass dengan menjalankan perintah berikut

> sudo gem install sass

untuk mengecek jalankan perintah

> sass -v

## 2. Perintah di terminal

Buat folder project misal `belajar-sass` selanjutnya buat file bernama `style.scss` kemudian buka terminal dan masuk ke folder project. Kemudian jalankan perintah di bahawah ini untuk menjalakan sass

> sass style.scss output.css

secara otomatis akan tebuat file `output.css` sebagai output dari `style.scss` tetapi jika ada perubahan di file `style.scss` file output tidak akan berubah dan harus menjalankan perintah diatas untuk merender ulang. Untuk mengatasi masalah ini jalankan perintah

> sass --watch style.scss:output.css

Maka otomatis setiap ada perubahan di file `style.scss` dan disimpan file `output.css` akan berubah seperti struktur `style.scss`. Tapi jika kita mengedit lebih dari satu file maka file yang satu tidak akan ada perubahan. Misal ada file `style.scss` dan `style.admin.css` saat mengedit file `style.scss` maka file `output.css` akan berubah sedangkan jika mengedit file `style.admin.css` tidak akan berubah. Karena perintah diatas hanya menunjuk file `style.scss` sebagai file yang diedit dan `output.css` sebagai hasil dari `style.scss`. Jika melakukan lebih dari satu pengeditan file `.scss`.

Buat folder dengan nama `sass` dan `css`. pindahkan file `style.scss` kedalam folder `sass` otomatis file `output.css` akan terhapus. Jalankan perintah berikut agar bisa otomatis merender file di dalam folder `sass` dan outputnya di folder `css`.

> sass --watch sass:css  

Maka secara otomatis akan tebuat file `style.css` di folder `css`. Pindahkan file `style.admin.scss` maka otomatis akan tebuat file `style.admin.css` di folder `css`.

Untuk membuat file css lebih mudah dibaca tambahkan style di sass kita ada 4 style yang digunakan di dalam sass yaitu:

__1. Nested__

Nested adalah style default yang digunakan sass.

> sass --watch sass:css --style nested

__2. Compact__

Compact adalah style menjadikan penulisan css perbaris
```css
body { color: red; }

.box1 { -webkit-transition: 320ms ease; -moz-transition: 320ms ease; -ms-transition: 320ms ease; -o-transition: 320ms ease; transition: 320ms ease; }
```

> sass --watch sass:css --style compact

__3. Compressed__

Compressed adalah membuat file menjadi minified atau satubaris css

> sass --watch sass:css --style comressed

__4. Expanded__

Expanded adalah style seperti penulisan css manual yang rapi seperti tidak ada nested dan tutup kurung kurawal di baris baru. Expanded adalah style yang paling mudah dibaca

> sass --watch sass:css --style nested

## 3. Script yang digunakan dalam css

__1. Import__

Import adalah menginclude file. Misal jika memiliki file bernama `style.scss` dan `reset.scss` cukup tuliskan `@import "reset";` di `style.scss` biasanya file yang import/partial memiliki tanda `_` underscore sebelum nama file tersebut misal `_reset.scss` untuk menandakan itu adalah file partial.

__2. Variabel__

Sass memungkinkan kita untuk membuat variabel agar bisa dipanggil kembali. dan jika kita mengubah isi dari variabel itu maka semua properti yang menggunakan variabel itu akan berubah misalnya:

- Input

```sass
    $primary-color: blue; //variabel
    .first-class {
        color: $primary-color;
        font-family: sans-serif;
    }
    .second-class {
        background-color: $primary-color;
    }
```

- Output

```css
    .first-class {
        color: blue;
        font-family: sans-serif;
    }
    .second-class {
        background-color: blue;
    }
```

__3. Operator__

Operator adalah operasi matematika seperti penjumlahan, pengurangan, pembagian dan perkalian misal:

- Input

```scss
    $container: 1000px;

    .half {
        width: $container/2;
    }

```

- Output

```css
    .half {
        width: 500px;
    }
```

__4. Extend__

Extend adalah suatu class memiliki property dan value seperti class yang di extend misal:

- Input

```sass
    .first-class {
        color: blue;
        font-family: sans-serif;
    }
    .second-class {
        @extend .first-class;
        background-color: blue;
    }
```

- Output

```css
    .first-class, .second-class {
        color: blue;
        font-family: sans-serif;
    }
    .second-class {
        background-color: blue;
    }
```

__5. Tanda `&`__

Tanda `&` digunakan untuk mempersingkat penulisan class misalnya:

```scss
    a.link-class { font-family: sans-serif; color: $primary-color;
        &:hover,
        &:focus,
        &:active { color: blue; }
    }
```

- Output

```css
    a.link-class {
      font-family: sans-serif;
      color: #000;
    }
    a.link-class:hover, a.link-class:focus, a.link-class:active {
      color: blue;
    }
```

__6. Function__

Dalam SASS kita juga bisa menggunakan function misalnya jika kita ingin membuat class yang menggunakan pembagian.

- Input

```scss
    @function half-height($first, $second) { // function
        @return $first / $second;
    }
    .half {
        height: half-height(10px,2); // memanggil nama function
    }
```

- Output

```css
    .half {
        height: 5px; /* hasil pembagian 10px dibagi 2 */
    }
```

__7. Mixins__

Mixins mirip seperti function. Mixins digunakan untuk support browser css3 kita bisa menggunakan variabel dan memberi nilai default pada variabel tersebut misal:

- Input

```scss
    @mixin animate-time( $time: 320ms ) { // mixins dengan variabel $time dengan nilai default 320ms
        -webkit-transition: $time ease;
        -moz-transition: $time ease;
        -ms-transition: $time ease;
        -o-transition: $time ease;
        transition: $time ease;
    }

    .box1 {
        @include animate-time; // pemanggilan mixins animate-time dengan nilai default
    }

    .box2 {
        @include animate-time( 500ms ); // pemanggilan mixins animate-time dengan nilai 500ms
    }
```

- Output

```css
.box1 {
  -webkit-transition: 320ms ease;
  -moz-transition: 320ms ease;
  -ms-transition: 320ms ease;
  -o-transition: 320ms ease;
  transition: 320ms ease;
}

.box2 {
  -webkit-transition: 500ms ease;
  -moz-transition: 500ms ease;
  -ms-transition: 500ms ease;
  -o-transition: 500ms ease;
  transition: 500ms ease;
}
```

__8. Loop__

Seperti dalam PHP, Javascript atau bahasa pemrograman lain sass juga memiliki fungsi loop.

__a. For Loop__

For loop memiliki susunan perintah seperti berikut:

> for $var from `<start>` through `<end>` { #code... }

`<start>` dan `<end>` berisi integer yang akan mengulang dari start ke end misal:

- Input

```scss
    @for $space from 1 through 3
    {
        $width: percentage( 1 / $space );

        .column-#{$space}
        {
            width: $width;
        }
    }
```

- Output

```css
    .column-1 {
      width: 100%;
    }

    .column-2 {
      width: 50%;
    }

    .column-3 {
      width: 33.3333333333%;
    }
```

__b. While Loop__

While loop memiliki struktur perintah sebagai berikut:

> @while $var operator(>, <, =>, =<, == ) `<int>` { #code... }

- Input
```scss
    $num: 1;

    @while $num < 3
    {
        $width: percentage( 1 / $num );

        .column-#{$num}
        {
            width: $width;
        }

        $num: $num + 1;
    }
```

- Output

```css
    .column-1 {
      width: 100%;
    }

    .column-2 {
      width: 50%;
    }

    .column-3 {
      width: 33.3333333333%;
    }
```

__c. Each Loop__

Each loop adalah fungsi looping dengan array. Each loop memiliki struktur perintah sebagai berikut:

> @each $key, $value in $array { #code... }

```scss
    $white: #fff;
    $black: #000;
    $primary: #4f4f4f;
    $secondary: #333;

    $colours: (
        'white': $white,
        'black': $black,
        'primary' : $primary,
        'secondary' : $secondary
    );

    @each $colour, $hex in $colours
    {
        .text-#{$colour} {
            color: $hex;
        }
    }
```

- Output

```css
    .text-white {
      color: #fff;
    }

    .text-black {
      color: #000;
    }

    .text-primary {
      color: #4f4f4f;
    }

    .text-secondary {
      color: #333;
    }
```

Copy Right By: [mhgufron](https://mhgufron.github.io)
