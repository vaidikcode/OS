

# Process Management

## Basics

* **Single-tasking / Batch systems**: Only one process active → simple management.
* **Multiprogramming / Multitasking**: Multiple processes active → complex management.

  * Shared resources (e.g., memory).
  * Requires **process synchronization**.

**Advantages of Multiprogramming**

* Better **CPU utilization**.
* Improved **system responsiveness**.
* Processes can run **interleaved** (e.g., CPU assigned to another process when one is waiting for I/O).

---

## CPU-bound vs I/O-bound Processes

* **CPU-bound**: Needs more CPU time → spends longer in *running state*.
* **I/O-bound**: Needs more I/O time → spends longer in *waiting state*.

---

## Process Scheduling

* Determines which process runs next.
* **Goals**:

  * Maximize **CPU utilization**.
  * Minimize **turnaround time**.
  * Improve **response time**.

---

## Tasks in Process Management

1. **Process Creation & Termination**

   * Creation → Process ID, Process Control Block (PCB).
   * Termination → Release allocated resources.
2. **CPU Scheduling** – Allocate CPU fairly & efficiently.
3. **Deadlock Handling** – Prevent circular waiting.
4. **Inter-Process Communication (IPC)** – Shared memory, message passing.
5. **Process Synchronization** – Coordinate shared resource access.

---

## Process Operations

* **Creation** – Generate new independent process.
* **Scheduling** – Pick from *ready queue*.
* **Execution** – CPU runs process, may block/wait for I/O.
* **Killing** – Remove PCB after completion.

---

## Context Switching

* Saving current process state & loading another.
* **Occurs when**:

  * High-priority process becomes ready.
  * Interrupt occurs.
  * Preemptive CPU scheduling.
  * Sometimes on user ↔ kernel mode switch.

### Context Switch vs Mode Switch

* **Mode Switch**: User ↔ Kernel privilege change. No process change required.
* **Context Switch**: Entire process state saved/restored (done by kernel).

---

## Scheduling Algorithms

1. **FCFS (First-Come, First-Served)**

   * Non-preemptive, simple.
2. **SJF (Shortest Job First)**

   * Preemptive, lowest burst time first → minimizes avg waiting.
3. **Round Robin (RR)**

   * Fixed time slice per process → fairness, avoids starvation.
4. **Priority Scheduling**

   * Highest priority first.
5. **Multilevel Queue**

   * Separate ready queues with different algorithms.

---

## Pros & Cons of Process Management

**Advantages**

* Run multiple programs (multitasking).
* Process isolation → fault containment.
* Fair resource sharing.
* Smooth switching → responsive system.

**Disadvantages**

* Overhead (CPU + memory for PCB & queues).
* Complexity (scheduling + resource allocation).
* Deadlocks possible.
* Frequent context switching → performance loss.

# Process Table and Process Control Block (PCB)

## Process Control Block (PCB)
- **Definition:** Data structure used by the OS to store information about a process and manage execution.  
- **Key Points:**
  - Each process has a **unique Process ID (PID)**.
  - Stores **state, program counter, stack pointer, registers, open files, scheduling info**.
  - Updated during **state transitions**.
  - Essential for **context switching**.

### Structure of PCB
- **Pointer:** Saves stack pointer during state switch.  
- **Process State:** Current state (Running, Ready, Waiting, etc.).  
- **Process ID:** Unique identifier (PID).  
- **Program Counter:** Address of the next instruction.  
- **Registers:** CPU register values saved/restored during context switch.  
- **Memory Limits:** Info about memory management (page/segment tables).  
- **Open Files List:** Tracks files opened by the process.  

### Advantages of PCB
1. **Stores Process Details:** PID, state, registers, memory, etc.  
2. **Helps Resume Processes:** Saves execution point for context switching.  
3. **Smooth Execution:** Manages CPU, memory, files, devices.  
4. **Facilitates Context Switching:** Saves/restores process states.  
5. **Aids in Scheduling:** Holds priority, policy, quantum.  
6. **Resource Allocation:** Tracks files, memory, I/O devices.  

### Disadvantages of PCB
- High **memory usage** (one PCB per process).  
- **Context switching overhead** (time to save/load PCB).  
- **Security risk** if PCB is not protected.  

### Additional Notes
- **Interrupt Handling:** PCB stores info on interrupts.  
- **Context Switching:** Saves state of current process, loads next.  
- **Real-Time Systems:** PCB may include deadlines/priorities.  
- **Virtual Memory:** PCB holds page tables, fault handling.  
- **Fault Tolerance:** Some OSes keep multiple PCB copies.  
- **Storage Location:** Kept in protected memory (often kernel stack).  

---

## Process Table
- **Definition:** OS data structure containing an entry (PCB) for each active process.  
- **Purpose:** Efficient **management, scheduling, and switching** between processes.  
- **Contents:** PID, state, program counter, CPU registers, memory use, resources.  

### Advantages of Process Table
1. **Tracks Processes:** Centralized record of all active processes.  
2. **Helps Scheduling:** Contains priority, burst time, arrival time.  
3. **Easy Management:** Allows create, suspend, resume, terminate.  
4. **Facilitates Context Switching:** Stores registers, stack pointers, etc.  
5. **Supports IPC:** Contains pointers/flags for shared memory, pipes, queues.  
6. **Resource Allocation:** Tracks memory, files, I/O devices.  
7. **Deadlock Handling:** Maintains locks held/requested.  
8. **Security & Access Control:** Includes user ID, permissions.  
9. **Debugging & Monitoring:** Used by tools (`ps`, `top`).  

### Disadvantages of Process Table
- Consumes **memory** (large table for many processes).  
- **Slower operations** with too many entries.  
- Adds **system overhead** (frequent updates).  

---

## Key Difference
- **Process Table:** Global structure holding all processes.  
- **PCB:** Individual structure with details of one process.  

# Process Schedulers in Operating System

## Introduction
- **Process**: Instance of a program in execution.  
- **Scheduling**: Decides which process gets CPU time in multiprogramming systems.  
- **Process Scheduler**: OS component that determines execution order of processes.  

---

## Process Scheduling
- Activity of selecting/removing processes for CPU execution.  
- Processes move among queues:
  - **Ready Queue**
  - **Waiting Queue**
  - **Device Queue**

---

## Categories of Scheduling
1. **Non-Preemptive**
   - Process cannot be interrupted until it finishes or waits.
   - Resources are switched only when process completes.  
2. **Preemptive**
   - OS can interrupt and move process to ready state.
   - CPU may prioritize another process.  

---

## Types of Process Schedulers

### 1. Long-Term Scheduler (Job Scheduler)
- Loads process from disk → main memory (Ready State).  
- Controls **Degree of Multiprogramming**.  
- Balances **I/O-bound** vs **CPU-bound** tasks.  
- May not exist in time-sharing systems (e.g., Windows).  
- **Slowest** among all schedulers.  

---

### 2. Short-Term Scheduler (CPU Scheduler)
- Selects process from **Ready Queue** for CPU execution.  
- Runs frequently to avoid starvation.  
- Uses various scheduling algorithms.  
- Works closely with **Dispatcher**.  
- **Fastest** scheduler.  

#### Dispatcher
- Transfers selected process to CPU.  
- Handles:
  - Saving/restoring process context (PCB).  
  - Switching system → user mode.  
  - Jumping to correct instruction.  
- **Dispatch Latency**: Time taken by dispatcher.  

---

### 3. Medium-Term Scheduler
- Performs **Swapping** (process ↔ disk).  
- Reduces degree of multiprogramming.  
- Suspended processes swapped out, resumed later.  
- **Speed**: Between Long-Term and Short-Term.  

---

## Other Schedulers
- **I/O Schedulers**: Manage order of I/O operations (FCFS, RR, etc.).  
- **Real-Time Schedulers**: Ensure deadlines in real-time systems (e.g., EDF, RM).  

---

## Comparison of Schedulers

| Feature                | Long-Term            | Short-Term           | Medium-Term           |
|-------------------------|----------------------|----------------------|-----------------------|
| Role                   | Job scheduling       | CPU scheduling       | Process swapping      |
| Speed                  | Slowest              | Fastest              | Intermediate          |
| Multiprogramming Ctrl  | Yes                  | Minimal              | Reduces degree        |
| Presence in Systems    | Often absent in TS   | Minimal in TS        | Present in TS         |
| Reintroduction         | Yes                  | Selects ready process| Yes                   |

---

## Context Switching
- Mechanism to **save/restore process state (PCB)**.  
- Enables multiple processes to share one CPU.  
- Essential in multitasking OS.  

**Stored in PCB:**
- Program Counter  
- Scheduling Information  
- Base & Limit Registers  
- CPU Registers  
- Process State  
- I/O State Information  
- Accounting Information  

---

# Context Switching in Operating System

## Definition
- **Context Switching**: CPU stops one process, saves its state, and loads another process’s state.  
- Enables **multiprogramming** → multiple processes share CPU effectively.  

---

## Need in Multitasking
- Ensures fair CPU sharing among multiple processes.  
- Creates illusion of parallel execution (CPU runs one process at a time).  
- Prevents CPU monopolization by a single process.  

---

## Role in Scheduling
- **Scheduler**: Decides next process (based on algorithms like RR, Priority, etc.).  
- **Context Switch**: Implements that decision (stop current, start chosen).  
- **Dispatcher**: Performs actual switching.  

---

## Triggers of Context Switching
1. **Interrupts**  
   - e.g., I/O completion, hardware request.  
   - CPU switches to interrupt handler.  
2. **Kernel/User Switch**  
   - Switching between **user mode** ↔ **kernel mode**.  
3. **System Calls / Exceptions**  
   - Process voluntarily/involuntarily yields CPU.  

---

## Working of Context Switching

### Example: Switching between `p0` and `p1`
1. **Execution Phase (p0 running, p1 idle)**  
   - Interrupt/system call occurs.  
2. **Save Current State (p0 → PCB0)**  
   - OS saves registers, program counter, etc. to PCB0.  
3. **Load New State (PCB1 → p1)**  
   - OS restores p1’s state from PCB1.  
4. **Execution Phase (p1 running, p0 idle)**  
   - Another interrupt/system call occurs.  
5. **Save State (p1 → PCB1)**  
6. **Reload State (PCB0 → p0)**  
   - OS resumes p0 from where it left.  

---

## Overhead
- **Context Switch Overhead**: Time spent switching (not executing).  
- Excessive switching → lower CPU efficiency.  

---

## Factors Affecting Switch Time
- **Hardware support** (fast register save/load).  
- **Number of registers** (more registers = slower switch).  
- **Memory speed** for PCB storage.  
- **OS kernel efficiency** in handling switches.  
- Example: **Sun UltraSPARC** uses multiple register sets → faster switching.  

---

# Threads in Operating System
_Last Updated: 29 Aug, 2025_

## Definition
- A **thread** is a single sequence of execution within a process.  
- Also called **lightweight processes**.  
- Each thread belongs to one process.  

## Properties
- **Shared among all threads in a process:** Code section, data section, OS resources (files, signals).  
- **Unique to each thread:** Thread ID, Program Counter (PC), Register Set, Stack.  

---

## Why Do We Need Threads (Benefits)
- **Performance:** Parallel execution → faster programs.  
- **Responsiveness:** One thread can respond while another works.  
- **Concurrency:** Multiple tasks at once (e.g., typing + formatting in MS Word).  
- **Simple Communication:** Direct data sharing, no IPC needed.  
- **Prioritization:** Higher-priority thread runs first.  
- **Efficient Context Switching:** Faster than process switching.  
- **Multiprocessor Utilization:** Threads can run on multiple CPUs.  
- **Resource Sharing:** Save memory/resources.  
- **Throughput:** More jobs per unit time.  
- **Synchronization:** Locks, semaphores ensure safe resource access.  
- **Thread Management:** Handled using a **Thread Control Block (TCB)**.  

---

## Components of a Thread
- **Stack Space** → local variables, function calls.  
- **Register Set** → temporary data & results.  
- **Program Counter** → current instruction pointer.  

---

## Types of Threads
### 1. User-Level Threads (ULTs)
- Managed in **user space** (via thread libraries).  
- **Fast switching** (PC, registers, stack only).  
- Lightweight (no system calls).  
- **Limitation:** If one thread blocks, all threads in that process block.  
- Limited multiprocessor use → kernel schedules processes, not threads.  

### 2. Kernel-Level Threads (KLTs)
- Managed by the **OS kernel**.  
- Kernel schedules each thread → true parallelism on CPUs.  
- Handles blocking system calls (other threads can still run).  
- Better load balancing.  
- **Slower switching** (user ↔ kernel mode transitions).  
- More complex; heavy load on scheduler with many threads.  

---

## Difference: Process vs Thread
- **Process:** Independent, separate memory spaces.  
- **Thread:** Share memory & resources within a process.  
- **Unique per thread:** PC, registers, stack.  









