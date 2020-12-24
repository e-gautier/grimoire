# sed (stream editor) cheat sheet
|||
| :- | :- |
| `sed -e '5d' file` | read a file content except the 5th line |
| `sed -n '5p' file` | read only the 5th line from a file content |
| `sed -n '$p' file` | read only the last line from a file content |
| `sed -f commands.txt file` | run the list of commands.txt on a file content |
| `sed -n '/http/, +3 p'` | read each line that match 'http' plus 3 lines from file content |
| `sed -n '3,$ w file.bak' file` | save the lines 3 to the end from a file content into a file file.bak |
| `sed '4 a line' file` | add a line after (before == i) line 4 while reading a file content |
| `sed '4 c line' file` | change line 4 while reading a file content |
| `echo "1 5 15 20" \| sed 'y/151520/IVXVXX/'` | translate characters |
| `sed '/http/ q 100'` | match every lines that contains 'http' and quit and return code 100 |
| `sed 'r file'` | read a file |
| `sed 'e date'` | execute a command |
| `sed 'e' commands.txt`  | execute a list of commands |
| `sed 's/,/./g' file` | search and replace (g == don't stop at the first occurence in line) |
| `sed '/http/ s/,/./g'` | search and replace only if the line matches 'http' |
| `cat file \| sed '/^$/d'` | remove empty lines |
| `sed '/http/ s/^/#/' file`  | comment lines that match 'http' |
| `sed -iSUFFIX file`  | edit file in place, create a backup with a suffix if specified |

>Source: https://www.tutorialspoint.com/sed
