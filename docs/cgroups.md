# CGroups

The control groups are a feature provided by the Linux kernel to manage, restrict, and audit groups of processes.

## cgroups2

Attach a process to a new group and set a memory threehold:
```bash
# create group
mkdir /sys/fs/cgroup/groupname

# add the memory controller
echo +memory > cgroup.subtree_control

# set the threehold
echo 1000000 > /sys/fs/cgroup/groupname/memory.high

# attach the process
echo $PID > /sys/fs/cgroup/groupname/cgroup.procs

```

## Systemd usage
```bash
systemctl edit --full systemd-resolved.service

[...]
MemoryMax=50M
```
```bash
systemctl restart systemd-resolved.service
```
```bash
ps -aux | grep systemd-resolved

[...]
systemd+ 163946 /usr/lib/systemd/systemd-resolved
```
```bash
cat /proc/163946/cgroup

0::/system.slice/systemd-resolved.service
```
```bash
cat /sys/fs/cgroup/system.slice/systemd-resolved.service/memory.max

52428800
```
>Sources:
>- https://www.kernel.org/doc/Documentation/cgroup-v2.txt
>- https://man7.org/linux/man-pages/man7/cgroups.7.html
>- https://wiki.archlinux.org/index.php/cgroups
>- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/ch01
