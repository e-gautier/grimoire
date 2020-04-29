# Write to a process std
```bash
echo "hello" > /proc/21551/fd/0

# where 21551 is the pid of the process and 0 the stdin (1 stdout, 2 stderr)
```