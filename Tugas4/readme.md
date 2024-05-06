## SIKLUS CPU - PERAN BAHASA PEMROGRAMAN DAN COMPILER

- [Siklus CPU](#soal1)

1.Buatlah presentasi langkah demi langkah tentang siklus CPU (fetch,decode,execute) utk mengeksekusi sebuah program. Jelaskan juga peran dari Bahasa pemrograman dan compiler, begitu juga dengan peran dari Sistem Operaso. Gunakan referensi : [Video referensi 1](https://www.youtube.com/watch?v=Z5JC9Ve1sfI) dan [Video referensi 2](https://www.youtube.com/watch?v=jFDMZpkUWCw)

penjelasan tentang tiga tahap utama dalam siklus fetch-execute: {#soal1}

1. Fetch (Pengambilan):
Siklus fetch adalah proses pengambilan data ke memori atau register. CPU mengambil sejumlah data atau intruksi dari memori utamakemudian menyimpan kedalam memori internal yang di sebut register

2. Decode (Pendekodean/menerjemahkan):
Siklus decode adalah proses menerjemahkannya ke dalam perintah komputer, Decode menafsirkan instruksi.Selama siklus ini instruksi di dalam IR (instruksi pendaftaran) akan diterjemahkan.

3. Execute (Pelaksanaan/eksekusi):
Siklus execute adalah  proses di mana komputer atau mesin virtual mengeksekusi dan bertindak berdasarkan instruksi program komputer.

Eksekusi dalam sebuah program

![cpu (1)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/566da58b-c555-4807-b3d9-7147613118de)

pada click pertama siklus Fetch :
![cpu (29)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/5210d90c-12a8-4912-82d2-7b53d37a7130)
jam menunjukan pada click 2, lalu cpu mengambil intruksi(value) yang berisi LOAD 6 pada RAM / memori  dan memasukan kedalam INTRUCTION REGISTER 

Pada click  kedua siklus decode :
![cpu (30)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/70798991-c3bd-4c79-8060-69ec110bb8c3)
jam menunjukan pada click 1, CPU menerjemahkan intruksi dalam gambar tersebut intruksinya adalah LOAD dan alamatnya adalah 6, jadi kita memuat nilai di alamat 6 memasukkan nya ke dalam ACCUMULATOR  

Pada click  ketiga siklus Execute :
![cpu (4)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/a16cc30f-c74e-4857-b7d6-e436fd97e7b3)
jam menunjukan pada click 2, CPU menjalankan intruksi dibutuhkan nilai di alamat 6 yaitu 1 dan memuatnya ke ACCUMULATOR

Pada click keempat siklus Fetch :
![cpu (31)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2889ad44-f000-4fb1-98c3-5c7d472dfa2c)
jam menunjukan pada click 1, Perhitungan program bertambah lalu CPU mengambil intruksi berikutnya pad memori yaitu ADD 7

Pada click  kelima siklus decode :
![cpu (32)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/3ea4e250-40ac-43c7-a8c0-40311d4c68cb)
jam menunjukan pada click 2, CPU menerjemahkan intruksi pada gambar tersebut intruksinya adalah ADD dan alamatnya adalah 7, jadi kita menambahkan apa yang ada di alamat 7  ke dalam apa yang sdah ada di ACCUMULATOR  

Pada click  keenam siklus Execute :
![cpu (7)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6a7bce20-a0b9-4e5d-b71c-c8ef283581c3)jam menunjukan pada click 1, CPU mengeksekusi intruksi kali ini alamatnya adalah 7 dan nilainya adalah 1, nilai sebelunya pada ACCUMULATOR adalah 1  di tambah dengan nilai pada alamat 7 berarti 1+1= 2 jadi pada ACCUMULATOR adalah 2

Pada click ketujuh siklus Fetch :
![cpu (8)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/51723973-c1d6-4709-b338-5f91268a25c9)
jam menunjukan pada click 2, CPU mengambil intruksi berikutnya pad memori yaitu STORE 6  

Pada click  kedelapan siklus decode :
![cpu (9)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/9ea73b55-a2b0-4820-a5b9-a2137840c1c4)
jam menunjukan pada click 1,   CPU menerjemahkan intruksi pada gambar tersebut intruksinya adalah STORE dan alamatnya adalah 6

Pada click  kesembilan siklus Execute :
![cpu (11)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6a71490a-155f-4905-b566-799647eabd1d)
jam menunjukan pada click 2, CPU mengeksekusi intruksi menimpa apa yang sudah pada alamat 6 yang bernilai , dalam hal ini alamat 6 memiliki nilai 2 

Pada click kesepuluh siklus Fetch :
![cpu (12)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/54917d43-8de6-4fba-b6a4-b3ee266049cf)
jam menunjukan pada click 1, CPU mengambil intruksi baru pada memori yaitu  JUMP 1

Pada click  kesebelas siklus decode :
![cpu (13)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/08794a17-f990-4a96-b3e2-b32d3e3970a3)
jam menunjukan pada click 2, CPU menerjemahkan intruksi pada gambar tersebut intruksinya adalah JUMP dan alamatnya adalah 1 jadi kita akan melompat ke alamat nomor 1

Pada click  keduabelas siklus Execute :
![cpu (14)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/7bd5443b-23c6-4304-8b9c-d09e4fde0c63)
jam menunjukan pada click 1, CPU mengeksekusi intruksi perhitungan program sekarang kembali ke 1

pada click ketigabelas siklus Fetch :
![cpu (15)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/f7421e5b-716d-4ec9-9996-c71ee33a56b5)
jam menunjukan pada click 2, lalu cpu mengambil dari lokasi 1 yang berisi ADD 7 pada RAM / memori  dan memasukan kedalam INTRUCTION REGISTER 

Pada click  keempatbelas siklus decode :
![cpu (16)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/632ca023-41d5-432a-ad82-6d0c707270c3)
jam menunjukan pada click 1,  CPU menerjemahkan intruksi pada gambar tersebut intruksinya adalah ADD dan alamatnya adalah 7, jadi kita menambahkan apa yang ada di alamat 7  ke dalam apa yang sdah ada di ACCUMULATOR  
 

Pada click  kelimabelas siklus Execute :
![cpu (17)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/7b94a79b-c071-42ce-9854-4463e409b43f)
jam menunjukan pada click 2, CPU menjalankan intruksi tapi ACCUMULATOR pada siklus ini masih berisi nilai sebelumnya yaitu 2 jadi pada tahap ini nilai bertambah menjadi 3


pada click keenambelas siklus Fetch :
![cpu (33)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/048e8bed-5a95-4c68-9050-128ed4572953)
jam menunjukan pada click 1,CPU mengambil intruksi berikutnya pad memori yaitu STORE 6 

Pada click  ketujubelas siklus decode :
![cpu (19)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/4d4fe51a-28df-4441-9465-ee945b1793f7)
jam menunjukan pada click 2, CPU menerjemahkan intruksi pada gambar tersebut intruksinya adalah STORE dan alamatnya adalah 6
 
Pada click  kelapanbelas siklus Execute :
![cpu (24)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/d5cc09e7-bef3-41b2-8899-0edbb7736169)
jam menunjukan pada click 1,  CPU mengeksekusi intruksi myimpan ke lokasi nomor 6 ,sebelumnya 2+1 jadi nilai dari alamat 6 sekarang adalah 3


pada click kesembilanbelas siklus Fetch :
![cpu (21)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/f330df84-c88c-4362-9cbf-d205b3468a10)
jam menunjukan pada click 2,CPU mengambil intruksi  pada memori yaitu  JUMP 1

Pada click  keduapuluh siklus decode :
![cpu (22)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/201367d0-d1ba-4ed2-b52d-c988dce70496)
jam menunjukan pada click 1, CPU menerjemahkan intruksi pada gambar tersebut intruksinya adalah JUMP dan alamatnya adalah 1 jadi kita akan melompat ke alamat nomor 1
 
Pada click  keduapuluh1 siklus Execute :
![cpu (23)](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/eb396340-96b9-4e75-abe7-4b8117ae9162)
jam menunjukan pada click 2,  CPU mengeksekusi intruksi perhitungan program sekarang kembali ke 1








Bahasa pemrograman adalah sebuah instruksi standar untuk memerintah komputer agar menjalankan fungsi tertentu. Bahasa pemrograman ini merupakan suatu himpunan dari aturan sintaksis dan semantik yang dipakai untuk mendefinisikan tata olah (program). Bahasa ini memungkinkan seorang penata olah (programmer) dapat menentukan secara persis data mana yang akan diolah oleh komputer, bagaimana data ini akan disimpan/diteruskan, dan jenis langkah apa yang secara persis akan diambil dalam berbagai situasi.

Compiler adalah software komputer yang mengubah kode sumber (source code) program dalam bahasa pemrograman menjadi kode objek atau bahasa mesin yang dimengerti komputer untuk kemudian dieksekusi / Program yang mengubah program computer yang dihasilkan dari suatu bahasa pemrograman ke bahasa pemrograman lain yang berbeda.
Dengan compiler (kompilator), programmer cukup menulis kode sumber (coding) dengan bahasa pemrograman yang dipahami manusia. Tugas kompilator adalah menerjemahkan kode program menjadi bahasa mesin berbentuk kode biner (0 dan 1).

Setelah menghasilkan kode objek, komputer bisa menjalankan perintah sesuai instruksi yang ditulis oleh programmer.
Maka bisa dibilang, compiler adalah jembatan penghubung antara programmer dan komputer atau perangkat mesin lainnya melalui perintah pemrograman.

Peran Sistem Operasi
Sistem operasi adalah perangkat lunak (software) yang dapat melakukan tugas mengontrol dan mengatur perangkat keras (hardware) sekaligus operasi dasar sistem lainnya dan juga bisa untuk menjalankan program aplikasi.

Sistem operasi mempunyai peran penting di dalam suatu sistem komputer.
Manajemen Sumber Daya Komputer
Sebagai Aplikasi Dasar Sebuah Perangkat
Mengoptimalkan Fungsi Sebuah Perangakt
Mengatur Sistem Kerja Perangkat

[no2]: #no2
2. Baca dan pahami rangkuman materi OS: [Materi Intro to OS-01](https://github.com/ferryastika/OS-01)
[no3]: #no3
3. Jalankan VM Debian anda, lalu lakukan clone https://github.com/ferryastika/flops-iops. Compile dan eksekusi sesuai petunjuk. Sesuiakan jumlah thread dengan jumlah CPU yang ada di VM Debianmu. Catat hasilnya dan jelaskan arti dari hasil ekskusi. Lakukan sebanyak 5 kali. Bandingkan hasilnya anatar temanmu. Buat Plot perbandinnga hasil untuk masing-masing PC di tiap kelompokmu. Analisa hasil percobaan tadi dan beri kesimpulan tentang IOPS dan FLOPS.

 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/5b4d656e-8515-4493-b161-287dfd6952af)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/13354f59-caea-4425-9bba-78b26ac534d8)

	Keterangan : dengan perintah git clone akan melakukan cloning flops-iops dari GitHub ke direktori  saat ini. Lalu cd flops-iops perinitah tersebut akan masuk ke directory flops-iops
  $ make
  $ make clean
  $ sudo make install
  $ iops64 $(nproc)
  $ flops64 $(nproc)
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/cbe29999-80d0-40b0-b578-5640bd52aa48)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6f0c8e81-24a7-4487-837b-500ace8d6c79)

IOPS (Input/Output Operations Per Second):
IOPS mengukur jumlah operasi masukan/keluaran (Input/Output) yang dapat dilakukan oleh sistem dalam satu detik.
FLOPS (Floating Point Operations Per Second):
FLOPS mengukur jumlah operasi titik mengambang (floating point) yang dapat dilakukan oleh sistem dalam satu detik.
Kesimpulan
Semakin tinggi nilai IOPS, semakin cepat sistem dapat memproses operasi masukan/keluaran, yang berarti kinerja sistem I/O yang lebih baik. Semakin tinggi nilai FLOPS, semakin cepat sistem dapat menyelesaikan operasi, yang berarti kinerja komputasi yang lebih baik.

 
[no4]: #no4
4.	Apabila Debian VM mu masih belum terdapat packeage gcc, make dan git, lakukan instalasi dan catat setiap langkahnya!
Untuk melakukan instalasi harus mengedit repository terlebihdahulu 
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2785efbe-fea1-4681-b271-96d16b41633b)

Perintah su yaitu untuk masuk ke rott lalu masuk ke /etc/apt# nano sources.list untuk mengedit repositori
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/9e32a3e4-14e7-4d00-8882-d2392ea0082f)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/8494c88d-4bc3-4bb7-a9e7-208aad490ab9)
 
Ketikan kode tersebut lalu crtl x untuk keluar dan save
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/175f49e9-f4d2-4719-99f8-ebfe451d88c7)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/b11c88c9-05f8-4206-9fa0-4d128e34de9c)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/88b7868d-13a8-4ddf-bcda-08ffdb6a65a0)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/486ab920-27be-4cf9-a5eb-43234f79aa9d)
Lalu lakukan apt update 
Lalu ketik apt install (apa yang ingin di install) gcc, make dan git
penginstalan sudah selesai
