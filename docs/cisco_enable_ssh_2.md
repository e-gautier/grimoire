# Enable SSH lib v2 on a Cisco device

```
enable
```
```
conf t
```
```
crypto key generate rsa label ssh modulus 4096 usage-keys
```
```
ip ssh rsa keypair-name ssh
```
```
ip ssh version 2
```