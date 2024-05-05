## Tugas4

-[Belajar tentang shell programming](#Belajar-tentang-shell-programming)




## Belajar tentang shell programming

TUGAS PENDAHULUAN: 
Jawablah pertanyaan-pertanyaan di bawah ini : 

1. Apa yang dimaksud redirection ? 
2. Apa yang dimaksud pipeline ? 
3. Apa yang dimaksud perintah di bawah ini : 
echo, cat, more, sort, grep, wc, cut, uniq
Jawaban :
1.	Redirection adalah proses mengalihkan output dari suatu program atau perintah ke lokasi lain.
2.	Pipeline adalah Mekanisme pipa yang digunakan sebagai alat komunikasi antar proses.
3.	Echo : digunakan untuk menampilkan nilai atau variabel cara menngunakan nya echo “hello word”
cat :  Untuk menggabungkan dan menampilkan isi satu atau beberapa file secara urut.
more :  Untuk menampilkan isi file satu halaman pada satu waktu.
sort : Digunakan untuk mengurutkan masukannya berdasarkan urutan nomor ASCII dari karakter.
grep : untuk menyaring masukannya dan menampilkan baris-baris yang hanya 
mengandung pola yang ditentukan. Pola ini disebut regular expression. 
wc : Digunakan untuk menghitung jumlah baris, kata dan karakter dari baris-baris 
masukan yang diberikan kepadanya
cut : Digunakan untuk mengambil kolom tertentu dari baris-baris masukannya, yang
ditentukan pada option –c.
uniq : Digunakan untuk menghilangkan baris-baris berurutan yang mengalami duplikasi, biasanya digabungkan dalam pipeline dengan sort

Percobaan 1 : File descriptor
1.	Output ke layar (standar output), input dari system (kernel)
$ ps
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/c6092510-7025-4836-9602-a4112701ef72)

Keterangan : perintah ps digunakan untuk menampilkan daftar proses yang berjalan pada sistem.
2.	Output ke layar (standar output), input dari keyboard (standard input)
 $ cat
 hallo, apa khabar
 hallo, apa khabar
 exit dengan ^d
 exit dengan ^d
 [Ctrl-d]
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/9ffc2784-b774-4b4e-a639-917ca8773879)

Keterangan : perintah cat digunakan untuk menampilkan isi file
3.	Input nama direktori, output tidak ada (membuat direktori baru), bila terjadi error maka tampilan error pada layar (standard error)
$ mkdir mydir
$ mkdir mydir **(Terdapat pesan error)**
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/d0fdd718-9035-4dab-abc9-651b183795d6)

Keterangan : perintah mkdir digunakan untuk membuat directory yang bernama mydir kenapa kog eror yang kedua karena sudah ada directory 
Percobaan 2 : Pembelokan (redirection)
1.	Pembelokan standar output
 $ cat 1> myfile.txt
 Ini adalah teks yang saya simpan ke file myfile.txt
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/516bece8-0b48-47bb-a4bd-43699f390b79)

Keterangan : perintah ini akan menjalankan perintah cat, dan output dari perintah tersebut akan dituliskan ke dalam file baru yang disebut myfile.txt.
2.	Pembelokan standar input, yaitu input dibelokkan dari keyboard menjadi dari file
 $ cat 0< myfile.txt
 $ cat myfile.txt
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/4cf29dad-bba3-4eca-bcd4-75b166dfc3ff)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/40f639b8-0e55-466f-a74a-b8c568058bbf)

 
Keterangan : $ cat 0< myfile.txt: Perintah ini menggunakan operator < untuk mengalihkan standar input dari perintah cat menjadi berasal dari file myfile.txt (file descriptor 0 menunjukkan standar input).
$ cat myfile.txt: Perintah ini langsung menampilkan isi dari file myfile.txt di layar.
3.	Pembelokan standar error untuk disimpan di file
 $ mkdir mydir (Terdapat pesan error)
 $ mkdir mydir 2> myerror.txt
 $ cat myerror.txt
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/7786753e-6ed1-4731-9c5b-e6c794d30d32)

Keterangan : mkdir mydir: Perintah ini mencoba membuat direktori baru bernama mydir.
2>: Operator 2> digunakan untuk mengalihkan standar error dari perintah ke dalam file yang ditentukan. Angka 2 disini adalah file descriptor untuk standar error.
myerror.txt: Ini adalah nama file tempat pesan kesalahan akan dituliskan dalam file tersebut.
4.	Notasi 2>&1 : pembelokan standar error (2>) adalah identik dengan file descriptor 1.
 $ ls filebaru (Terdapat pesan error)
 $ ls filebaru 2> out.txt
 $ cat out.txt
 $ ls filebaru 2> out.txt 2>&
 $ cat out.txt
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6429a90b-8302-4e3b-b35b-8877d645a23c)

Keterangan : $ ls filebaru (Terdapat pesan error): Ini adalah perintah untuk mengecek keberadaan file atau direktori filebaru. Jika file atau direktori tersebut tidak ada, akan muncul pesan error di terminal.
$ ls filebaru 2> out.txt: Perintah ini juga mengecek keberadaan file atau direktori filebaru, tetapi jika terjadi kesalahan, pesan kesalahan akan ditangkap dan ditulis ke dalam file out.txt. Operator 2> digunakan untuk mengalihkan standar error ke dalam file out.txt.
$ ls filebaru 2> out.txt 2>&: Perintah ini tampaknya salah karena tidak memiliki tujuan. Operator 2>& digunakan untuk mengalihkan standar error ke lokasi yang sama dengan standar output.
$ cat out.txt: Ini adalah perintah untuk menampilkan isi dari file out.txt di layar. 
5.	Notasi 1>&2 (atau >&2) : pembelokan standar output adalah sama dengan file descriptor 2 yaitu standar error
$ echo “mencoba menulis file” 1> baru
$ cat filebaru 2> baru 1>&
$ cat baru
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/c78918c7-2c4c-4e12-b74f-4df7edd44c29)

Keterangan : Perintah ini Ini akan mengalihkan standar output dari cat filebaru ke file baru, dan juga mengalihkan standar error ke lokasi yang sama dengan standar output.
6.	Notasi >> (append)
$ echo “kata pertama” > surat
$ echo “kata kedua” >> surat
$ echo “kata ketiga” >> surat
$ cat surat
$ echo “kata keempat” > surat
$ cat surat
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/0d18fb9f-b8ce-4f50-bd7f-317bb287f7a3)

Keterangan : perintah echo gi guankan untuk menulis kata pertama lalu disimpan ke file surat, kata kedua di dimpan ke file surat dan kata ke tiga lalu perintah cat digunakan untuk menampilkan isi file 
7.	Notasi here document (<<++ .... ++) digunakan sebagai pembatas input dari keyboard. Perhatikan bahwa tanda pembatas dapat digantikan dengan tanda apa saja, namun harus sama dan tanda penutup harus diberikan pada awal baris
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
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/0919095a-6aac-428f-9b62-63c8c463b9db)

Keterangan :  cat <<++ Perintah ini mengaktifkan notasi here document dengan delimiter ++. Ini berarti bahwa semua teks yang dituliskan setelah perintah ini akan ditampilkan di layar hingga delimiter ++ seperti hallo, apa kabar sedangkan perintah cat <<%%% … %%% text yang berada dalam perintah tersebut akan ditampilkan di layar
8.	Notasi – (input keyboard) adalah representan input dari keyboard. Artinya menampilkan file 1, kemudian menampilkan input dari keyboard dan menampilkan file 2. Perhatikan bahwa notasi “-“ berarti menyelipkan input dari keyboard
$ cat myfile.txt – surat
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2053a95c-1b80-4ede-9966-699bbcfc6fa3)

Keterangan : melihat isi dari myfile.txt dan surat 
Percobaan 3 : Pipa (pipeline)
1.	Operator pipa (|) digunakan untuk membuat eksekusi proses dengan melewati data langsung ke data lainnya.
$ who
$ who | sort
$ who | sort –r
$ who > tmp
$ sort tmp
$ rm tmp
$ ls –l /etc | more
$ ls –l /etc | sort | more
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/43553259-5cdd-4297-934a-f4d93fe48968)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/cee6236a-6987-4333-bfda-399604bfda6f)

 
Keterangan : $ who: Menampilkan daftar pengguna yang sedang masuk ke sistem.
$ who | sort: Mengambil output dari perintah who, mengurutkannya, dan menampilkannya secara terurut.
$ who | sort –r: Kesalahan penulisan, seharusnya $ who | sort -r. Ini mengambil output dari perintah who, mengurutkannya secara terbalik (descending), dan menampilkannya.
$ who > tmp: Mengalihkan output dari perintah who ke dalam file sementara yang disebut tmp.
$ sort tmp: Mengurutkan isi dari file sementara tmp dan menampilkannya.
$ rm tmp: Menghapus file sementara tmp.
$ ls –l /etc | more: Menampilkan isi dari direktori /etc dengan format yang lebih rinci menggunakan ls -l, kemudian outputnya dialihkan ke perintah more untuk ditampilkan secara bertahap.
$ ls –l /etc | sort | more: Menampilkan isi dari direktori /etc dengan format yang lebih rinci menggunakan ls -l, mengurutkan outputnya, kemudian hasilnya dialihkan ke perintah more untuk ditampilkan secara bertahap.
2.	Untuk membelokkan standart output ke file, digunakan operator ">"
$ echo hello
$ echo hello > output
$ cat output
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/66a63a26-23ec-4d6c-9105-b9ac50590001)

Keterangan : perintah echo yaitu untuk memunculkan hello lalu  > untuk membeklokan standart output ke file outuput lalu perintah cat untuk melihat isi file output
3.	Untuk menambahkan output ke file digunakan operator ">>"
$ echo bye >> output
$ cat output
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/eaa04603-84f6-441c-847c-ec5ebaa2cdbb)

Keterangan : $ echo bye >> output digunakan untuk menambahkan text by ke file output
$ cat output perintah ini dikunakan untuk melihat isi file output
4.	Untuk membelokkan standart input digunakan operator "<"
$ cat < output
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/33f3de42-ccc4-4e70-a50b-ae1e91b56fb3)

Keterangan : perintah tersebut digunakan untuk menampilkan isi file dari output
5.	Pembelokan standart input dan standart output dapat dikombinasikan tetapi tidak boleh menggunakan nama file yang sama sebagai standart input dan output.
$ cat < output > out
$ cat out
$ cat < output >> out
$ cat out
$ cat < output > output
$ cat output
$ cat < out >> out (Proses tidak berhenti)
[Ctrl-c]
$ cat out
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/208783dc-d5e2-4130-b513-9903060678fc)

Keterangan : $ cat < output > out: Perintah ini mengambil isi dari file output dan menuliskannya ke dalam file out.
$ cat out: Perintah ini menampilkan isi dari file out.
$ cat < output >> out: Perintah ini mengambil lagi isi dari file output dan menambahkannya ke dalam file out. Dengan menggunakan operator >>, teks tambahan akan ditambahkan ke akhir file out. $ cat out: Perintah ini menampilkan isi dari file out. Sekarang, isi dari file out akan terdiri dari dua salinan dari isi file output. $ cat < output > output: Perintah ini mencoba mengambil isi dari file output dan menuliskannya kembali ke file output. Namun, karena kita mencoba menuliskan kembali ke file yang sama yang sedang dibaca, ini dapat menghasilkan perilaku yang tidak terduga dan dapat berpotensi mengakibatkan loop tak terbatas. $ cat output: Perintah ini menampilkan isi dari file output. Karena tidak ada operasi yang berhasil menuliskan ulang isi file output, isi file output tidak berubah. $ cat < out >> out: Perintah ini mencoba mengambil isi dari file out dan menambahkannya kembali ke file out. Dengan menggunakan operator >>, teks tambahan akan ditambahkan ke akhir file out. Namun, karena file out tidak berubah, proses ini akan masuk ke dalam loop tak terbatas. Dengan menekan Ctrl-c, proses tersebut dihentikan. $ cat out: Perintah ini menampilkan isi dari file out. Karena tidak ada tambahan yang ditambahkan ke file out, isi dari file out tetap sama seperti sebelumnya.
Percobaan 4 : Filter
1.	Pipa juga digunakan untuk mengkombinasikan utilitas sistem untuk membentuk fungsi yang lebih kompleks
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
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/db8ca35c-2223-40d6-a4f9-3218336707a9)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/84fbc0b5-e69b-490f-93f2-64e6cdc03ed9)

  
Keterangan : $ cat > kelas1.txt: Perintah ini membuka editor untuk membuat atau mengedit file bernama kelas1.txt
LATIHAN:
1.	Lihat daftar secara lengkap pada direktori aktif, belokkan tampilan standard output ke file baru.
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/5fa03a83-a785-4716-adea-c45d683f41d5)

Keterangan : Perintah ls untuk menampilkan daftar file,  perintah “>”  untuk mengarahkan output perintah ke file baru
2.	Lihat daftar secara lengkap pada direktori /etc/passwd, belokkan tampilan standard output ke file baru tanpa menghapus file baru sebelumnya.
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/17c5e1f8-b6c2-463d-a51f-d68a0d9fe348)

Keterangan : Perintah cat untuk menggabungkan dan menampilkan isi satu atau beberapa file secara urut di /etc/passwd.lalu  perintah “>>” untuk mengalihkan outpunya ke file baru.
3.	Urutkan file baru dengan cara membelokkan standard input.
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2b79f95b-6d3a-452a-8808-ad3dbf72a8e7)

Keterangan :  perintah sort digunakan untuk mengurutkan masukannya, perintah “<” digunakan untuk sebagai input dari perintah sort ke file baru
4.	Urutkan file baru dengan cara membelokkan standard input dan standard output ke file baru.urut.
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/d4be7bc0-755e-48c3-838b-ad41d61eb319)

Keterangan : perintah sort digunakan untuk mengurutkan masukannya berdasarkan urutan nomor, “< “ baru mengarahkan isi file baru sebagai input untuk perintah sort.”>” mengarahkan output dari perintah sort ke file baru dengan nama baru.urut .
5.	Buatlah direktori latihan 2 sebanyak 2 kali dan belokkan standard error ke file rmdirerror.txt.
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/33687ab0-41b2-4d8b-8de8-4e058b47546e)

Keterangan : Menggunakan mkdir untuk membuat direktori Latihan2  sebnyak 2 kali, “2>”mengarhkan error ke file rmdirerror.txt
6.	Urutkan kalimat berikut :
Jakarta
Bandung
Surabaya
Padang
Palembang
Lampung
Dengan menggunakan notasi here document (<@@@ ...@@@) . [HINT](https://www.geeksforgeeks.org/how-to-use-here-document-in-bash-programming/)
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/df54d003-5cb4-42d0-bef3-67e20ab4fb25)

Keterangan : “<<@@@” digunakan untuk mengurutkan secara alfabet dan ditutup dengan @@@.

7.	Hitung jumlah baris, kata dan karakter dari file baru.urut dengan menggunakan filter dan tambahkan data tersebut ke file baru.
 
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/4d40245f-f039-4727-8cad-cefa7426cfb8)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/26271498-95d3-4751-b5f2-6bba9f2f00a3)


Keterangan : Untuk menghidung jumlah baris, kata dan karakter kita harus menggunakan perintah wc -l untuk menghitung jumlah baris, wc -w untuk menghitaung jumlah kata, dan wc -c untuk menghitung jumlah karakter kemudian menggunakan perintah pengelompokan “{}” untuk memindahkan jumlah baris, kata dan karakter, menggunakan perintah “>>” untuk memindahkan file tersebut ke file Bernama baru.
8.	Gunakan perintah di bawah ini dan perhatikan hasilnya.
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
 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/5bc12f1a-95f2-4699-981d-342af767a082)

Keterangan : Perintah “cat > hello.txt” digunakan untuk membuat atau menulis ke file hello.txt. perintah “ cat hello.txt | sort | uniq “akan mengeluarkan hasil teks yang sudah diurutkan dan tidak mengandung baris yang sama, Perintah “cat hello.txt | grep "dog" | grep -v "cat" “, akan mencari baris-baris dalam file hello.txt yang mengandung kata "dog" tetapi tidak mengandung kata "cat".
LAPORAN RESMI:
1.	Analisa hasil percobaan 1 sampai dengan 4, untuk setiap perintah jelaskan tampilannya.
2.	Kerjakan latihan diatas dan analisa hasilnya
3.	Berikan kesimpulan dari praktikum ini.
Kesimpulan praktikum tersebut adalah kitab isa tau tentang perintah pembelokan standart input dan standartoutput, dan tau tentang perintah dasar seperti grep, wc, sort, cut dan uniq

