## Tugas4

-[Belajar tentang shell programming](#Belajar-tentang-shell-programming)

## Daftar Isi
- [SAMPUL](#sistem-operasi)
- [TUGAS PENDAHULUAN](#tugas-pendahuluan)
- [PERCOBAAN](#percobaan)
- [LATIHAN](#latihan)
- [KESIMPULAN](#kesimpulan)


<div align="center">
  <h1 style="text-align: center;font-weight: bold"><br>Sistem Operasi</h1 {#sistem-operasi}
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br/>
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : 
  <p style="text-align: center;">
    <strong>Nama : Stalis Ahmad Sholeh</strong><br>
    <strong>Nrp : 3123521010</strong>
  </p>

<h3 style="text-align: center;line-height: 1.5">PROGRAM STUDI D3 TEKNIK INFORMATIKA<br>DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER<br>POLITEKNIK ELEKTRONIKA NEGERI SURABAYA – PSDKU LAMONGAN</h3>
  <hr><hr>
</div>

# Operasi Input Output
Referensi : [Shell Programming](https://www.geeksforgeeks.org/introduction-linux-shell-shell-scripting/?ref=shm_)
## POKOK BAHASAN:
```
* Pipeline
* Redirection
```
## TUJUAN PEMBELAJARAN:
Setelah mempelajari materi dalam bab ini, mahasiswa diharapkan mampu:
* Memahami konsep proses I/O dan redirection
* Memahami standar input, output dan error
* Menggunakan notasi output, append dan here document
* Memahami konsep *PIPE* dan filter
  
## DASAR TEORI:

### 1. PROSES I/O
Sebuah proses memerlukan Input dan Output. Instruksi (command) yang diberikan pada Linux melalui Shell disebut sebagai eksekusi program yang selanjutnya disebut proses. Setiap kali instruksi diberikan, maka Linux kernel akan menciptakan sebuah proses dengan memberikan nomor PID (Process Identity). Proses dalam Linux selalu membutuhkan Input dan menghasilkan suatu Output.

```mermaid
graph LR
    Input[Input] --> Process[Process] --> Output[Output]
```

Dalam konteks Linux input/output adalah :
* Keyboard (input)
* Layar (output)
* Files
* Struktur data kernel
* Peralatan I/O lainnya (misalnya Network)

## 2. FILE DESCRIPTOR

Linux berkomunikasi dengan file melalui file descriptor yang direpresentasikan melalui angka yang dimulai dari 0, 1, 2 dan seterusnya. Tiga buah file descriptor standar yang lalu diciptakan oleh proses adalah :
* 0 = keyboard (standar input)
* 1 = layar (standar output)
* 2 = layar (standar error)

Linux tidak membedakan antara peralatan hardware dan file. Linux memanipulasi peralatan hardware dengan memperlakukannya sama dengan ketika memperlakukan sebuah file.

## 3.PEMBELOKAN (REDIRECTION)

Pembelokan dilakukan untuk standard input, output dan error, yaitu untuk mengalihkan file descriptor dari 0, 1 dan 2. Simbol untuk pembelokan adalah :
```mermaid
flowchart LR
    A(Standart Input) -->|Keyboard| B{Process}
    B -->|Monitor| C[Standart Output]
    B -->|Monitor| D[Standart Error]
 ```

## 4. PIPA (PIPELINE)
Mekanisme pipa digunakan sebagai alat komunikasi antar proses.

```mermaid
graph LR
  A(Input) --> B(Proses-1) --> C(Output) --> D(Input) --> E(Proses-2) --> F(Output)
```
Proses-1 menghasilkan output yang selanjutnya digunakan sebagai input oleh Proses-2. Hubungan output input ini dinamakan ``pipa ataiupipelining``, yang menghubungkan Proses-1 dengan Proses-2 dan dinyatakan dengan symbol “|”.
```
    Proses1 | Proses
```

## 5. FILTER
Filter adalah utilitas Linux yang dapat memproses standard input (dari keyboard) dan menampilkan hasilnya pada standard output (layar). Contoh filter adalah cat, sort, grep, pr, head, tail, paste dan lainnya.
Pada sebuah rangkaian pipa : 

        P<sub>1</sub> | P<sub>2</sub> | P<sub>3</sub> ... | P<sub>n-1</sub> | P<sub>n</sub>

Maka P2 sampai dengan P<sub>n-1</sub> berfungsi sebagai filter. P1 (awal) dan Pn (terakhir) boleh tidak filter. Utilitas yang bukan filter misalnya who, ls, ps, lp, lpr, mail dan lainnya.
Beberapa perintah Linux yang digunakan untuk proses penyaringan antara lain :
* Perintah ``grep``
  Digunakan untuk menyaring masukannya dan menampilkan baris-baris yang hanya mengandung pola yang ditentukan. Pola ini disebut regular expression.
* Perintah ``wc``
  Digunakan untuk menghitung jumlah baris, kata dan karakter dari baris-baris masukan yang diberikan kepadanya. Untuk mengetahui berapa baris gunakan option –l, untuk mengetahui berapa kata, gunakan option –w dan untuk mengetahui berapa karakter, gunakan option –c. 
  Jika salah satu option tidak digunakan, maka tampilannya adalah jumlah baris, jumlah kata dan jumlah karakter.
* Perintah ``sort``
  Digunakan untuk mengurutkan masukannya berdasarkan urutan nomor ASCII dari karakter.
* Perintah ``cut``
  Digunakan untuk mengambil kolom tertentu dari baris-baris masukannya, yang ditentukan pada option –c.
* Perintah ``uniq``
  Digunakan untuk menghilangkan baris-baris berurutan yang mengalami duplikasi, biasanya digabungkan dalam pipeline dengan ``sort``.

## TUGAS PENDAHULUAN

## Jawablah pertanyaan-pertanyaan di bawah ini :

1. Apa yang dimaksud redirection?<br>Redirection adalah proses mengalihkan output dari suatu program atau perintah ke lokasi lain.
2. Apa yang dimaksud pipeline?<br>Pipeline adalah Mekanisme pipa yang digunakan sebagai alat komunikasi antar proses.
3. Apa yang dimaksud perintah di bawah ini :
   <br> echo, cat, more, sort, grep, wc, cut, uniq
<br>Echo : digunakan untuk menampilkan nilai atau variabel cara menngunakan nya echo “hello word”
<br>cat :  Untuk menggabungkan dan menampilkan isi satu atau beberapa file secara urut.
<br>more :  Untuk menampilkan isi file satu halaman pada satu waktu.
<br>sort : Digunakan untuk mengurutkan masukannya berdasarkan urutan nomor ASCII dari karakter.
<br>grep : untuk menyaring masukannya dan menampilkan baris-baris yang hanya 
<br>mengandung pola yang ditentukan. Pola ini disebut regular expression. 
<br>wc : Digunakan untuk menghitung jumlah baris, kata dan karakter dari baris-baris masukan yang diberikan kepadanya
<br>cut : Digunakan untuk mengambil kolom tertentu dari baris-baris masukannya, yang ditentukan pada option –c.
<br>uniq : Digunakan untuk menghilangkan baris-baris berurutan yang mengalami duplikasi, biasanya digabungkan dalam pipeline dengan sort


## PERCOBAAN

1. Login sebagai user.
2. Bukalah Console Terminal dan lakukan percobaan-percobaan di bawah ini. Perhatikan hasil setiap percobaan.
3. Selesaikan soal-soal latihan.


## Percobaan 1 : File descriptor

1. Output ke layar (standar output), input dari system (kernel)
    ```
    $ ps
    ```
    <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/c6092510-7025-4836-9602-a4112701ef72)
   <br> Keterangan : Perintah $ ps digunakan untuk untuk menampilkan informasi tentang proses yang sedang aktif di dalam sistem.
3. Output ke layar (standar output), input dari keyboard (standard input)
   ```
    $ cat
    hallo, apa khabar
    hallo, apa khabar
    exit dengan ^d
    exit dengan ^d
    [Ctrl-d]
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/9ffc2784-b774-4b4e-a639-917ca8773879)
   <br> Keterangan : Perintah cat digunakan untuk untuk menampilkan informasi tentang proses yang sedang aktif di dalam sistem.

5. Input nama direktori, output tidak ada (membuat direktori baru), bila terjadi error maka tampilan error pada layar (standard error)
   ```
   $ mkdir mydir
   $ mkdir mydir **(Terdapat pesan error)**
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/d0fdd718-9035-4dab-abc9-651b183795d6)
   <br> Keterangan : Perintah mkdir perintah yang digunakan untuk membuat direktori baru di dalam filesystem.

## Percobaan 2 : Pembelokan (redirection)
1. Pembelokan standar output
   ```
    $ cat 1> myfile.txt
    Ini adalah teks yang saya simpan ke file myfile.txt
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/516bece8-0b48-47bb-a4bd-43699f390b79)
   <br> Keterangan : Perintah “cat 1> myfile.txt” digunakan untuk meng-input‐kan dengan keyboard dan tanda "1>" merupakan pengganti dari standard output.
3. Pembelokan standar input, yaitu input dibelokkan dari keyboard menjadi dari file
   ```
    $ cat 0< myfile.txt
    $ cat myfile.txt
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/4cf29dad-bba3-4eca-bcd4-75b166dfc3ff)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/40f639b8-0e55-466f-a74a-b8c568058bbf)
   <br> Keterangan : Perintah “cat 0< myfile.txt” ini digunakan untuk file input dibelokkan dari keyboard dari file sehingga antara “cat 0< myfile.txt” dan “cat myfile.txt” memiliki keterkaitan.
5. Pembelokan standar error untuk disimpan di file
   ```
    $ mkdir mydir (Terdapat pesan error)
    $ mkdir mydir 2> myerror.txt
    $ cat myerror.txt
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/7786753e-6ed1-4731-9c5b-e6c794d30d32)
   <br> Perintah “mkdir mydir” digunakan untuk membuat folder dengan nama mydir tetapi muncul pesan error, karena sudah dibuat sebelumnya. Selanjutnya, pada perintah “mkdir mydir 2> myerror.txt” digunakan untuk membelokkan (memindahkan) pesan error sebelumnya ke dalam file myerror.txt. Tanda "2>" menandakan bahwa output standard error. Selanjutnya, pada perintah “cat myerror.txt” digunakan untuk memunculkan teks yang terdapat dalam file myerror.txt berupa pesan error yang telah dibelokkan sebelumnya.
7. Notasi 2>&1 : pembelokan standar error (2>) adalah identik dengan file descriptor 1.
   ```
    $ ls filebaru (Terdapat pesan error)
    $ ls filebaru 2> out.txt
    $ cat out.txt
    $ ls filebaru 2> out.txt 2>&
    $ cat out.txt
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6429a90b-8302-4e3b-b35b-8877d645a23c)
   <br> Pembelokan standard error (2>) adalah identik dengan file descriptor 1. Perintah “ls filebaru” digunakan untuk menampilkan isi dari folder atau direktori dari filebaru. Tetapi, muncul pesan error karena direktori filebaru tidak ada. Kemudian, perintah “ls filebaru 2> out.txt” digunakan untuk memindahkan pesan error tersebut ke dalam file out.txt melalui standard error yang ditandai dengan "2>". Kemudian, perintah “ls filebaru 2 > out.txt 2>&1” mempunyai fungsi yang sama dengan perintah “cat out.txt.”.
9. Notasi 1>&2 (atau >&2) : pembelokan standar output adalah sama dengan file descriptor 2 yaitu standar error
   ```
   $ echo “mencoba menulis file” 1> baru
   $ cat filebaru 2> baru 1>&
   $ cat baru
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/c78918c7-2c4c-4e12-b74f-4df7edd44c29)
   <br> Perintah echo "mencoba menulis file" >1 baru digunakan untuk menulis kata "mencoba menulis file" yang kemudian dibelokkan ke filebaru yang ditandai dengan tanda "1>". Selanjutnya, pada perintah “cat filebaru 2> baru 1>&2” digunakan untuk membelokkan tampilan filebaru ke standard output yang ditandai dengan tanda "1>&2" yang berarti sama dengan descriptor 2 yaitu standard error.
10. Notasi >> (append)
   ```
   $ echo “kata pertama” > surat
   $ echo “kata kedua” >> surat
   $ echo “kata ketiga” >> surat
   $ cat surat
   $ echo “kata keempat” > surat
   $ cat surat
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/0d18fb9f-b8ce-4f50-bd7f-317bb287f7a3)
   <br> Perintah echo "kata pertama" > surat digunakan untuk menulis kalimat "kata pertama" ke dalam file surat. Selanjutnya, pada perintah echo "kata kedua" >> surat digunakan untuk menulis "kata kedua" ke dalam file surat tanpa menghapus teks sebelumnya yang ditandai dengan ">>". Selanjutnya, pada perintah echo "kata ketiga" >> surat digunakan untuk menulis kalimat "kata ketiga" ke dalam file surat tanpa menghapus teks sebelumnya. Kemudian, teks tersebut ditampilkan dengan perintah cat surat. Selanjutnya, perintah echo "kata keempat" > surat digunakan untuk menulis "kata keempat" dengan menghapus teks sebelumnya yang ditandai dengan tanda ">". Kemudian perintah cat surat digunakan untuk menampilkan isi file surat.
11. Notasi here document (<<++ .... ++) digunakan sebagai pembatas input dari keyboard. Perhatikan bahwa tanda pembatas dapat digantikan dengan tanda apa saja, namun harus sama dan tanda penutup harus diberikan pada awal baris
   ```
   $ cat <<++
   Hallo, apa kabar?
   Baik-baik saja?
   Ok!
   ++
   $ cat <<%%%
   Hallo, apa kabar?
   Baik-baik saja?
   Ok!
   %%%
   ```
<br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/0919095a-6aac-428f-9b62-63c8c463b9db)
<br> Tanda ++ ... ++ digunakan sebagai pembatas input dari keyboard. Tanda tersebut bisa diganti oleh tanda apa saja asalkan pada awal dan akhirnya sama. Pada saat mengetikkan perintah “cat << ++” kemudian mengetikkan kalimat, setelah enter ternyata bisa memasukkan beberapa kalimat lagi. Tetapi, saat menuliskan kalimat ++, sistem menghentikan proses kemudian menampilkannya.
11. Notasi – (input keyboard) adalah representan input dari keyboard. Artinya menampilkan file 1, kemudian menampilkan input dari keyboard dan menampilkan file 2. Perhatikan bahwa notasi “-“ berarti menyelipkan input dari keyboard
  ```
  $ cat myfile.txt – surat
  ```
<br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2053a95c-1b80-4ede-9966-699bbcfc6fa3)
<br> Tanda "‐" (input dari keyboard) adalah representan input dari keyboard. Artinya, menampilkan file 1, kemudian menampilkan input dari keyboard dan menampilkan file 2. Tanda "‐" menyatakan bahwa menyelipkan input dari keyboard. Pada terminal ini, akan menampilkan isi file dari "myfile.txt" sekaligus menampilkan file "surat".

## Percobaan 3 : Pipa (pipeline)

1. Operator pipa (|) digunakan untuk membuat eksekusi proses dengan melewati data langsung ke data lainnya.
   ```
   $ who
   $ who | sort
   $ who | sort –r
   $ who > tmp
   $ sort tmp
   $ rm tmp
   $ ls –l /etc | more
   $ ls –l /etc | sort | more
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/43553259-5cdd-4297-934a-f4d93fe48968)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/cee6236a-6987-4333-bfda-399604bfda6f)
   <br> Pipeline memungkinkan user untuk menggabungkan beberapa perintah secara efisien, dengan output dari satu perintah menjadi input untuk perintah berikutnya. Hal ini sangat berguna untuk memproses dan menganalisis data secara langsung tanpa perlu menyimpannya dalam file sementara
2. Untuk membelokkan standart output ke file, digunakan operator ">"
   ```
   $ echo hello
   $ echo hello > output
   $ cat output
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/66a63a26-23ec-4d6c-9105-b9ac50590001)
   <br> Perintah “echo hello” digunakan untuk menampilkan teks "hello" seketika itu juga. Selanjutnya, perintah “echo hello > output” digunakan untuk membelokkan kata "hello" ke file output. Selanjutnya, perintah “cat output” digunakan untuk menampilkan isi dari file output.
3. Untuk menambahkan output ke file digunakan operator ">>"
   ```
   $ echo bye >> output
   $ cat output
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/eaa04603-84f6-441c-847c-ec5ebaa2cdbb)
   <br> Perintah “echo bye >> output” digunakan untuk menambahkan teks "bye" ke dalam file output yang ditandai dengan ">>". Setelah itu, perimtah “cat output” digunakan untuk menampilkan isi dari file output.
4. Untuk membelokkan standart input digunakan operator "<"
   ```
   $ cat < output
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/33f3de42-ccc4-4e70-a50b-ae1e91b56fb3)
   <br> perintah tersebut digunakan untuk menampilkan isi file dari output
5. Pembelokan standart input dan standart output dapat dikombinasikan tetapi tidak boleh menggunakan nama file yang sama sebagai standart input dan output.
   ```
   $ cat < output > out
   $ cat out
   $ cat < output >> out
   $ cat out
   $ cat < output > output
   $ cat output
   $ cat < out >> out (Proses tidak berhenti)
   [Ctrl-c]
   $ cat out
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/208783dc-d5e2-4130-b513-9903060678fc)
   <br> Perintah “cat < output > out” dan “cat out” merupakan perintah yang dikombinasikan untuk membelokkan standard output dari file output menjadi standard input untuk file out sehingga hasil standard output‐nya sama. Selanjutnya, perintah “cat < output >> out” digunakan untuk membelokkan standard output dari file output menjadi penambahan output ke file yang bernama out. Sehingga, output dari file out akan ditambahkan dengan output dari file output. Selanjutnya, perintah “cat output >> out”, “cat out”, “cat < output > output”, “cat output”, “cat < out >> out” tidak diperkenankan karena menggunakan nama file yang sama. Maka, akan muncul tulisan terus menerus hingga menekan tombol CTRL+c

## Percobaan 4 : Filter
1. Pipa juga digunakan untuk mengkombinasikan utilitas sistem untuk membentuk fungsi yang lebih kompleks
   ```
    $ w –h | grep <user>
    $ grep <user> /etc/passwd
    $ ls /etc | wc
    $ ls /etc | wc –l
    $ cat > kelas1.txt
    Badu
    Zulkifli
    Yulizir
    Yudi
    Ade
    [Ctrl-d]
    $ cat > kelas2.txt
    Budi
    Gama
    Asep
    Muchlis
    [Ctrl-d]
    $ cat kelas1.txt kelas2.txt | sort
    $ cat kelas1.txt kelas2.txt > kelas.txt
    $ cat kelas.txt | sort | uniq
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/db8ca35c-2223-40d6-a4f9-3218336707a9)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/84fbc0b5-e69b-490f-93f2-64e6cdc03ed9)
   <br> $ cat > kelas1.txt: Perintah ini membuka editor untuk membuat atau mengedit file bernama kelas1.txt

## LATIHAN

1. Lihat daftar secara lengkap pada direktori aktif, belokkan tampilan standard output   ke file baru.<br>![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/5fa03a83-a785-4716-adea-c45d683f41d5)
<br>Keterangan : Perintah ls untuk menampilkan daftar file,  perintah “>”  untuk mengarahkan output perintah ke file baru
2. Lihat daftar secara lengkap pada direktori /etc/passwd, belokkan tampilan standard output ke file baru tanpa menghapus file baru sebelumnya.<br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/17c5e1f8-b6c2-463d-a51f-d68a0d9fe348)
<br>Keterangan : Perintah cat untuk menggabungkan dan menampilkan isi satu atau beberapa file secara urut di /etc/passwd.lalu  perintah “>>” untuk mengalihkan outpunya ke file baru.
3. Urutkan file baru dengan cara membelokkan standard input.<br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2b79f95b-6d3a-452a-8808-ad3dbf72a8e7)
<br>Keterangan :  perintah sort digunakan untuk mengurutkan masukannya, perintah “<” digunakan untuk sebagai input dari perintah sort ke file baru
4. Urutkan file baru dengan cara membelokkan standard input dan standard output ke file baru.urut.<br>![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/d4be7bc0-755e-48c3-838b-ad41d61eb319)
<br>Keterangan : perintah sort digunakan untuk mengurutkan masukannya berdasarkan urutan nomor, “< “ baru mengarahkan isi file baru sebagai input untuk perintah sort.”>” mengarahkan output dari perintah sort ke file baru dengan nama baru.urut .
5. Buatlah direktori latihan 2 sebanyak 2 kali dan belokkan standard error ke file rmdirerror.txt.<br>![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/33687ab0-41b2-4d8b-8de8-4e058b47546e)
<br>Keterangan : Menggunakan mkdir untuk membuat direktori Latihan2  sebnyak 2 kali, “2>”mengarhkan error ke file rmdirerror.txt
6. Urutkan kalimat berikut :
   ```
   Jakarta
   Bandung
   Surabaya
   Padang
   Palembang
   Lampung
   ```
  Dengan menggunakan notasi **here document (<@@@ ...@@@)** . [HINT](https://www.geeksforgeeks.org/how-to-use-here-document-in-bash-programming/)
  <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/df54d003-5cb4-42d0-bef3-67e20ab4fb25)
<br> Keterangan : Pertama, buat notasi here document yang akan dibelokkan ke sebuah file kemudian isi document tersebut. Setelah diisi dan diakhiri, isi dokumen akan tersimpan ke file yang dibelokkan. File tersebut kemudian diurutkan menggunakan perintah $ sort.



7. Hitung jumlah baris, kata dan karakter dari file baru.urut dengan menggunakan filter dan tambahkan data tersebut ke file baru. <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/4d40245f-f039-4727-8cad-cefa7426cfb8)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/26271498-95d3-4751-b5f2-6bba9f2f00a3)
<br>Keterangan : Untuk menghidung jumlah baris, kata dan karakter kita harus menggunakan perintah wc -l untuk menghitung jumlah baris, wc -w untuk menghitaung jumlah kata, dan wc -c untuk menghitung jumlah karakter kemudian menggunakan perintah pengelompokan “{}” untuk memindahkan jumlah baris, kata dan karakter, menggunakan perintah “>>” untuk memindahkan file tersebut ke file Bernama baru.
8. Gunakan perintah di bawah ini dan perhatikan hasilnya.
   ```
    $ cat > hello.txt
    dog cat
    cat duck
    dog chicken
    chicken duck
    chicken cat
    dog duck
    [Ctrl-d]
    $ cat hello.txt | sort | uniq
    $ cat hello.txt | grep “dog” | grep –v “cat”
   ```
   <br> ![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/5bc12f1a-95f2-4699-981d-342af767a082)
<br>Keterangan : Perintah “cat > hello.txt” digunakan untuk membuat atau menulis ke file hello.txt. perintah “ cat hello.txt | sort | uniq “akan mengeluarkan hasil teks yang sudah diurutkan dan tidak mengandung baris yang sama, Perintah “cat hello.txt | grep "dog" | grep -v "cat" “, akan mencari baris-baris dalam file hello.txt yang mengandung kata "dog" tetapi tidak mengandung kata "cat".

   
## LAPORAN RESMI:

1. Analisa hasil percobaan 1 sampai dengan 4, untuk setiap perintah jelaskan    tampilannya.
2. Kerjakan latihan diatas dan analisa hasilnya
3. Berikan kesimpulan dari praktikum ini.

## KESIMPULAN
Proses I/O, file descriptor, redirection, dan pipeline adalah konsep-konsep fundamental dalam sistem operasi dan pengelolaan aliran data di dalamnya.
Proses I/O (Input/Output) :
Sebuah proses memerlukan Input dan Output. Instruksi (command) yang diberikan pada Linux melalui Shell disebut sebagai eksekusi program yang selanjutnya disebut proses. Setiap kali instruksi diberikan, maka Linux kernel akan menciptakan sebuah proses dengan memberikan nomor PID (Process Identity). Proses dalam Linux selalu membutuhkan Input dan menghasilkan suatu Output.
File Descriptor :
- File descriptor adalah angka yang digunakan oleh sistem operasi untuk mengidentifikasi dan merujuk ke file atau aliran data yang terbuka oleh proses.
- File descriptor ini sering kali diasosiasikan dengan tiga deskriptor standar: 0 = keyboard (standar input), 1 = layar(standar output), dan 2 = layar (standar error).
Redirection :
- Redirection adalah proses mengubah aliran data standar masukan (stdin), keluaran (stdout), dan keluaran kesalahan (stderr) dari dan ke file lain.
- Dalam sistem UNIX/Linux, operator seperti '<', '>', dan '>>' digunakan untuk mengalihkan aliran data dari dan ke file.
Pipeline :
- Pipa adalah mekanisme di sistem operasi UNIX/Linux yang memungkinkan keluaran dari satu program digunakan sebagai masukan untuk program lainnya secara berurutan.
- Pipa menggunakan operator '|' untuk menghubungkan beberapa perintah bersama-sama, sehingga keluaran dari perintah pertama menjadi masukan bagi perintah kedua, dan seterusnya.

