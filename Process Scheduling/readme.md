#### Process Scheduling
-  Process scheduler selects among available 
processes for next execution on CPU core
- Goal -- Maximize CPU use, quickly switch 
processes onto CPU core
#### HOW??
- § Maintains scheduling queues of processes
  
• Ready queue – set of all processes residing in 
main memory, ready and waiting to execute

• Device Wait queues – set of processes waiting 
for an event (i.e., I/O)
Operating System Concepts – 10th Edition

• Processes migrate among the various queues 
```text
New → Ready → Running → Waiting → Terminated
         ↑         ↓         ↑
         └─────────┼─────────┘
              Interrupt/Scheduler
```
```text
┌─────────────────────────────────────────────────────────┐
│                     JOB QUEUE                           │
│  All processes in the system                            │
└───────────────┬─────────────────────────────────────────┘
                │ (Admitted)
                ↓
┌─────────────────────────────────────────────────────────┐
│                     READY QUEUE                         │
│  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐      │
│  │ PCB1 │  │ PCB2 │  │ PCB3 │  │ PCB4 │  │ PCB5 │      │
│  └──────┘  └──────┘  └──────┘  └──────┘  └──────┘      │
└───────────────┬─────────────────────────────────────────┘
                │ (Scheduler Dispatch)
                ↓
           ┌─────────┐
           │ RUNNING │
           │ Process │
           └────┬────┘
     ┌──────────┼──────────┐
     ↓ (I/O wait)    (Time slice expired/Interrupt) ↓
┌──────────────┐     ┌─────────────────────────────┐
│ WAITING/     │     │         READY QUEUE         │
│ DEVICE QUEUE │     │ (Process returns here)      │
└──────────────┘     └─────────────────────────────┘
     │ (I/O complete)        ↑
     └───────────────────────┘
```
