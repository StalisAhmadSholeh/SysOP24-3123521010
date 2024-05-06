## Tugas 

1. Buatlah presentasi langkah demi langkah tentang siklus CPU (fetch,decode,execute) utk mengeksekusi sebuah program. Jelaskan juga peran dari Bahasa pemrograman dan compiler, begitu juga dengan peran dari Sistem Operaso. Gunakan referensi : Video referensi 1 dan Video referensi 2 [jawaban ada disini](#siklus-cpu)
2. Baca dan pahami rangkuman materi OS: Materi Intro to OS-01
3. Jalankan VM Debian anda, lalu lakukan clone https://github.com/ferryastika/flops-iops. Compile dan eksekusi sesuai petunjuk. Sesuiakan jumlah thread dengan jumlah CPU yang ada di VM Debianmu. Catat hasilnya dan jelaskan arti dari hasil ekskusi. Lakukan sebanyak 5 kali. Bandingkan hasilnya anatar temanmu. Buat Plot perbandinnga hasil untuk masing-masing PC di tiap kelompokmu. Analisa hasil percobaan tadi dan beri kesimpulan tentang IOPS dan FLOPS. [jawaban ada disini](#cloning)
4. Apabila Debian VM mu masih belum terdapat packeage gcc, make dan git, lakukan instalasi dan catat setiap langkahnya! [jawaban ada disini](#install-packeage)

1.Buatlah presentasi langkah demi langkah tentang siklus CPU (fetch,decode,execute) utk mengeksekusi sebuah program. Jelaskan juga peran dari Bahasa pemrograman dan compiler, begitu juga dengan peran dari Sistem Operaso. Gunakan referensi : [Video referensi 1](https://www.youtube.com/watch?v=Z5JC9Ve1sfI) dan [Video referensi 2](https://www.youtube.com/watch?v=jFDMZpkUWCw)

## Siklus CPU 


penjelasan tentang tiga tahap utama dalam siklus fetch-execute: 

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
