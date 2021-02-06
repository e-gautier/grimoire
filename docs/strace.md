# strace
|||
| :- | :- |
| `strace -e open ls` | trace specific system call |
| `strace -e signal=SIGTERM ls` | trace specific signal |
| `strace -e trace=open,read,write ls` | trace multiple system call |
| `strace -f ls` | follow forks |
| `strace -y ls` | resolve file names from file descriptor ids |
| `strace -o output.txt ls` | trace output |
| `sudo strace -p <pid>` | trace a specific running linux process |
| `strace -t ls` | print timestamp |
| `strace -c ls` | generate stats |