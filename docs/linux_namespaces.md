# Linux namespaces
Linux namespaces is an abstraction that make appear to a process its own isolated instance of the global resources. Interact with a namespace require the **CAP_SYS_ADMIN** capability (except for the **user_namespace** which require no privilege).

Namespaces can be created from the **clone(2)** syscall (which is part of the **fork(2)** process). A process can join an existing namespace using the **setns(2)** syscall.

| Namespace | Flag | Page | Isolate |
| - | - | - | - |
| CGroup | CLONE_NEWCGROUP | cgroup_namespaces(7) | Cgroup root directory |
| IPC | CLONE_NEWIPC | ipc_namespaces(7) | POSIX message queues |
| Network | CLONE_NEWNET | network_namespaces(7) | Network devices, stacks, ports, etc |
| Mount | CLONE_NEWNS | mount_namespaces(7) | Mount points |
| PID | CLONE_NEWPID | pid_namespaces(7) | Process IDs |
| Time | CLONE_NEWTIME | time_namespaces(7) | Boot and monotonic time |
| User | CLONE_NEWUSER | user_namespaces(7) | User and group IDs |
| UTS | CLONE_NEWUTS | uts_namespaces(7) | Hostname and NIS (Network Information Service) domain name |

> Note: PAM uses a module named **pam_namespace(8)** to isolate a session.


