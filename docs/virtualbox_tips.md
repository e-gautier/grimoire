# Virtualbox tips
Map a disk to a virtual one:
Unix:
```bash
VBoxManage internalcommands createrawvmdk -filename /tmp/disk.vmdk -rawdisk /dev/sdb
```
Windows:
```powershell
wmic diskdrive list brief

Caption                 DeviceID            Model                   Partitions  Size
Crucial_CT512MX100SSD1  \\.\PHYSICALDRIVE0  Crucial_CT512MX100SSD1  1           512105932800
```
```powershell
&"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" internalcommands createrawvmdk -filename ssd0.vmdk -rawdisk \\.\PHYSICALDRIVE0
```