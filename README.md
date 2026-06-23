# Lab7web-praktikum-1-7

# NAMA: LOLA SEFTYLIANI
# KELAS:I24ID
# NIM:312410339
# MATKUL: PEMROGRAMAN WEB 2

# DOUMENTASI LENGKAP PRAKTIKUM PEMOGRAMAN WEB 2

## Analisis Struktur Modul Praktikum

## Modul 1: Fondasi MVC dan Routing

Pada tahap awal praktikum, fokus utama adalah memahami konsep dasar Framework CodeIgniter 4 dengan menerapkan pola arsitektur Model-View-Controller (MVC) serta mekanisme routing. Proses yang terjadi dimulai ketika pengguna mengakses suatu URL, kemudian file **Routes.php** akan mengarahkan permintaan tersebut ke **Controller** yang sesuai. Selanjutnya, Controller akan memproses permintaan dan menampilkan halaman melalui **View**.

Implementasi pada modul ini dilakukan dengan membuat **Controller Page.php** yang berfungsi untuk menangani halaman statis seperti Home, About, dan Contact. Melalui modul ini dipahami bahwa logika bisnis sebaiknya ditempatkan pada Controller atau Model, bukan di dalam View, sehingga struktur aplikasi menjadi lebih terorganisir dan mudah dipelihara.

## Modul 2: CRUD dan Interaksi Database

Modul ini berfokus pada pengelolaan data secara dinamis menggunakan database MySQL. Untuk menghubungkan aplikasi dengan tabel database, dibuat **ArtikelModel.php** yang berperan sebagai perantara antara aplikasi dan tabel artikel.

Fitur yang diimplementasikan meliputi operasi CRUD (Create, Read, Update, Delete). Fitur Create digunakan untuk menambahkan data artikel baru melalui formulir input. Fitur Read berfungsi menampilkan data dari database ke dalam tabel HTML. Fitur Update digunakan untuk mengubah data yang sudah ada berdasarkan ID tertentu, sedangkan fitur Delete digunakan untuk menghapus data secara permanen dari database.

Selain itu, dilakukan konfigurasi koneksi database melalui file **.env** agar aplikasi dapat berkomunikasi dengan database MySQL secara optimal.

## Modul 3: Templating (View Layout dan View Cell)

Pada modul ini diterapkan konsep **DRY (Don't Repeat Yourself)** untuk mengurangi penulisan kode yang berulang. Implementasi dilakukan dengan menggunakan **View Layout**, yaitu membuat satu file induk bernama **layout/main.php** yang berisi struktur utama halaman. Halaman lain hanya perlu mengisi bagian konten menggunakan metode **$this->extend()** dan **$this->section()**.

Selain itu, digunakan **View Cell** untuk membuat komponen yang bersifat modular, seperti komponen **ArtikelTerkini**. Komponen ini dapat dipanggil pada berbagai halaman tanpa perlu menuliskan ulang query database pada setiap Controller. Dengan pendekatan ini, pemeliharaan kode menjadi lebih mudah karena perubahan pada bagian Header atau Footer cukup dilakukan pada satu file saja.

## Modul 4: Autentikasi dan Security Filter

Modul ini bertujuan untuk meningkatkan keamanan aplikasi dengan menerapkan sistem autentikasi dan filter akses. Proses login dilakukan dengan memvalidasi username dan password pengguna menggunakan Session.

Untuk membatasi akses ke halaman tertentu, dibuat **AuthFilter.php**. Filter ini akan memeriksa status login pengguna sebelum mengakses halaman admin. Jika pengguna belum melakukan login dan mencoba mengakses halaman admin, sistem secara otomatis akan mengarahkan pengguna kembali ke halaman login.

Sebagai pendukung proses autentikasi, dibuat tabel **user** pada database yang berfungsi menyimpan data kredensial administrator.

## Modul 5: Optimasi User Experience (Pagination dan Searching)

Modul terakhir berfokus pada peningkatan kenyamanan pengguna saat mengakses data dalam jumlah besar. Implementasi **Pagination** dilakukan dengan mengganti metode **findAll()** menjadi **paginate(10)** sehingga data ditampilkan secara bertahap sebanyak 10 data per halaman. Teknik ini membantu mengurangi beban browser dan meningkatkan performa aplikasi.

Selain itu, ditambahkan fitur **Searching** menggunakan metode **like()** pada query SQL untuk melakukan pencarian artikel berdasarkan kata kunci yang dimasukkan pengguna. Agar kata kunci pencarian tetap tersimpan ketika pengguna berpindah halaman, digunakan metode **pager->only(['q'])**. Dengan demikian, hasil pencarian tetap konsisten meskipun pengguna berpindah ke halaman berikutnya.
