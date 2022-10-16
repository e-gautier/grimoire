# chmod cheat sheet

## execute `1` write `2` read `4`

| Bin | Decimal | Representation |
| :-: | :-: | :-: |
| 000 | 0 | -&nbsp;-&nbsp;- |
| 001 | 1 | -&nbsp;-&nbsp;x |
| 010 | 2 | -&nbsp;w&nbsp;- |
| 011 | 3 | -&nbsp;w&nbsp;x |
| 100 | 4 | r&nbsp;-&nbsp;- |
| 101 | 5 | r&nbsp;-&nbsp;x |
| 110 | 6 | r&nbsp;w&nbsp;- |
| 111 | 7 | r&nbsp;w&nbsp;x |

## SetUID, SetGID, Sticky bit

| Representation | Meaning |
| :-: |:-|
| `---------t` | **sticky bit**, only the owner can delete |
| `------s---` | **gid bit**, operations in dir are done with the permission of the owner |
| `---s------` | **uid bit**, allow to execute with the permission of the owner |

**S** and **T** (upper case) means the associated permission bit isn't set

**example:** `drw-rwSrw-. 1 user group 18540 May 17 21:06 dir` a new file or directory created in `dir` will have its group set as the group of the directory's owner, not the creator

| Command | Representation |
| :-: | :-: |
| 0000 | `----------` |
| 1000 | `---------T` | 
| 2000 | `------S---` | 
| 3000 | `------S--T` |
| 4000 | `---S------` |
| 5000 | `---S-----T` |
| 6000 | `---S--S---` |
| 7000 | `---S--S--T` |

```bash
# find all setUID or setGID binaries on the system
find ${PATH//:/ } -maxdepth 1 -type f -perm /6000 -ls
```