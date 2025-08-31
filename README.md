# OS

---

# Operating System (OS) - Notes

## Introduction
- **Definition**: An OS is software that acts as an intermediary between the user and computer hardware.  
- **Purpose**: Provides an environment for users to execute programs **conveniently and efficiently**.  
- **Always running**: The OS runs at all times; all other programs run on top of it.  
- **Functions**:
  - Resource assignment (CPU, memory, I/O devices).  
  - Ensures fairness, security, and correct system operation.  

### OS as a User Interface
- **User** → **System/Application Programs** → **Operating System** → **Hardware**.  
- **Hardware**: CPU, ALU, memory, I/O, storage, peripherals.  
- **System Programs**: compilers, loaders, editors, OS.  

## Goals of an Operating System
### Primary Goals
- **User Convenience**: Easy-to-use interface.  
- **Program Execution**: Provides environment for running user programs.  
- **Resource Management**: Fair allocation of CPU, memory, I/O, storage.  
- **Security**: Protects data and prevents unauthorized access.  

### Secondary Goals
- **Efficient Resource Utilization**: Maximizes CPU, memory, I/O usage.  
- **Reliability**: Robust, modular, error-handling capabilities.  

## Common Operating Systems
### Windows
- **Developer**: Microsoft  
- **Features**: User-friendly, hardware/software support, strong gaming support.  
- **Use Cases**: Personal computing, business, gaming.  

### macOS
- **Developer**: Apple  
- **Features**: Intuitive UI, Apple ecosystem integration, strong security.  
- **Use Cases**: Creative industries, personal/professional computing.  

### Linux
- **Developer**: Community-driven  
- **Features**: Open-source, customizable, stable, runs on old hardware.  
- **Use Cases**: Servers, programming, tech enthusiasts.  

### Unix
- **Developer**: AT&T Bell Labs (various versions)  
- **Features**: Multiuser, multitasking, secure, portable.  
- **Use Cases**: Servers, workstations, research, academia.  

## History of Operating Systems
| Era           | Key Developments                          | Examples                   |
|---------------|-------------------------------------------|----------------------------|
| 1956          | First OS: GM-NAA I/O                      | GM-NAA I/O (1956)          |
| 1960s         | IBM time-sharing systems                  | OS/360, DOS/360, TSS/360   |
| 1970s         | Unix popularized multitasking, PCs emerge | Unix (1971), CP/M (1974)   |
| 1980s         | GUI-based OS, networking features         | Macintosh (1984), Windows (1985) |
| 1990s         | Linux (open-source), improved GUIs        | Linux (1991), Windows 95   |
| 2000s-Present | Mobile OS, cloud, virtualization          | iOS (2007), Android (2008) |

## Characteristics of Operating Systems
- **Device Management**: Tracks and allocates I/O devices.  
- **File Management**: Allocates/deallocates files and resources.  
- **Job Accounting**: Tracks time/resources used.  
- **Error Detection**: Provides debugging/error tools.  
- **Memory Management**: Manages primary memory allocation.  
- **Processor Management**: Allocates/deallocates CPU to processes.  
- **Security**: Prevents unauthorized access.  

## Layered Design of OS
- **Extended Machine Layer**: Provides abstraction (context save, I/O, swapping).  
- **OS Layer (Top Layer)**: Built on extended machine, simplifying coding/debugging.  

## Components of an Operating System
- **Shell**: Outermost layer; interacts with user, interprets commands.  
- **Kernel**: Core of OS; interface between hardware and system.  

# Types of Operating Systems

## 1. Batch Operating System
- **Definition**: Executes jobs in batches without user interaction.  
- **Advantages**: Efficient job management, minimal idle time, high throughput, handles repetitive tasks.  
- **Disadvantages**: Poor CPU utilization, high response time, unpredictable job completion, no real-time feedback.  
- **Examples**: Payroll, Bank Statements.  

---

## 2. Multi-Programming OS
- **Definition**: Multiple programs run in memory simultaneously; CPU switches between them.  
- **Advantages**: Better CPU utilization, reduced response time.  

---

## 3. Multi-Tasking / Time-Sharing OS
- **Definition**: Each task/user gets CPU time (quantum) in round robin fashion. Interactive in real time.  
- **Advantages**: Equal CPU share, reduced idle time, resource sharing, improved productivity & user experience.  
- **Disadvantages**: Reliability issues, high overhead, complexity, security risks.  
- **Examples**: IBM VM/CMS, TSO, Windows Terminal Services.  

---

## 4. Multi-Processing OS
- **Definition**: Uses more than one CPU for execution.  
- **Advantages**: Higher throughput, fault-tolerant (if one CPU fails, others continue).  

---

## 5. Distributed OS
- **Definition**: Network of independent computers acting as a single system; enables remote access.  
- **Advantages**: Fault tolerance, faster data exchange, shared resources, scalable, reduced delays.  
- **Disadvantages**: Expensive, complex, dependent on main network, language not well-defined.  
- **Issues**: Network delays, complex control functions, security risks in message transfer.  
- **Examples**: LOCUS, MICROS, Amoeba.  

---

## 6. Network OS
- **Definition**: Runs on servers; manages users, data, security, and shared resources over a private network.  
- **Advantages**: Stable servers, centralized security, remote access, easy upgrades.  
- **Disadvantages**: Expensive servers, dependency on central server, regular maintenance needed.  
- **Examples**: Windows Server, UNIX, Linux, Mac OS X, Novell NetWare.  

---

## 7. Real-Time OS (RTOS)
- **Definition**: Provides immediate response; used in systems with strict timing requirements.  
- **Types**:  
  - **Hard RTOS**: No delays allowed (e.g., airbags, missile systems).  
  - **Soft RTOS**: Minor delays acceptable.  
- **Advantages**: Fast response, high resource utilization, task shifting, error-free, efficient memory management.  
- **Disadvantages**: Limited tasks, resource-heavy, complex algorithms, requires specific drivers/interrupts.  
- **Examples**: Air traffic control, medical imaging, robots, industrial systems.  

---

## 8. Mobile OS
- **Definition**: Designed for mobile devices (smartphones, tablets).  
- **Advantages**: User-friendly, large app ecosystem, multiple connectivity options, regular updates.  
- **Disadvantages**: Battery constraints, security risks, fragmentation (esp. Android), limited hardware.  
- **Examples**: Android, iOS.  

# Operating System Structures

## What is a System Structure?
- **Definition**: Blueprint of how OS components interact and integrate with the kernel.  
- **Goal**: Simplify OS design by dividing into smaller manageable parts.  
- **Importance**: Helps in maintainability, debugging, scalability, and performance.  

---

## Types of OS Structures
1. **Simple Structure**
   - No clear separation between functions; small & limited.  
   - **Advantages**: High performance, simple development, low overhead, suitable for small systems.  
   - **Disadvantages**: No modularity, poor maintainability, no data hiding, security risks.  
   - **Example**: MS-DOS.  

2. **Layered Structure**
   - OS divided into layers (0 = hardware, N = user interface).  
   - **Advantages**: Modular, easy debugging, maintainability, abstraction.  
   - **Disadvantages**: Performance overhead (calls pass through layers), rigid structure.  
   - **Example**: UNIX.  

3. **Modular Structure**
   - Kernel with core components + dynamically loadable modules.  
   - Combines flexibility of modularity with layered design.  
   - **Example**: Solaris.  

4. **Virtual Machines (VMs)**
   - Abstracts hardware into multiple independent execution environments.  
   - **Advantages**: Hardware abstraction, efficient resource use, isolation, portability, snapshots, legacy support.  
   - **Disadvantages**: Slower than native execution, high resource demand, complex management, security risks if misconfigured.  
   - **Example**: VirtualBox.  

5. **Monolithic Structure**
   - Entire OS runs as one large kernel process (all services together).  
   - **Advantage**: High speed due to minimal overhead.  
   - **Disadvantage**: Hard to maintain, less secure.  

6. **Micro-Kernel Structure**
   - Minimal kernel; non-essential services in user space.  
   - **Advantages**: Secure, reliable (service failure doesn’t crash OS), easy to extend.  
   - **Disadvantage**: Higher overhead due to communication between kernel and user processes.  
   - **Example**: macOS.  

7. **Hybrid Kernel**
   - Combination of monolithic (speed) and micro-kernel (modularity, reliability).  
   - **Examples**: Windows NT, modern macOS.  

8. **Exo-Kernel**
   - Minimal OS giving apps direct control over hardware.  
   - **Advantages**: Customization, minimal abstraction, small size.  
   - **Disadvantages**: Limited operability, higher complexity for developers.  
   - **Developed at MIT**.  

---

# Booting and Dual Booting of Operating System

## What is Booting?
- **Definition**: Process of loading the OS from secondary storage (HDD/SSD) into main memory (RAM) when a computer starts.  
- **Role**: Prepares system by initializing hardware and loading the kernel.  

---

## Types of Booting
1. **Cold / Hard Booting**
   - Starting the computer from completely powered-off state.  
   - Performs **POST (Power-On Self Test)** → initializes hardware → loads OS into RAM.  
   - **Advantage**: Full system initialization.  

2. **Soft / Warm Booting**
   - Restarting without turning off power (via restart command or key combo).  
   - Skips some hardware initialization.  
   - **Advantage**: Faster restart.  
   - **Use**: Both cold boot (full init) and warm boot (quick restart) are necessary in practice.  

---

## Power-On Self Test (POST)
- First diagnostic routine during startup.  
- Tests: CPU, RAM, storage devices, peripherals.  
- **If failure**: Shows error codes/beeps.  
- **If success**: Proceeds to load OS.  

---

## Master Boot Record (MBR)
- Located at the **start of the disk**.  
- Contains:
  - Partition table.  
  - Bootloader code to load OS.  
- **Boot sequence**:
  1. BIOS/UEFI locates MBR from boot device.  
  2. Loads and runs bootloader.  
  3. Bootloader loads OS kernel into memory.  

---

## Boot Process
- Requires **Bootstrap Loader** (stored in ROM).  
- **Example**: BIOS.  
- BIOS/UEFI checks devices in configured **boot order** (e.g., CD → HDD → Network).  
- Bootstrap loader finds kernel, loads it into memory, and executes it.  
- In some systems:
  - Simple loader → loads more complex boot program → loads kernel.  

---

## Dual Booting
- **Definition**: Having two or more OS installed on one computer.  
- **Mechanism**: Boot manager/bootloader provides menu to choose OS at startup.  
- **Storage**: Each OS typically resides in a separate partition/drive.  

---

## Booting vs Dual Booting (Comparison)

| Parameter          | Booting | Dual Booting |
|--------------------|---------|--------------|
| **Definition**     | Starting OS on a computer | Running multiple OS on one computer |
| **Purpose**        | Loads single OS into memory | Lets user choose OS at startup |
| **OS Installed**   | Single OS | Multiple OS (different partitions/drives) |
| **Configuration**  | Direct boot to installed OS | Requires bootloader/boot manager |
| **Setup Complexity** | Simple | More complex (multi-OS setup) |
| **Resource Use**   | All resources for one OS | Resources divided between OSes |

---

# System Calls in Operating System

## Definition

* A **system call** is a programmatic way for a process to request a service from the OS kernel.
* Acts as the **only entry point into the kernel**, executed in **kernel mode**.
* Allows programs to interact with OS instead of directly managing hardware.

---

## Key Points

* Written in high-level languages (C, C++, Pascal) or assembly.
* Triggered by a specific instruction → switch to kernel mode → OS executes request → result returned.
* Prevents inconsistent/error-prone direct hardware handling.

---

## Services Provided by System Calls

1. **Process Management** – create, terminate, wait, fork, etc.
2. **Memory Management** – allocate/free memory.
3. **File Management** – create, open, read, write, delete, close.
4. **Device Management** – read/write to devices.
5. **Information Maintenance & Communication** – get/set system info, IPC.
6. **Protection & Networking** – security and communication services.

---

## Features

* **Interface** – standard interface between user programs & OS.
* **Protection** – allows access to privileged operations safely.
* **Kernel Mode** – switch from user → kernel mode for execution.
* **Context Switching** – involves saving/restoring process state.
* **Error Handling** – returns error codes for failed requests.
* **Synchronization** – ensures safe shared resource access (locks, semaphores).

---

## Working of System Calls (Steps)

1. Program needs OS-controlled resource (file, memory, device).
2. Program issues a **system call** instruction.
3. OS intercepts and transfers control to **Kernel**.
4. Kernel performs requested operation.
5. Control is returned to program.

---

## Types of System Calls

* **Process Control** – `fork()`, `exit()`, `wait()`
* **File Manipulation** – `open()`, `read()`, `write()`, `close()`
* **Device Management** – `ioctl()`, `read()`, `write()`
* **Information Maintenance** – `getpid()`, `alarm()`, `sleep()`
* **Communication** – `pipe()`, `shmget()`, `mmap()`
* **Protection** – `chmod()`, `umask()`, `chown()`

---

## Example (Windows vs Unix)

| Category              | Windows Example                    | Unix Example          |
| --------------------- | ---------------------------------- | --------------------- |
| **Process Control**   | `CreateProcess()`, `ExitProcess()` | `fork()`, `exit()`    |
| **File Manipulation** | `CreateFile()`, `ReadFile()`       | `open()`, `read()`    |
| **Device Management** | `ReadConsole()`, `WriteConsole()`  | `ioctl()`, `read()`   |
| **Info Maintenance**  | `GetCurrentProcessID()`, `Sleep()` | `getpid()`, `alarm()` |
| **Communication**     | `CreatePipe()`, `MapViewOfFile()`  | `pipe()`, `shmget()`  |
| **Protection**        | `SetFileSecurity()`                | `chmod()`, `umask()`  |

---

## Parameter Passing Methods

1. **Registers** – simple but limited by number of registers.
2. **Address of Block** – parameters stored in block; address passed in register (common in Linux/Solaris).
3. **Stack** – parameters pushed onto stack, OS retrieves them.

---

## Advantages

* Provides hardware access.
* Enables memory & process management.
* Ensures security & standardization across platforms.

---

## Disadvantages

* **Performance overhead** – due to user ↔ kernel mode switch.
* **Security risks** – if misused or exploited.
* **Complex error handling**.
* **Compatibility issues** – differ across OS.
* **Resource consumption** in high-load environments.

---






