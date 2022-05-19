Allocate memory for an array of char elements:
char * c = (char * ) calloc(100, sizeof(char));


Then the application opens the file foo.txt to read or create:
int fd = open("foo.txt", O_RDONLY | O_CREAT);


After that the value of the file descriptor is printed:
printf("fd = %d/n", fd);.


The application will read 10 bytes from the file and write the resulting amount of information into the sz variable:
sz = read(fd, c, 10);


The application will write the terminal zero c[sz] = '\0' to the end of the array and close the file:
if (close(fd) < 0)
{
perror("close file error:");
exit(1);
}

