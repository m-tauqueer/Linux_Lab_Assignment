# Question 4 - Commands, Outputs, and Observations

## Command 1

```bash
echo "Application log entry 1" > app.log
echo "Application log entry 2" >> app.log
```

Output:

```text
No output
```

Observation: These commands create a log file and append a second entry. The > operator overwrites; >> appends to the existing file.

## Command 2

```bash
cat app.log
```

Output:

```text
Application log entry 1
Application log entry 2
```

Observation: This command displays the log file contents. Both entries were written successfully using output redirection.

## Command 3

```bash
ls -l /proc/$fish_pid/fd
```

Output:

```text
lrwx------ 1 tauqueer tauqueer 64 Jul  3 12:09 0 -> /dev/pts/1
lrwx------ 1 tauqueer tauqueer 64 Jul  3 12:09 1 -> /dev/pts/1
lrwx------ 1 tauqueer tauqueer 64 Jul  3 12:09 2 -> /dev/pts/1
lrwx------ 1 tauqueer tauqueer 64 Jul  3 12:09 10 -> anon_inode:inotify
lrwx------ 1 tauqueer tauqueer 64 Jul  3 12:09 11 -> anon_inode:[eventfd]
lrwx------ 1 tauqueer tauqueer 64 Jul  3 12:09 12 -> anon_inode:[eventfd]
```

Observation: This command lists all open file descriptors for the current shell. Descriptors 0, 1, and 2 are stdin, stdout, and stderr, all connected to the terminal device /dev/pts/1.

## Command 4

```bash
echo "This is standard output" > stdout.log
```

Output:

```text
No output
```

Observation: This command redirects standard output to stdout.log instead of printing to the terminal.

## Command 5

```bash
ls /nonexistent_path_12345 2> stderr.log
```

Output:

```text
No terminal output (error sent to file)
```

Observation: This command redirects stderr to stderr.log. The error from the failed ls command was captured in the file rather than displayed on screen.

## Command 6

```bash
cat stdout.log
```

Output:

```text
This is standard output
```

Observation: This command confirms that stdout redirection worked and the text was saved to the file.

## Command 7

```bash
cat stderr.log
```

Output:

```text
"ls: /nonexistent_path_12345": No such file or directory (os error 2)
```

Observation: This command confirms that stderr redirection captured the error message from the failed ls command.

## Command 8

```bash
ulimit -n
```

Output:

```text
1024
```

Observation: This command shows the soft limit for the maximum number of open file descriptors. A process can have up to 1024 files open at once by default.

## Command 9

```bash
cat /proc/self/limits
```

Output:

```text
Max open files            1024                 524288               files
Max processes             62508                62508                processes
Max file size             unlimited            unlimited            bytes
```

Observation: This command displays all resource limits for the current process. The soft limit for open files is 1024 but the hard limit allows up to 524288.

## Command 10

```bash
sleep 60 < app.log &
```

Output:

```text
No output (background job started)
```

Observation: This command starts a background process with app.log redirected to its standard input, so we can inspect which files it has open.

## Command 11

```bash
lsof app.log
```

Output:

```text
COMMAND    PID     USER FD   TYPE DEVICE SIZE/OFF    NODE NAME
sleep   131289 tauqueer 0r   REG  259,5       48 4106868 app.log
```

Observation: This command lists processes that have app.log open. The sleep process (PID 131289) has file descriptor 0 open for reading the log file.

## Command 12

```bash
kill %1
```

Output:

```text
fish: Job 1, 'sleep 60 < app.log &' terminated by signal SIGTERM (Polite quit request)
```

Observation: This command terminates the background sleep process, releasing its hold on app.log.
