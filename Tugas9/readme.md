## Tugas9

- [Install](#install)
- [Fork01](#fork01)
- [Fork02](#fork02)
- [Fork03](#fork03)


- Buat tulisan tentang konsep fork dan implementasinya dengan menggunakan bahasa pemrograman C! (minimal 2 paragraf disertai dengan gambar)
- Akses dan clonning repo : https://github.com/ferryastika/operatingsystem.git
- Deskripsikan dan visualisasikan pohon proses hasil eksekusi dari kode program fork01.c, fork02.c, fork03.c,

## Install

![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/eb152342-e3bd-456e-b238-d876eb4b35db)
lalu masuk ke superuser dengan mengetikan su -
lalu ketik sudo apt intsall gcc g++ 
jika terjadi eror atau tidak memiliki akses atau not sudoers file
anda bisa menambahkan Perintah sudo usermod -aG sudo (username) 
contoh
Perintah sudo usermod -aG sudo salisahmad akan menambahkan pengguna bernama "salisahmad" ke grup "sudo". Setelah mengeksekusi perintah ini, pengguna "salisahmad" akan memiliki akses sudo di sistem tersebut.

lalu ketikan sudo apt intsall gcc g++ 

Perintah sudo apt install gcc g++ adalah perintah yang digunakan untuk menginstal compiler GNU untuk bahasa pemrograman C dan C++ di sistem operasi berbasis Debian atau Ubuntu.

gcc adalah compiler untuk bahasa pemrograman C.
g++ adalah compiler untuk bahasa pemrograman C++.
![dbn2](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/b99f381f-d3cd-428f-9e45-deafed971129)

## fork01

 ketikan nano fork01.cpp lalu ketikan program berikut :

```
using namespace std;

#include <iostream>
#include <sys/types.h>
#include <unistd.h>


/* getpid() adalah system call yg dideklarasikan pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t mypid;
	uid_t myuid;
	for (int i = 0; i < 3; i++) {
		mypid = getpid();
		cout << "I am process " << mypid << endl;
		cout << "My parent process ID is " << getppid() << endl;
		cout << "The owner of this process has uid " << getuid()
	<< endl;
/* sleep adalah system call atau fungsi library
yang menghentikan proses ini dalam detik
*/
	sleep(3);
	}
return 0;
}
```
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/a394e858-308c-499a-8b77-cf4542881dca)

lalu untuk keluar krtikan ctrl x untuk exit lalu pilih y untuk mrngrsave dan enter 
lalu ketikan Perintah g++ fork01.cpp -o forko1
perintah tersebut untuk mengkompilasi program C++ yang disebut "fork01.cpp" menggunakan compiler g++ dan memberikan output dengan nama "fork01".
lalu ketikan ./fork01 untuk menjalankan program tersebut

![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/aeacbfca-743b-46b4-bf04-909133523290)

Output program ini menampilkan ID proses (PID), ID proses parent (PPID), dan ID pengguna (UID). Setelah mencetak informasi tersebut, program akan berhenti selama tiga detik sebelum mencetak informasi lagi. Program ini looping sebanyak tiga kali.



## fork02

ketikan nano fork02.cpp 
lalu ketikan kode berikut :


```
#include <iostream>
#include <sys/types.h>
#include <unistd.h>
using namespace std;


/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/

int main(void) {
	pid_t childpid;
	int x = 5;
	childpid = fork();

	while (1) {
		cout << "This is process ID" << getpid() << endl;
		cout << "In this process the value of x becomes " << x << endl;	
		sleep(2);
		x++;
	}
	return 0;
}
```
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6d67d26c-374a-4a10-9116-22c6960c21f9)
lalu jalankan seperti contoh fork01 <br>
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2058b1d0-31bc-404c-9ef2-f04695b906f4)
Output program menampilkan ID proses (PID) mereka sendiri dan nilai variabel x dalam loop tak terbatas. Program menggunakan system call fork() untuk membuat proses saat ini, dan menciptakan child process.

## fork03

ketikan nano fork03.cpp 
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/a4e20de9-fcb6-4717-9e6c-42b33fbef611)

lalu ketikan kode berikut :

```
#include <iostream>
using namespace std;
#include <sys/types.h>
#include <unistd.h>

/* getpid() dan fork() adalah system call yg dideklarasikan
pada unistd.h.
Menghasilkan suatu nilai dengan type pid_t.
pid_t adalah type khusus untuk process id yg ekuivalen dg int
*/
int main(void) {
	pid_t childpid;
	childpid = fork();
	for (int i = 0; i < 5; i++) {
		cout << "This is process " << getpid() << endl;
		sleep(2);
	}
	return 0;
}
```
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/6fe30bdc-6ed4-4bb7-8464-a40fe63f24a4)

lalu ketkan perintah ./fork03 untuk menjalankan program

Analisa

Output program diatas melakukan proses forking secara looping (berulang) sebanyak 5 kali, yang menghasilkan proses-proses baru dengan pesan yang mencatat ID proses (PID) masing-masing. Adanya beberapa PID yang berulang menandakan bahwa parent process melakukan fork beberapa kali, menghasilkan proses-proses child dengan PID yang sama.




