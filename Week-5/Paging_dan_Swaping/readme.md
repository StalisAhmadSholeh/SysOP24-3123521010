## PERBEDAAN PAGING DAN SWAPING

Paging adalah strategi manajemen memori di mana ruang alamat proses dibagi menjadi blok-blok dengan ukuran yang sama,<br>
yang disebut halaman. Ukuran setiap halaman adalah pangkat 2, dan berkisar antara 512 byte dan 8192 byte.<br> 
Besar kecilnya proses kemudian diukur dalam jumlah halaman. Memori utama dibagi menjadi blok-blok kecil berukuran tetap yang disebut frame.<br>
Ukuran setiap frame dijaga sama dengan ukuran halaman agar memori utama dapat dimanfaatkan secara optimal dan untuk menghindari fragmentasi eksternal.<br>
Paging pada dasarnya adalah teknik alokasi memori yang menggunakan teknik manajemen memori yang tidak bersebelahan.

Swapping adalah teknik manajemen memori di mana seluruh proses disalin ke lokasi lain. Dengan kata lain,<br>
swapping adalah teknik di mana seluruh proses ditempatkan di memori utama untuk pelaksanaannya.<br> 
Pertukaran akan menghapus proses yang tidak aktif dari memori utama sistem. Swapping membantu menyediakan ruang memori untuk pengoperasian proses lainnya.<br>
Oleh karena itu, pertukaran berdampak pada kinerja sistem, karena membantu dalam menjalankan beberapa operasi besar secara bersamaan.<br>
Swapping dapat dilakukan tanpa menggunakan teknik manajemen memori apa pun.

Perbedaan paling signifikan antara keduanya adalah swapping adalah proses di mana seluruh proses disalin ke lokasi lain, sedangkan paging adalah teknik alokasi memori.
