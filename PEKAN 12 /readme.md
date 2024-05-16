## Perbedaan Serial, Parallel, Concurent dan Concurent Parallel

1. [Parallek](#parallel)
2. [Concurent](#concurent)
3. [Concurent Parallel](#concurent-parallel)





## gambar judul
![WhatsApp Image 2024-05-14 at 09 03 30_70c6efc3](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/9106f52c-9d9b-4a64-8ddd-2fae76becb24)

## Parallel 

Parallel adalah beberapa proses / proses yang dilakukan secara bersamaan
Seperti contoh pada gambar diatas dimana core1 menjalankan task 1 dan core 2 menjalankan task 2 secara bersamaan.

contoh : 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/46409dcc-8174-45f8-a6df-4fe32154d5ba)

<br>Pada gambar ini Proses A dan Proses B menjalankan proses 1, proses 2, proses 3 secara bersamaan / dalam satu waktu 
Ksimpulan : Proses akan lebih efisien dengan membagi kerja sehingga dapat mempercepat waktu eksekusi keseluruhan tugas. 

## Concurent

Concurrent adalah sebuah proses yang dijalankan secara sekaligus secara bergantian , bukan seacara bersamaan tapi secara sekaligus. pada gambar {diatas} Core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalu core 1 menjalankan task 2.2 core 2 menjalankan task 1.2 dikarenakan proses task 1.2 belum selesai maka core 1 menjslankan task 2.3 lalu core 2 setelah proses dari task 1.2 selesai maka menjalankan proses task 1.3 lalu setelah core 1 selesai makan akan menjalankan proses setelahnya.

contoh : 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/f24e60c8-45d1-42c6-bd38-fa261ffb08df)
dari gambar di atas Proses A menjalankan task 1 lalu ketika task 1 selesai makan akan menjalankan proses lainya 

## Paraller dan Concurent



Concurrent and Parallel dijalankan secara bersamaan dan bergantian pada dua core.
seperti contoh pada gambar judul di atas core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalau setelah task 1.1 proses selesai lanjut mrnjalankan task 2.2 dan  dan 2.3 secara urut lalu pada core 2 selewsai menjalankan task 2.1 makan akan menjalankan task 1.2 dikarenakan task 1.1 sudah terisi oleh task 2.2 maka core 2 menjalankan task 1.2 dan 1.3 dan seterusnya   
Kesimpulan : penggunaan CPU yang lebih optimal utuk menjaga responsivitas sistem.
