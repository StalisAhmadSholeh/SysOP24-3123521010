## Tugas9

Buat tulisan tentang konsep fork dan implementasinya dengan menggunakan bahasa pemrograman C! (minimal 2 paragraf disertai dengan gambar)
Akses dan clonning repo : https://github.com/ferryastika/operatingsystem.git
Deskripsikan dan visualisasikan pohon proses hasil eksekusi dari kode program fork01.c, fork02.c, fork03.c,

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
![dbn3](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/e89c4d7d-a7c4-4dfe-b580-6e97a83ad407)
Analisa

Output program ini menampilkan ID proses (PID), ID proses parent (PPID), dan ID pengguna (UID). Setelah mencetak informasi tersebut, program akan berhenti selama tiga detik sebelum mencetak informasi lagi. Program ini looping sebanyak tiga kali.


lalu ketikan nano fork01.cpp lalu ketikan program berikut :
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

lalu untuk keluar krtikan ctrl x untuk exit lalu pilih y untuk mrngrsave dan enter 
lalu ketikan Perintah g++ fork01.cpp -o forko1.exe
perintah tersebut untuk mengkompilasi program C++ yang disebut "fork01.cpp" menggunakan compiler g++ dan memberikan output dengan nama "fork01.exe".
lalu ketikan ./fork01.exe untuk menjalankan program tersebut
Analisa

Output program menampilkan ID proses (PID) mereka sendiri dan nilai variabel x dalam loop tak terbatas. Program menggunakan system call fork() untuk membuat proses saat ini, dan menciptakan child process.

![dbn6](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/2cbd4164-085e-45b3-9365-5ccd449f1776)

untuk yang ke 2 dan ke 3 caranya sama seperti fork1 

ketikan nano fork02.cpp 
lalu ketikan kode berikut :
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
lalu jalankan seperti contoh fork01
![dbn4](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/3fd07bd3-7c77-4524-87de-d40b10ca5b08)
![dbn7](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/68d3234a-2a29-4859-bd61-d3586bb97146)

ketikan nano fork02.cpp 
lalu ketikan kode berikut :
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
Analisa

Output program diatas melakukan proses forking secara looping (berulang) sebanyak 5 kali, yang menghasilkan proses-proses baru dengan pesan yang mencatat ID proses (PID) masing-masing. Adanya beberapa PID yang berulang menandakan bahwa parent process melakukan fork beberapa kali, menghasilkan proses-proses child dengan PID yang sama.



![dbn5](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/b28906ad-60cb-49fd-8b82-eafa3027b87b)
![dbn8](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/a53d3bb6-7733-41af-a9a2-cc349f14737f)

