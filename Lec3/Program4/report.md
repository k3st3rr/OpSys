First the program (Program4) calls the fork() function, which creates a child process:
int pid = fork();


Then the program prints the PID of the process it is in:
printf("my pid =%i, returned pid =%i\n", getpid(), pid);
