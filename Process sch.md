

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











* Registers + PC must be saved.
* TLB entries may be flushed (not always saved).

---

Do you want me to also **add diagrams (like process states, context switch flow, or scheduling timelines) in ASCII / Markdown-friendly form**, or should I keep notes strictly text-based?
