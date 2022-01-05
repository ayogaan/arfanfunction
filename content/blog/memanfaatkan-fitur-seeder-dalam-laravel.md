---
title: "Memanfaatkan Fitur Seeder Laravel"
date: 2021-11-03T10:07:47+06:00
draft: false

# post thumb
image: "images/featured-post/post-3.jpg"

# meta description
description: "this is meta description"

# taxonomies
categories: 
  - "Web Programming"
tags:
  - "Laravel"
  - "PHP"


# post type
type: "post"
---

Belum lama ini saya mendapatkan projek sistem informasi dengan menggunakan framework laravel dan dalam pengerjaanya terdapat banyak sekali nilai default yang harus saya simpan di database,yang tentunya akan menguras waktu dan tenaga apabila saya menginputkanya satu persatu, untung saja ditengah tengah proses pengerjaan saya mengingat ada satu fitur di laravel yang dapat memudahkan pekerjaan ini. yepp.. fitur tersebut adalah seeder.

sebenarnya seeder ini bukan hanya berfungsi untuk menginput data default yang ada di database melainkan bisa juga untuk mengisi data dummy atau data testing pada prosess pengembangan aplikasi, namun saya sendiri jarang menggunakanya wkwkwkwkw.
yah langsung saja kita coba membuat sebuah seeder

### Perisapan
##### buat file seeder
disini saya akan membuat seeder untuk table category
untuk membuat nya kita dapat mengetikan command dibawah ini di terminal

```javascript
pip artisan make:seeder CategorySeeder
```

command tersebut berfungsi untuk mengenerate template file seeder yang akan kita edit dengan nama file CategorySeeder, nah lalu buka file nya dan mari kita edit, file nya sendiri terdapat pada folder database/seeder/

```
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use App\Models\Category;
class CategorySeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        
    }
}

```

nah selanjutnya kita akan mengeditnya sebagai berikut

kode diatas adalah kode sederhana yang berfungsi untuk menginput item item yang ada di array kedalam database didalam table category
