At the beginning the program receives a signal from the user and processes it.
Then the global variable counter is set:
int counter = 0;


There are also two processing functions in the program, handler1:
void handler1(int sig)
{
counter++;
printf("counter = %d\n", counter);
/* Output the printed string to stdout */
fflush(stdout);
kill(pid, SIGUSR1);
}


And the handler2 function:
void handler2(int sig)
{
counter += 3;
printf("counter = %d\n", counter);
exit(0);
}

Handling: The program binds the first handler function to the current process.
Next, if the process happens to be a child, the handler2 function will handle the signal.

