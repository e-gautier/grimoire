# Perf
Perf is a performance analysis tool looking at the kernel instruction pointer address and resolving it to a function name. To do so it:
- gets the program instruction pointer address
- gets a copy of the program stack
- unwinds the stack to find the address of the current function call
- uses the program's symbol table to figure out the name of the symbol that address corresponds to

|||
| :- | :- |
| `perf top` | CPU used by every function |
| `perf list` | list events |
| `perf record {PID, COMMAND, -a}` | record events and put it in a file |
| `perf record -p PID sleep 5` | record PID for 5 seconds |
| `perf report` | quick analyse of a record |
| `perf annotate` | assembly analysis of a record |
| `perf script` | print the sample as text |

Create a flamegraph from a capture of `ls` (`firefox ./graph.svg`):
```bash
perf record -g ls && perf script | stackcollapse-perf.pl | flamegraph.pl > graph.svg
```

>Sources:
>- http://www.brendangregg.com/perf.html
>- perf-zine.pdf
