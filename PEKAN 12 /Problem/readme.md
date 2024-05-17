## Problem

1. [Bounded-Buffer Problem](#bounded-buffer-Problem)
2. [Readers and Writers Problem](#readers-and-writers-problem)
3. [Dining-Philosopher 's Problem](#dining-philosopher-s-problem)

## Bounded-Buffer Problem

![WhatsApp Image 2024-05-14 at 09 41 43_e53949bd](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/db2f56c7-7062-403a-92c1-f0a1c76e7882)


masalah bounded buffer ini adalah proses di antara produsen dan konsumen. Kendala yang dari masalah ini yaitu penjadwalan (scheduling) dan mutual exclusion (mutex) seperti konsumen harus menunggu jika ada buffer kosong , produsen harus menunggu jika buffer sedang penuh, dan hanya satu buffer yang dapat memanipulasi buffer tersebut .Dengan kata lain, terdapat samber daya yang terbatas dan produsen mengisikan (write)harus produknya ke dalam sumber daya tersebut.<br> Sedangkan konsumen akan mengambil (read)) sumber daya yang penuh tersebut dan meninggalkannya pada sumber daya yang kosong. Kompleksitas utama dari masalah tersebut adalah menjaga perhitungan jumlah ketersediaan sumber daya yang kosong ataupun penuh<br>
Untuk mengatasi masalah tersebut.dibutuhkan semaphore yang berfungsi sebagai penjaga agar produsen tidak mengakses sumber
Untuk mengatasi masalah sinkronisasi pada bounded buffer problem yaitu Semaphore, Semaphore digunakan untuk mengatur akses produsen dan konsumen terhadap sumber daya. semaphore membantu menjaga ketersediaan sumber daya yang kosong atau penuh serta mengatur akses produsen dan konsumen secara aman.

```
#include<stdio.h>
#include<stdlib.h>
 
int mutex=1,full=0,empty=3,x=0;
 
int main()
{
	int n;
	void producer();
	void consumer();
	int wait(int);
	int signal(int);
	printf("\n1.Producer\n2.Consumer\n3.Exit");
	while(1)
	{
		printf("\nEnter your choice:");
		scanf("%d",&n);
		switch(n)
		{
			case 1:	if((mutex==1)&&(empty!=0))
						producer();
					else
						printf("Buffer is full!!");
					break;
			case 2:	if((mutex==1)&&(full!=0))
						consumer();
					else
						printf("Buffer is empty!!");
					break;
			case 3:
					exit(0);
					break;
		}
	}
	
	return 0;
}
 
int wait(int s)
{
	return (--s);
}
 
int signal(int s)
{
	return(++s);
}
 
void producer()
{
	mutex=wait(mutex);
	full=signal(full);
	empty=wait(empty);
	x++;
	printf("\nProducer produces the item %d",x);
	mutex=signal(mutex);
}
 
void consumer()
{
	mutex=wait(mutex);
	full=wait(full);
	empty=signal(empty);
	printf("\nConsumer consumes item %d",x);
	x--;
	mutex=signal(mutex);
}


/*

Producer consumer problem is also known as bounded buffer problem. In this problem we have two processes, producer and consumer, who share a fixed size buffer. Producer work is to produce data or items and put in buffer. Consumer work is to remove data from buffer and consume it. We have to make sure that producer do not produce data when buffer is full and consumer do not remove data when buffer is empty.

The producer should go to sleep when buffer is full. Next time when consumer removes data it notifies the producer and producer starts producing data again. The consumer should go to sleep when buffer is empty. Next time when producer add data it notifies the consumer and consumer starts consuming data. This solution can be achieved using semaphores.
*/
```

Pada implementasi ini, ketika buffer penuh, produsen akan masuk ke dalam mode tidur. Ketika konsumen menghapus data dari buffer, ia memberi tahu produsen sehingga produsen dapat mulai menghasilkan data lagi. Begitu juga sebaliknya, ketika buffer kosong, konsumen akan masuk ke dalam mode tidur. Ketika produsen menambahkan data ke dalam buffer, ia memberi tahu konsumen sehingga konsumen dapat mulai mengonsumsi data. Solusi ini dapat dicapai menggunakan  Semaphore.

## Readers and Writers Problem

Reader-Writer Problem ini menggambarkan situasi di mana beberapa proses (pembaca dan penulis) harus mengakses sumber daya bersama (misalnya, basis data) dengan cara tertentu.

Pembaca: Beberapa pembaca dapat membaca data secara bersamaan.

Penulis: Penulis membutuhkan akses eksklusif ke data. Ketika penulis sedang menulis, tidak ada pembaca atau penulis lain yang boleh mengakses data. 

Untuk menangani masalah ini, harus dipastikan bahwa tidak ada proses bersamaan yang menyebabkan segala bentuk ketidakkonsistenan data dalam sistem operasi.

![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2dba1d4a-c419-4a33-80d3-e84c41d2fc3e)


```
 #include <pthread.h>
 #include <semaphore.h>
 #include <stdio.h>
 #include <unistd.h>

 sem_t rw_mutex;  // Semaphore for writers
 sem_t mutex;     // Semaphore for reader count
 int read_count = 0;

 void* reader(void* arg) {
 int id = *(int*)arg;

 while (1) {
    sem_wait(&mutex);
    read_count++;
    if (read_count == 1)
        sem_wait(&rw_mutex);
    sem_post(&mutex);

    printf("Reader %d is reading\n", id);
    sleep(1);

    sem_wait(&mutex);
    read_count--;
    if (read_count == 0)
        sem_post(&rw_mutex);
    sem_post(&mutex);

    sleep(1);
  }
 }

 void* writer(void* arg) {
 int id = *(int*)arg;

 while (1) {
    sem_wait(&rw_mutex);

    printf("Writer %d is writing\n", id);
    sleep(1);

    sem_post(&rw_mutex);

    sleep(1);
  }
 }

 int main() {
 pthread_t rtid[5], wtid[2];
 int ids[5] = {1, 2, 3, 4, 5};
 int writer_ids[2] = {1, 2};

 sem_init(&rw_mutex, 0, 1);
 sem_init(&mutex, 0, 1);

 for (int i = 0; i < 5; i++)
    pthread_create(&rtid[i], NULL, reader, &ids[i]);
 for (int i = 0; i < 2; i++)
    pthread_create(&wtid[i], NULL, writer, &writer_ids[i]);

 for (int i = 0; i < 5; i++)
    pthread_join(rtid[i], NULL);
 for (int i = 0; i < 2; i++)
    pthread_join(wtid[i], NULL);

 sem_destroy(&rw_mutex);
 sem_destroy(&mutex);

 return 0;
 }

```

Untuk mengatasi permasalahan ini , terdapat 3 solusi yang dapat dilakukan. <br>
1.solusi dengan memprioritaskan pembaca. Solusi ini tepat digunakan jika tujuan yang ingin dicapai adalah memperoleh throughput semaksimal mungkin Solusi ini bekerja dengan lebih memprioritaskan pembaca meskipun sudah banyak writer yang mengantri.

2.solusi dengan memprioritaskan penulis. Pada solusi ini, jika tidak ada yang mengaksess berkas maka penulis akan mengakses berkas dan pembaca akan dibiarkan mengantri sampai semua penulis menyelesaikan tugasnya . Keuntungan solusi ini adalah pembaca dapat memperoleh informasi yang selau up-to-date. Namun , kedua solusi tersebut tidak memenuhi syarat bahwa setiap thread tidak boleh dibiarkan menunggu untuk waktu yang tidak terbatas.

3.Solusi yang ketiga adalah pembaca dan penulis memperoleh prioritas yang sama secara bergantian. Pada solusi ini, penulis dan pembaca diberi giliran yang adil dalam hal pengaksesan berkas . Jika tidak ada thread pembaca yang sedang mengakses penulis dapat mengaksesnya. Dan jika selesai maka akan memberikan gilira pembaca untuk mengakses berkas . Dengan solusi ini., tidak ada thread yang dalam waktu yang tidak terbatas maka cara ini merupakan cara yang tepat ui menyelesaikan masalah konkurensi.


## Dining Philosopher s Problem
   

Dining Philosopher s Problem adalah masalah klasik dalam ilmu komputer yang menggambarkan sinkronisasi dan deadlock dalam sistem konkuren. Diperkenalkan oleh Edsger Dijkstra pada tahun 1965, masalah ini menggambarkan situasi di mana lima filsuf duduk di meja bundar dengan satu piring spaghetti di depan masing-masing. Ada garpu di antara setiap dua filsuf, dan setiap filsuf membutuhkan dua garpu untuk makan.


![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/f25dffc8-d8b8-473f-8d5e-ffe43c6f35a6)

Solusi Waiter
Solusi sederhana ini dilakukan dengan mengadakan seorang waiter yang senantiasa mengawasi penggunaan sumpit di meja makan. Ketika empat buah (dua pasang) sumpit sedang dipakai, orang berikutnya yang ingin memakai sumpit harus meminta izin kepada sang waiter, yang hanya dapat diberi ketika salah satu sumpit telah selesai terpakai.

Contoh: Misalkan ke-lima orang tersebut dinamakan dari A sampai E secara berurutan.

Ketika A dan C sedang makan, 4 buah sumpit sedang terpakai. B tidak memiliki kedua sumpit, dan D dan E memiliki satu buah sumpit diantara mereka.

Apabila D ingin makan dan mengambil sumpit ke-lima, deadlock sangat mungkin terjadi . Maka waiter akan meminta D untuk menunggu, hingga pada saat salah satu sumpit telah selesai dipakai.

```
 #include <pthread.h>
 #include <semaphore.h>
 #include <stdio.h>
 #include <unistd.h>

 #define N 5

 sem_t forks[N];

 void* philosopher(void* num) {
 int id = *(int*)num;

 while (1) {
    printf("Philosopher %d is thinking\n", id);
    sleep(1);
    
    // Take forks
    sem_wait(&forks[id]);
    sem_wait(&forks[(id + 1) % N]);

    printf("Philosopher %d is eating\n", id);
    sleep(1);

    // Put down forks
    sem_post(&forks[id]);
    sem_post(&forks[(id + 1) % N]);
   }
 }  

 int main() {
 pthread_t thread[N];
 int ids[N];

 for (int i = 0; i < N; i++)
    sem_init(&forks[i], 0, 1);

 for (int i = 0; i < N; i++) {
    ids[i] = i;
    pthread_create(&thread[i], NULL, philosopher, &ids[i]);
 }

 for (int i = 0; i < N; i++)
    pthread_join(thread[i], NULL);

 for (int i = 0; i < N; i++)
    sem_destroy(&forks[i]);

  return 0;
 }
```

Dari code di atas pada setiap garpu direpresentasikan oleh sebuah semafor. Ketika seorang filsuf ingin makan, ia harus mengambil dua garpu (semafor) secara bersamaan. Setelah selesai makan, ia meletakkan kembali kedua garpu tersebut untuk digunakan oleh filsuf lain.

