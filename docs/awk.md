# AWK cheat sheet

## examples

|||
| :- | :- |
| `awk -f commands.txt file` | run multiple awk commands on a file |
| `awk '{print $1}' file` | print the first column |
| `awk '/http/ {print $1}' file` | print the first column of each line that matches 'http' |
| `awk 'length($0) > 20' file` | print lines longer than 20 characters |
| `awk '{system($0)}' file` | run every entry as a system command |

## built-in variables

`man --pager='less -p Built-in\ Variables' awk`

>Source: https://www.tutorialspoint.com/awk
