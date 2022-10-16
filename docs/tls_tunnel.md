# TLS tunnel (using socat)
```bash
man socat
```
## server side
```bash
openssl genrsa -out server.key 4096
openssl req -new -key server.key -x509 -out server.crt
cat server.key server.crt > server.pem
# give server.crt to the client
# protect 127.0.0.1:1234 behind TLS:4443
socat OPENSSL-LISTEN:4443,fork,reuseaddr,cert=server.pem,cafile=client.crt TCP:127.0.0.1:1234
```
## client side
```bash
openssl genrsa -out client.key 4096
openssl req -new -key client.key -x509 -out client.crt
cat client.key client.crt > client.pem
# give client.crt to the server
# open 127.0.0.1:1234 and redirect to TLS:<server ip>:4443 (verify=0 to ignore common name)
socat TCP-LISTEN:1234,fork,reuseaddr OPENSSL:<server ip>:4443,cert=client.pem,cafile=server.crt,verify=0
# connect
nc 127.0.0.1 1234
```