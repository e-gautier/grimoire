# Linux sockets
[socket(2)](https://man7.org/linux/man-pages/man2/socket.2.html)
[bind(2)](https://man7.org/linux/man-pages/man2/bind.2.html)
[address_families(7)](https://man7.org/linux/man-pages/man7/address_families.7.html)
[unix(7)](https://man7.org/linux/man-pages/man7/unix.7.html)
[ip(7)](https://man7.org/linux/man-pages/man7/ip.7.html)

> AF: Address Families

> PF: Protocol Families

> Note: Family and type are not dependant, type is the communication semantics.

## Families and types (not exhaustive)

- IP (AF_INET/AF_INET6) Layer 3 communication
  - UDP (SOCK_DGRAM) connectionless, unreliable, datagrams
    > udp_socket = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);
  - UDPLite (SOCK_DGRAM)
    > sockfd = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDPLITE);
  - TCP (SOCK_STREAM) connection-based, reliable, sequenced, congestion management
    > tcp_socket = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)
  - SCTP (SOCK_SEQPACKET)
    > sctp_socket = socket(AF_INET, SOCK_STREAM, IPPROTO_SCTP);
  - RAW (SOCK_RAW) requires **CAP_NET_RAW** capability (eg. `getcap /usr/bin/ping` -> `/usr/bin/ping = cap_net_admin,cap_net_raw+p`)
    > raw_socket = socket(AF_INET, SOCK_RAW, protocol);
- Unix/Local (AF_UNIX) local communication
  - SOCK_STREAM, RAW etc..
- Netlink (AF_NETLINK) userspace to kernelspace communications
  - NETLINK_NETFILTER (netfilter configuration communication)
  - NETLINK_ROUTE (routing configuration communication)
- Packet (AF_PACKET) layer 2 communication (eg. bound to an interface)
- Bluetooth (AF_BLUETOOTH) bluetooth low level communication
- CAN (AF_CAN) CAN bus communication
- Kernel Crypto API (AF_ALG) kernel crypto API communication
- SELinux etc..