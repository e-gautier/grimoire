# Remove comments from bash file
```bash
cat file.conf | cut -d "#" -f1 > newfile.conf
```