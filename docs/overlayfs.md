# Overlay filesystem
Overlay filesystem is useful to provide a read-write layer over an existing read-only one.
```bash
mount -t overlay overlay -o lowerdir=/tmp/overlaylower,upperdir=/tmp/overlayupper,workdir=/tmp/overlayworkdir /tmp/overlay
```
|||
| :- | :- |
| `lowerdir` | the ro layer |
| `upperdir` | the rw layer |
| `workdir` | the working directory (needs to be an empty directory on the same filesystem as upperdir) |
| `/tmp/overlay` | the mounted overlay filesystem |
```bash
tree /tmp/overlay*

overlay
├── readonlyfiles
└── readwritefiles
overlaylower
└── readonlyfiles
overlayupper
└── readwritefiles
overlayworkdir
└── work
```
```bash
umount /tmp/overlay && tree overlay*

overlay
overlaylower
└── readonlyfiles
overlayupper
└── readwritefiles
overlayworkdir
└── work
```

>Sources:
>- https://www.kernel.org/doc/html/latest/filesystems/overlayfs.html
>- https://wiki.archlinux.org/index.php/Overlay_filesystem
