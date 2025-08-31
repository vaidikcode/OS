

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

