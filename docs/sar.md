# sar
- CPU activity: `sar -P ALL 1`
- Load activity: `sar -q 1`
- Memory activity: `sar -rh 1`
- Swap activity: `sar -Sh 1`
- I/O activity: `sar -b 1`
- Network activity: `sar -n DEV 1` (Possible keywords are DEV, EDEV, FC, ICMP, EICMP, ICMP6, EICMP6, IP, EIP, IP6, EIP6, NFS, NFSD, SOCK, SOCK6, SOFT, TCP, ETCP, UDP and UDP6).
