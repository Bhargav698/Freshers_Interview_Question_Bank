
---

## Operating Systems (OS)

| Q# | Question                                                                           | Answer                                                                                                    | Concept(s) Tested                    | Difficulty |
| -- | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------ | ---------- |
| 1  | Your browser and code editor are both open. How does the OS manage this?           | Each runs as a separate **process**, managed by the **scheduler** for CPU time and **memory allocation**. | Processes, Scheduling                | Easy       |
| 2  | You clicked a button and saw a delay before response. What could be the OS reason? | Could be **context switching**, **I/O wait**, or **low priority** task scheduling.                        | Context Switch, I/O Wait             | Medium     |
| 3  | You have 1 CPU core and 3 programs running. How does OS execute them?              | Via **time slicing** and **preemptive multitasking**, each gets CPU for a short period.                   | CPU Scheduling, Multitasking         | Easy       |
| 4  | Why are background tasks not slowing down the foreground app?                      | OS assigns **lower priority** to background tasks and uses **priority scheduling**.                       | Priority Scheduling                  | Medium     |
| 5  | What happens if two threads try to access shared data at the same time?            | Can cause **race conditions** unless handled by **synchronization** or **locks**.                         | Thread Safety, Synchronization       | Medium     |
| 6  | A program is using too much RAM. How does OS handle it?                            | OS may use **paging**, or **swap** part of memory to disk to free up RAM.                                 | Paging, Virtual Memory               | Medium     |
| 7 | What does the OS do when you open a `.txt` file from desktop?                      | Finds file using **File System**, loads content to **memory**, opens with default app.                    | File Handling, System Calls          | Easy       |
| 8 | Why use multi-threading in an app?                                                 | To allow **parallel execution** of independent tasks (e.g., UI thread + network thread).                  | Threads, Concurrency                 | Easy       |
| 9 | What does a deadlock look like in real-world software?                             | Two programs waiting for each other's resources → both **get stuck forever**.                             | Deadlock            | Medium     |
| 10 | Your system is very slow. What resources would you check first?              | Check resources like **CPU**, **RAM**, and **disk usage**.            | Resource Monitoring, Troubleshooting | Easy       |
| 11 | How do OS ensure multiple programs don’t write to disk at same time corrupting it? | Uses **locking mechanisms** and **I/O scheduling** to manage disk access.                                 | Disk Scheduling, Locks               | Medium     |

---