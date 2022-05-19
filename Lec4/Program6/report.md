The program creates an array of file descriptors.
The program will then check if the input is correct and print out an error message, if any:
if (argc != 2)
и
if (pipe(pipefd) == -1)


It will then call fork() of the child process to the PID of the child process. Next it will check the PID it has just obtained. The child has an ID of zero. Then the parent process will write something:
close(pipefd[0]);
write(pipefd[1], argv[1], strlen(argv[1]);
close(pipefd[1]);
wait(NULL);
exit(EXIT_SUCCESS);


And the child reads the data:
if (pid == 0)
{
close(pipefd[1]);
while (read(pipefd[0], & buf, 1) > 0)
write(STDOUT_FILENO, & buf, 1);
write(STDOUT_FILENO, "\n", 1);
close(pipefd[0]);
_exit(EXIT_SUCCESS);

Thus, communication between processes is done using a common channel.

