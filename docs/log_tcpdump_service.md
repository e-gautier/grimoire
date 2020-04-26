# tcpdump as a service with log and rotation

```
[Unit]
Description=TCPDUMP logging and rotation

[Service]
Environment="TCPDUMPROTATEFILECOMMAND=/tmp/tcpdumprotatefilecommand"
Environment="OUTPUT=/tmp/output"
Environment="PORT=8000"
Environment="ROTATIONTIME=3600"
Environment="IFACE=lo"
ExecStartPre=/bin/su -c '\
/usr/bin/printf "#!/bin/sh\nmv \\$1 ${OUTPUT}" > ${TCPDUMPROTATEFILECOMMAND} && /bin/chmod +x ${TCPDUMPROTATEFILECOMMAND}\
'
ExecStart=/usr/sbin/tcpdump -i ${IFACE} -w /tmp/tcpdump-%%d-%%m-%%Y-%%H-%%M-%%S -z ${TCPDUMPROTATEFILECOMMAND} -G ${ROTATIONTIME} tcp[tcpflags] == tcp-syn or udp and port ${PORT}
ExecStopPost=/bin/rm -f ${TCPDUMPROTATECOMMAND}
Restart=always

[Install]
WantedBy=multi-user.target
```
**ExecStartPre** create `/tmp/tcpdumprotatefilecommand` which is a script that contains:
```
#!/bin/sh
mv $1 /tmp/output
```
**ExecStopPost** delete it.
```
# only TCP syn packets and datagrams
tcp[tcpflags] == tcp-syn or udp and port ${PORT}
```
```
# write a pcap with a date format
-w /tmp/tcpdump-%%d-%%m-%%Y-%%H-%%M-%%S
```
```
# rotate it every ROTATIONTIME seconds
-G ${ROTATIONTIME}
```
```
# then run TCPDUMPROTATEFILECOMMAND passing the rotated file in arg
-z ${TCPDUMPROTATEFILECOMMAND}
```