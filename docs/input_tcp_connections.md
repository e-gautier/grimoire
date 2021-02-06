# Log incoming TCP connections with tcpdump

```bash
tcpdump \
	-n \
	-i eth0 \
	dst YOUR.LOCAL.IP.ADDRESS \
		and "tcp[tcpflags] & (tcp-syn) != 0 and tcp[tcpflags] & (tcp-ack) = 0"
```
