Scheduling
==========

1. Dispatching -- mechanism part on how context switching happens
2. Scheduling -- algorithm part on how to pick tasks from one to another

When does a scheduler make decisions
- when a process
  1. switches from running to waiting state (calling system call)
  2. switches from running to ready state
  3. switches from waiting to ready
  4. terminates

Minimal: nonpreemptive (running process decides voluntarily)
- 1 and 4

Additional circumstances: preemptive (os forces the action)
- 2 and 3, depends on external event because usually you don't know when the process will wake up

#### scheduling algorithms

Criteria: __workload__ and __environment__

- workload:
  - process behavior: alternating sequence of CPU and I?O bursts
  - CPU bound (background calculation) vs. I/O bound (editors when typing stuff, only wake up when you press something)
  - Linux favors I/O bound processes

- Environment:
  - Batch (like running a quantum computing for days without interaction, thus have a different scheduling algorithms) vs. interactive
  - Specialized vs. general


- average waiting time: total time you have to wait
- average response time: when do you start after you arrive

- FCFS: naive algorithm, waiting time depends on arrival time, better to have the shortest job run first

- SJF: only theoretical because is it not possible to know how long a task will take. But theoretically optimal

- SRTF (shortest remaining time first): like SJF but you also preempt.
  - if new process arrives w/ shorter CPU burst than the remaining for current process, schedule new process
  - still not practical. Reduces average waiting time, provably optimal

- Round Robin
  - time slice can be dynamically managed by the OS, whether to make it for example 300 or 500 of hardward ticks
  - trade off waiting time to response time between different time slices
