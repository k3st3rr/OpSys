First, the program creates a handle and a channel with access rights for everyone:
int fd;
int len;
char buf[BUFSIZE];
if (mkfifo(NAMEDPIPE_NAME, 0777))
{
perror("mkfifo");
return 1;
}



After that, an infinite loop is started in which the application listens to it:
do {
memset(buf, '\0', BUFSIZE);
if ((len = read(fd, buf, BUFSIZE - 1)) <= 0)
{
error("read error");
close(fd);
remove(NAMEDPIPE_NAME);
return 0;
}
printf("Incoming message (%d): %s\n", len, buf);
} while (1);


If the program received the message:
if ((len = read(fd, buf, BUFSIZE - 1)) <= 0)</ br> The number of characters is output (taking into account the terminal zero) and the text itself.
