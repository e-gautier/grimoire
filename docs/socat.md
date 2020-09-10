# socat

socat redirect from/to:
- file
- socket (rw & stream)
- process stdin
- IP/TCP/UDP/SSL/SOCKS/HTTP packet
- unix pipe
- TTY/PTY
- interface

redirect tcp co to file:
```bash
socat -dd -u TCP-LISTEN:1234 CREATE:tcpdump
```

replay it to a host:
```bash
socat -dd -u OPEN:/tmp/tcpdump TCP:127.0.0.1:1234
```

capture network connections and send them to our tty:
```bash
socat -dd -u TCP-LISTEN:1234 STDOUT
```

redirect tcp stream listened from port 1234 to host:post while passing through socks server:
```bash
socat -dd TCP-LISTEN:1234,reuseaddr,fork,bind=127.0.0.1 SOCKS:<proxy server>:<host>:<port>,socksport=<proxy port>
```
redirect a TCP connection to a simple HTTP server
```bash
socat TCP-LISTEN:1234,reuseaddr,fork SYSTEM:"echo HTTP/1.1 200 OK;echo;cat index.html"
```
UDP on TCP to get through some proxies
```bash
# server side
socat TCP-LISTEN:1234,reuseaddr,fork UDP:127.0.0.1:53

# client side
socat udp4-RECVFROM:53,reuseaddr,fork tcp:127.0.0.1:1234
```