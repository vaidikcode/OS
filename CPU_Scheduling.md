# CPU Scheduling in Operating Systems

## Definition
- **CPU Scheduling**: Deciding which process gets CPU time when multiple are ready.  
- CPU handles only one task at a time → scheduling ensures **fairness and efficiency**.  

**Goals:**  
- Maximize CPU utilization.  
- Minimize response and waiting time.  

---

## Need for CPU Scheduling
- Selects a process for CPU when another is suspended.  
- Keeps CPU busy whenever possible.  
- Improves overall resource utilization in **multiprogramming systems**.  

---

## Key Terminologies
- **Arrival Time (AT):** Time process enters ready queue.  
- **Completion Time (CT):** Time process finishes execution.  
- **Burst Time (BT):** CPU time required by a process.  
- **Turnaround Time (TAT):** `CT - AT` → total time taken by a process.  
- **Waiting Time (WT):** `TAT - BT` → time spent waiting in ready queue.  
- **Response Time (RT):** Time from submission to first response.  

---

## Design Considerations
- **CPU Utilization:** Keep CPU busy (ideal 100%, real ~40–90%).  
- **Throughput:** No. of processes completed per unit time.  
- **Turnaround Time:** Total time from arrival to completion.  
- **Waiting Time:** Time spent waiting for CPU.  
- **Response Time:** Time till first response (important for interactive systems).  

---

## Scheduling Types
- **Preemptive Scheduling:** CPU can be taken away from a process (e.g., SRTF, RR).  
- **Non-Preemptive Scheduling:** Process keeps CPU until completion or waiting (e.g., FCFS, Non-preemptive Priority).  

---

## CPU Scheduling Algorithms
1. **FCFS (First Come First Serve)** – Simple, arrival order.  
2. **SJF (Shortest Job First)** – Chooses process with shortest burst time.  
3. **SRTF (Shortest Remaining Time First)** – Preemptive SJF.  
4. **Round Robin (RR)** – Fixed time quantum, cyclic order.  
5. **Priority Scheduling** – Based on priority (preemptive or non-preemptive).  
6. **HRRN (Highest Response Ratio Next)** – Ratio-based fairness.  
7. **Multilevel Queue (MLQ)** – Separate queues for process types.  
8. **Multilevel Feedback Queue (MFLQ)** – Processes move between queues based on behavior.  

---

## Comparison of Algorithms

| Algorithm              | Allocation Basis | Complexity | Avg. Waiting Time | Preemption | Starvation | Performance |
|------------------------|------------------|------------|-------------------|------------|------------|-------------|
| **FCFS**               | Arrival time     | Simple     | Large             | No         | No         | Slow        |
| **SJF**                | Shortest BT      | Higher     | Smallest          | No         | Yes        | Optimal AWT |
| **SRTF**               | Shortest BT (rem)| Higher     | Depends on AT/BT  | Yes        | Yes        | Prefers short jobs |
| **RR**                 | Time Quantum     | Depends on TQ | Larger        | Yes        | No         | Fair time-sharing |
| **Priority (Preemptive)** | Priority      | Moderate   | Smaller than FCFS | Yes        | Yes        | Starvation possible |
| **Priority (Non-Preemptive)** | Priority | Less complex | Smaller than FCFS | No         | Yes        | Good for batch systems |
| **MLQ**                | Queue priority   | Complex    | Smaller than FCFS | No         | Yes        | Starvation issue |
| **MFLQ**               | Queue + Feedback | Most Complex | Very small      | No         | No         | Best performance |

---

## Practice Questions

### Q1. False statement about SJF?  
- S1: SJF gives minimum avg. waiting time ✅  
- S2: SJF can cause starvation ✅  
**Answer: (D) Neither S1 nor S2 are false**  

---

### Q2. SRTF Scheduling Example  
Processes:  
| Process | AT | BT |
|---------|----|----|
| P0      | 0  | 9  |
| P1      | 1  | 4  |
| P2      | 2  | 9  |

- Avg. Waiting Time = **5 ms** ✅  

---

### Q3. SRTF Scheduling (Another Example)  
Processes:  
| Process | AT | BT |
|---------|----|----|
| P1      | 0  | 5  |
| P2      | 1  | 3  |
| P3      | 2  | 3  |
| P4      | 4  | 1  |

- Avg. Turnaround Time = **5.5 ms** ✅  

---

### Q4. Total Waiting Time for P2 (SRTF)  
Processes:  
| Process | BT | AT |
|---------|----|----|
| P1      | 20 | 0  |
| P2      | 25 | 15 |
| P3      | 10 | 30 |
| P4      | 15 | 45 |

- Completion Time P2 = 55  
- Waiting Time = 55 - (15+25) = **15 ms** ✅  

---

# Preemptive vs Non-Preemptive Scheduling

## CPU Scheduling
- **Goal**: Decide which process in the ready queue gets the CPU next.  
- **Objectives**: Maximize CPU utilization, minimize waiting & response time, support multitasking, and improve user experience.  
- **Types**:  
  1. **Preemptive Scheduling**  
  2. **Non-Preemptive Scheduling**  

---

## Preemptive Scheduling
- **Definition**: The OS can **interrupt** a running process and allocate CPU to another (e.g., higher priority or time-sharing).  
- **State Change**: Running → Ready before completion.  
- **Examples**: Round Robin, Shortest Remaining Time First (SRTF), Priority (preemptive).  

### ✅ Advantages
- Prevents CPU monopolization.  
- Better average **response time** (multi-user systems).  
- Used in modern OS (Windows, Linux, macOS).  

### ❌ Disadvantages
- Complex implementation.  
- Higher **overhead** (frequent context switches).  
- Possible **starvation** of low-priority processes.  
- Concurrency issues if preempted during shared resource use.  

---

## Non-Preemptive Scheduling
- **Definition**: Once a process starts, it **runs till completion** or voluntarily moves to waiting state.  
- **Examples**: FCFS, SJF, Priority (non-preemptive).  

### ✅ Advantages
- Simple and easy to implement.  
- Minimal scheduling overhead.  
- Less computational resource usage.  
- Used in early OS (Windows 3.11, old macOS).  

### ❌ Disadvantages
- Susceptible to **denial of service** (long jobs hog CPU).  
- Higher **average response time**.  
- No time-sharing possible.  

---

## Key Differences

| **Parameter**     | **Preemptive** | **Non-Preemptive** |
|--------------------|----------------|---------------------|
| **Basic**          | CPU allocated for limited time | CPU held until completion or waiting |
| **Interrupts**     | Process can be interrupted | Process cannot be interrupted |
| **Starvation**     | Low-priority may starve | Short jobs may starve if long one runs |
| **Overhead**       | Higher (context switching) | Lower |
| **Flexibility**    | Flexible | Rigid |
| **Cost**           | Costly (extra overhead) | No extra cost |
| **Response Time**  | Low (better response) | High (slower response) |
| **Decision Making**| Scheduler-driven (priority/time slice) | Process-driven (OS just follows) |
| **Process Control**| OS has greater control | OS has less control |
| **Concurrency**    | More (shared resource preemption) | Less (no forced preemption) |
| **Examples**       | RR, SRTF, Priority (preemptive) | FCFS, SJF, Priority (non-preemptive) |

---

👉 **In short**:  
- **Preemptive = fast response, fair sharing, more overhead.**  
- **Non-Preemptive = simple, less overhead, but can block others.**


# Multiple-Processor Scheduling in Operating System

In **multiple-processor scheduling**, multiple CPUs are available, allowing **load sharing**.  
However, it is more complex than single-processor scheduling.  

If processors are **homogeneous** (identical), any process can run on any processor.

---

## CPU Scheduling (Refresher)
- **Definition:** Mechanism to decide which task/process executes on CPU at any instant.  
- **Goal:** Keep CPU busy, optimize performance.  
- **Algorithms:** FCFS, Round Robin, Priority, etc.

---

## What is Multiple-Processor Scheduling?
- Applies when **>1 processor** is present.  
- **Benefits:** Higher throughput, concurrent task execution.  
- **Challenges:** Decide which CPU handles which task & balance workload.  

### Approaches
1. **Asymmetric Multiprocessing (AMP):**  
   - One CPU = master (scheduling + I/O).  
   - Other CPUs = execute user code.  
   - Simple, less data sharing.  

2. **Symmetric Multiprocessing (SMP):**  
   - Each CPU is self-scheduling.  
   - Ready queue: common or per-CPU.  
   - Each processor’s scheduler picks process to execute.  

---

## Key Concepts

### 1. Processor Affinity
- Processes prefer to run on the **same processor** to use cached data.  
- Avoids costly cache invalidation & repopulation.  

Types:  
- **Soft Affinity:** OS *tries* to keep process on same CPU (not guaranteed).  
- **Hard Affinity:** Process specifies subset of CPUs it may run on (Linux → `sched_setaffinity()`).

---

### 2. Load Balancing
- Keeps workload evenly distributed across CPUs in SMP.  
- Required when each CPU has its own queue.  
- Not required if common ready queue is used.  

Methods:  
- **Push Migration:** Overloaded CPU pushes tasks to idle CPUs.  
- **Pull Migration:** Idle CPU pulls tasks from busy CPU.

---

### 3. Multicore Processors
- Multiple **cores on same physical chip**.  
- Faster, less power vs. separate physical CPUs.  

**Problem:**  
- **Memory Stall** (waiting for data → up to 50% idle time).  

**Solution:** Multithreaded cores (multiple hardware threads per core).  
- **Coarse-Grained Multithreading:** Switch thread only on long-latency events (e.g., cache miss). Switching is expensive.  
- **Fine-Grained Multithreading:** Switch threads at instruction-cycle level. Switching is cheap.  

---

### 4. Virtualization and Threading
- Even a **single CPU** can appear as multiple virtual CPUs.  
- Host OS manages **guest OSes** via virtual machines.  
- Each guest OS believes it has full CPU → but actually shares cycles.  

**Impact:**  
- Poor response times in guest OS (e.g., 100ms timeslice may take >1s).  
- Guest OS clocks often inaccurate.  
- Virtualization may undo OS scheduling optimizations.  

---

## Conclusion
- Scheduling keeps CPU from idling and optimizes execution.  
- **Multiple-processor systems add complexity** (affinity, load balancing, virtualization).  
- Proper strategies ensure efficiency and fair distribution of workloads.

