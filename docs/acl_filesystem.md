# ACL on filesystem
Access Control Lists are used to gain flexibility over the filesystem permission management.
```bash
getfacl dir

# file: dir/
# owner: root
# group: root
user::rwx
group::---
mask::---
other::---
```
```bash
ls -l dir

drwx------+ 2 root root 60 dir
```
|||
| :- | :- |
| `setfacl -m "u:user:permissions" <file/dir>` | `m`odify the permissions for a user |
| `setfacl -m "g:group:permissions" <file/dir>` | `m`odify the permissions for a group |
| `setfacl -m "other:permissions" <file/dir>` | `m`odify the permissions for others |
| `setfacl -dm <entry> <file/dir>` | make created files and directories inherit from this rule (`d`efault) |
| `setfacl -x "u:user" <file/dir>` | remove a specific rule |
| `setfacl -k <file/dir>` | remove all default rules |
| `setfacl -b <file/dir>` | remove all rules |

>Sources:
> - https://wiki.archlinux.org/index.php/Access_Control_Lists
