## Problem

1. [Bounded-Buffer Problem](#bounded-buffer-Problem)
2. [Readers and Writers Problem](#readers-and-writers-problem)
3. [Dining-Philosopher 's Problem](#dining-philosopher-s-problem)

## Bounded-Buffer Problem

![WhatsApp Image 2024-05-14 at 09 41 43_e53949bd](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/db2f56c7-7062-403a-92c1-f0a1c76e7882)


masalah bounded buffer ini adalah proses di antara produsen dan konsumen. Kendala yang dari masalah ini yaitu penjadwalan (scheduling) dan mutual exclusion (mutex) seperti konsumen harus menunggu jika ada buffer kosong , produsen harus menunggu jika buffer sedang penuh, dan hanya satu buffer yang dapat memanipulasi buffer tersebut .Dengan kata lain, terdapat samber daya yang terbatas dan produsen mengisikan (write)harus produknya ke dalam sumber daya tersebut . Sedangkan konsumen akan mengambil (read)) sumber daya yang penuh tersebut dan meninggalkannya pada sumber daya yang kosong. Kompleksitas utama dari masalah tersebut adalah menjaga perhitungan jumlah ketersediaan sumber daya yang kosong ataupun penuh<br>
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
  

## Dining Philosopher s Problem
   Ini adalah pendahuluan.

