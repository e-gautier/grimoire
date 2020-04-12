* trace specific system call: `strace -e open ls`
* trace specific signal: `strace -e signal=SIGTERM ls`
* trace multiple system call: `strace -e trace=open,read,write ls`
* follow forks: `strace -f ls`
* trace output: `strace -o output.txt ls`
* trace a specific running linux process: `sudo strace -p <pid>`
* print timestamp: `strace -t ls`
* generate stats: `strace -c ls`