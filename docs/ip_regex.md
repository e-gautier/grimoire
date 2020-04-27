# IP REGEX
```regex
/^(?:(25[0-5]|2[0-4]\d|1\d\d|[1-9]\d|\d)\.){3}(?1)$/m
```
Long version:
```regex
/^(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]\d|\d)(?:\.(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]\d|\d)){3}$/m
```
tested on those:
```
0.0.0.0
1.2.3.4
10.3.90.255
255.255.255.255
99.204.254.254
1.1.1.512
200.200.0.30
199.199.199.199
9.9.9.90
1.1.1.206
248.230.102.2
248.230.102.2.
248.230.102.2.1
1.1.1.1.1
1.1.1
1111
1..1..1..1
512.512.512.512
00.1.1.1
```