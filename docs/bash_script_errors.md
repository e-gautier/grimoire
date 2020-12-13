# Bash script errors
|||
| :- | :- |
| set -e | stop on error |
| set -u | stop on unset variable |
| set -o pipefail | stop on pipe fail |
| set -p | run as suid |