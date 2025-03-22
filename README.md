# PHP Framework (Codeigniter4)
| Praktikum 1-3  |  Pemrograman Web 2  
|-------|---------
| NIM   | 312310632
| Nama  | Fakhri Afif
| Kelas | TI.23.A6
| Dosen |  Agung Nugroho, S.Kom., M.Kom.

## Praktikum 1

### Pertanyaan dan Tugas

- Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua
link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

#### Controller/Page.php
```
<?php

namespace App\Controllers;

use App\Models\ArtikelModel;

class Page extends BaseController
{
    public function about()
    {
        return view('about', [
            'title'   => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
        ]);
    }

    public function contact()
    {
        $data = [
            'title'   => 'Halaman Kontak',
            'email'   => 'taufikhidayat3621@gmail.com',
            'alamat'  => 'Sukatani, Cikarang',
            'telepon' => '+62 812-8627-5726'
        ];

        return view('contact', $data);
    }

    public function faqs()
    {
        echo "Ini halaman FAQ";
    }

    public function tos()
    {
        echo "Ini halaman Term of Services";
    }

    // Method untuk menampilkan daftar artikel
    public function artikel()
    {
        $artikelModel = new ArtikelModel();
        
        // Ambil semua artikel dan urutkan dari yang terbaru
        $data['artikel'] = $artikelModel->orderBy('id', 'DESC')->findAll();

        return view('artikel/index', $data);
    }
}
```
### Halaman About

![image](ss/ss1.png)

### Halaman Kontak

![image](ss/ss2.png)





## Praktikum 2
### Pertanyaan dan Tugas
- Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan improvisasi

#### Konfigurasi koneksi database di file (.env)

- Hapus (#) pada text konfigurasi database(.env)

![image](ss/ss3.png)


#### Membuat Database: Studi Kasus Data Artikel

- Buat database
  
```
CREATE DATABASE lab_ci4;
```

- Buat Table

```
CREATE TABLE artikel (
 id INT(11) auto_increment,
 judul VARCHAR(200) NOT NULL,
 isi TEXT,
 gambar VARCHAR(200),
 status TINYINT(1) DEFAULT 0,
 slug VARCHAR(200),
 PRIMARY KEY(id)
);
```

- Membuat Model file baru pada direktori app/Models dengan nama ArtikelModel.php

![image](ss/ss4.png)

- Membuat Controller dengan nama Artikel.php pada direktori app/Controllers.

![image](ss/ss5.png)

- Membuat View, buat direktori baru dengan nama artikel pada direktori app/views, kemudian buat file baru
dengan nama index.php.

![image](ss/ss6.png)

- Selanjutnya buka browser kembali, dengan mengakses url http://localhost:8080/artikel

![image](ss/ss7.png)

- Membuat Tampilan Detail Artikel, tambahkan fungsi baru pada Controller Artikel dengan nama view().

![image](ss/ss8.png)

- Membuat View Detail, buatview baru untuk halaman detail dengan nama app/views/artikel/detail.php

![image](ss/ss9.png)

- Membuat Routing untuk artikel detail, buka Kembali file app/config/Routes.php, kemudian tambahkan routing untuk artikel detail

![image](ss/ss10.png)

- Membuat Menu Admin untuk proses CRUD data artikel. Buat method baru pada Controller
Artikel dengan nama admin_index().

![image](ss/ss11.png)

- Selanjutnya buat view di app/Views/artikel untuk tampilan admin dengan nama admin_index.php

![image](ss/ss12.png)

- Tambahkan routing untuk menu admin seperti berikut:

![image](ss/ss13.png)

- Akses menu admin dengan url http://localhost:8080/admin/artikel

![image](ss/ss14.png)

- Menambah Data Artikel, tambahkan fungsi/method baru pada Controller Artikel dengan nama add()

![image](ss/ss15.png)

- Kemudian buat view untuk form tambah dengan nama form_add.php

![image](ss/ss16.png)

- tampilan di http://localhost:8080/admin/artikel/add

![image](ss/ss17.png)

- Mengubah Data, tambahkan fungsi/method baru pada app/Controller/Artikel dengan nama edit()

![image](ss/ss18.png)

- Kemudian buat file view di lokasi file Views/artikel/form_edit.php

![image](ss/ss19.png)

- tampilan di http://localhost:8080/admin/artikel/edit/1

![image](ss/ss20.png)

- Menghapus data, tambahkan fungsi/method baru pada app/Controller/Artikel dengan nama delete().

![image](ss/ss21.png)


## Praktikum 3
### Pertanyaan dan Tugas

- Sesuaikan data dengan praktikum sebelumnya, perlu melakukan perubahan field pada
database dengan menambahkan tanggal agar dapat mengambil data artikel terbaru.

- Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan
improvisasi.

- Apa manfaat utama dari penggunaan View Layout dalam pengembangan aplikasi?

- Jelaskan perbedaan antara View Cell dan View biasa.

- Ubah View Cell agar hanya menampilkan post dengan kategori tertentu.


### Membuat Layout Utama

- Buat folder layout di dalam app/Views/

- Buat file main.php di dalam folder layout dengan kode berikut:

![image](ss/ss22.png)

### Modifikasi File View
- Ubah app/Views/home.php agar sesuai dengan layout baru:

![image](ss/ss23.png)

### Membuat Class View Cell

- Buat folder Cells di dalam app/

- Buat file ArtikelTerkini.php di dalam app/Cells/ dengan kode berikut:

![image](ss/ss24.png)

### Membuat View untuk View Cell

- Buat folder components di dalam app/Views/

- Buat file artikel_terkini.php di dalam app/Views/components/ dengan kode berikut:

![image](ss/ss25.png) 

## Manfaat Utama Penggunaan View Layout dalam Pengembangan Aplikasi

Salah satu keuntungan utama dalam menggunakan View Layout adalah meningkatkan keteraturan dan kemudahan dalam pengelolaan kode. Dengan adanya View Layout, elemen yang sering digunakan seperti header, footer, atau sidebar hanya perlu dibuat sekali dan dapat digunakan kembali di berbagai halaman. Hal ini tidak hanya mempercepat proses pengembangan tetapi juga memastikan konsistensi tampilan di seluruh aplikasi. Selain itu, jika ada perubahan yang perlu dilakukan, cukup mengedit satu file tanpa harus memperbarui setiap halaman secara terpisah.

## Perbedaan Antara View Biasa dan View Cell

Terdapat perbedaan mendasar antara View biasa dan View Cell dalam penggunaannya:

- **View Biasa** digunakan untuk menampilkan halaman atau bagian dari halaman secara langsung. Biasanya dipanggil dari controller menggunakan `return view('namaview', $data)`. Isi dari View biasa dapat berupa kombinasi HTML dan PHP yang bertugas untuk menampilkan serta mengolah data yang dikirim dari controller.

- **View Cell** lebih fleksibel karena dapat dipanggil di dalam view lain. Komponen ini sangat berguna untuk menampilkan elemen yang sering digunakan kembali, seperti sidebar, widget, atau daftar artikel terbaru. Untuk memanggil View Cell, digunakan sintaks `<?= view_cell('NamaClass::method') ?>`, yang memungkinkan pemuatan data secara langsung tanpa harus melewati controller terlebih dahulu.

Secara sederhana, View biasa lebih cocok untuk menampilkan halaman utama, sedangkan View Cell digunakan untuk memuat bagian kecil dari halaman secara dinamis.




### Ubah View Cell agar hanya menampilkan post dengan kategori tertentu.

- Tampilan di http://localhost:8080/

![image](ss/ss26.png) 

# SELESAI
