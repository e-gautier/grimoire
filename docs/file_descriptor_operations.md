# File descriptor operations
Recover an open file:
```bash
cat >> /tmp/important.txt &
[1] 22626

rm -rf /tmp/important.txt
ls -l /proc/22626/fd/
lrwx------ 1 root root 64 Feb  3 19:03 0 -> /dev/pts/2
l-wx------ 1 root root 64 Feb  3 19:03 1 -> '/tmp/important.txt (deleted)'
lrwx------ 1 root root 64 Feb  3 19:03 2 -> /dev/pts/2

cat /proc/22626/fd/1 > /tmp/recover.txt
```
Write to a process std:
```bash
echo "hello" > /proc/21551/fd/0

# where 21551 is the pid of the process and 0 the stdin (1 stdout, 2 stderr)
```