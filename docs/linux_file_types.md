# Linux files
## Types
- Regular [-] `touch`
- Directory [d] `mkdir`
- Character device [c] (unbuffered driver file)
- Block device [b] (buffered driver file)
- Local domain socket [s]
- Named pipes [p] `mknod`
- Symbolic link [l] `ln`
  - Hard links (share the same index node address)
  - Soft links (content equals to the path of another file)

## Operations (not exhaustive)
- Open
- Close
- Read (<=> recv w/o flags for sockets)
- Write (<=< send w/o flags for sockets)
- Seek (set the cursor position)
- Tell (get the cursor position)