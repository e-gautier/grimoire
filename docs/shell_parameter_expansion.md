# Shell parameter expansion

|||
| :- | :- |
| `${VAR:-default}` | use a default "default" value if VAR is not set |
| `${VAR:+default}` | use a default "default" value if VAR is set |
| `${VAR:=default}` | set a default "default" value to VAR if VAR is not set |
| `${VAR:?error}` | print "error" and exit if the variable is not set |
| `${VAR#https://}` | remove a prefix from VAR |
| `${VAR%/articles}` | remove a suffix from VAR |
| `${VAR/search/replace}` | search and replace once |
| `${VAR//search/replace}` | search all and replace |
| `${#VAR}` | get the length of VAR |

> Source: https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html