# Virtualbox tips
Map a disk to a virtual one:
```
VBoxManage internalcommands createrawvmdk -filename /tmp/disk.vmdk -rawdisk /dev/sdb
```
