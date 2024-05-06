## TUGAS 10 FORKING, ORPHAN, ZOMBIE - TUGAS MENERJEMAHKAN

[forking, orphan, zombi](#cloning)
- [forking](#forking)
- [orphan](#orphan)
- [zombie](#zombie)

[Producer Consumen Problem in C](#producer-consumen)

## cloning

Langkah pertama yaitu clone terlebih dahulu ke github dengan mengetik git clone https://github.com/ferryastika/operatingsystem.git
<br>lalu masuk ke directory operatingsystem dengan menggunakan perintah cd operatingsystem lalu jalankan perintah  yang ada pada soal

## forking 


![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/cc673bd1-d3de-4201-afd0-2912bd1530fb)
```
#include <sys/types.h>
#include <stdio.h>
#include <unistd.h>
int main()
{
pid_t pid;

	/* fork a child process */
	pid = fork();
	if (pid < 0) { /* error occurred */
		fprintf(stderr, "Fork Failed");
	return 1;
	}
	else if (pid == 0) { /* child process */
		execlp("/bin/ls","ls",NULL);
	}
	else { /* parent process */
		/* parent will wait for the child to complete */
		wait();
		printf("Child Complete");
	}
return 0;

}
```

![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/76d15469-5439-445f-a445-1bba8299fefe)
Output dari program ini akan menampilkan daftar file dalam direktori saat ini, karena Child process menjalankan perintah ls. Namun, pesan "Child Complete" tidak akan langsung tercetak setelah itu, karena parent process menunggu hingga child process selesai sebelum mencetak pesan tersebut.

## orphan

ketikan program berikut :
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/07605afa-10be-4035-b9cd-67c17bd15faf)
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
	// fork() Create a child process

	int pid = fork();
	if (pid > 0)
	{
		//getpid() returns process id
		// while getppid() will return parent process id
		printf("Parent process\n");
		printf("ID : %d\n\n",getpid());
	}
	else if (pid == 0)
	{
		printf("Child process\n");
		// getpid() will return process id of child process
		printf("ID: %d\n",getpid());
		// getppid() will return parent process id of child process
		printf("Parent -ID: %d\n\n",getppid());

		sleep(10);

		// At this time parent process has finished.
		// So if u will check parent process id 
		// it will show different process id
		printf("\nChild process \n");
		printf("ID: %d\n",getpid());
		printf("Parent -ID: %d\n",getppid());
	}
	else
	{
		printf("Failed to create child process");
	}
	
	return 0;
}

/* https://www.includehelp.com/c-programs/orphan-process.aspx */
```
lalu masukan perintah
<br> lalu masukan perintah g++ orphan.c -o orphan
untuk menjalankan  ketikan ./orphan
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/e877ba99-2442-4fdd-9c4a-577b86692f98)
orphan.c output program tersebut yaitu menjalankan Parent process dan Child process

## zombie

![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/89f684da-2b58-4984-a224-acf2e8a85fd9)
```

#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
int main ()
{
  pid_t child_pid;

   /* Create child*/
  child_pid = fork ();
  if (child_pid > 0) {

    /* Parent process */
    sleep (60);
  }
  else {

    /*Child process. Exit immediately. */
    exit (0);
  }
  return 0;
}

/*ps -e -o pid,ppid,stat,cmd */
```
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/282a1280-507f-4a8f-9290-29b06f742726)
![image](https://github.com/StalisAhmadSholeh/SysOP24-3123521010/assets/160557634/d87c19ef-47bc-423f-9fba-7833d186bc55)

zombie.c output program tersebut yaitu Program ini membuat proses menggunakan fork(), dan jika proses tersebut parent process, maka ia akan tidur selama 60 detik (sleep(60)). Namun, jika proses tersebut adalah child process, maka program akan keluar secara langsung


