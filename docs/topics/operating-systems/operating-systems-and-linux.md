# Operating Systems and Linux

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

An operating system (OS) manages shared hardware resources and offers services to programs. Linux names both an OS kernel and, commonly, a family of systems built around that kernel plus user-space tools.

## Processes and OS Interfaces

| Term | Meaning and use |
|---|---|
| **Operating system (OS) / kernel / user space / kernel space** | An operating system (OS) manages hardware resources and offers common services. The kernel is its privileged core. User space runs ordinary applications with restricted privileges; kernel space is where the kernel executes privileged code. |
| **System call** | A controlled request from a program to the kernel, such as opening a file or creating a process. A library API may wrap one or more system calls. |
| **Process / thread / scheduler / context switch** | A process is a running program with resources and an address space. Threads are execution paths within a process. The scheduler selects runnable work; a context switch changes the active execution state. |
| **Interrupt / exception / signal** | A hardware interrupt asks the CPU to handle an event. A processor exception arises from instruction execution, such as a page fault. A Unix signal is an OS notification delivered to a process or thread. These names belong to different layers. |
| **File descriptor / file system** | A file descriptor is a small process-local handle for an open file, socket, pipe, or other resource on Unix-like systems. A file system organizes names and persistent data. |
| **Permissions** | Rules controlling access to a resource, such as read, write, and execute rights. The model and details differ across operating systems and file systems. |

## Shell and Command-Line Terms

| Term | Meaning and use |
|---|---|
| **Shell / terminal** | A shell interprets commands and scripts. A terminal is a text input/output interface; a terminal emulator hosts a shell window. |
| **Standard input / standard output / standard error** | Conventionally file descriptors 0, 1, and 2 for input, ordinary output, and diagnostics respectively. Programs may redirect them. |
| **Pipe / redirection** | A pipe connects one program's output to another's input. Redirection sends input or output to a file or another destination. |
| **Environment variable** | A named value inherited by a process from its environment, often used for configuration such as `PATH`. Avoid putting secrets in logs or command histories. |
| **Daemon / service manager** | A daemon is a background process. A service manager starts, stops, and supervises system services; systemd is one common Linux example, not the only one. |
| **Driver / device tree / bootloader / firmware** | A driver controls or communicates with a device. A device tree describes hardware for an OS, especially in embedded systems. A bootloader starts the system and loads later software. Firmware is low-level software associated with a device or platform. |

## Memory and Coordination

| Term | Meaning and use |
|---|---|
| **Virtual memory / page table / page fault / TLB** | Virtual memory gives a process an address space mapped to physical memory. Page tables describe mappings. A page fault occurs when access needs OS handling. A Translation Lookaside Buffer (TLB) caches address translations. |
| **Mutex / semaphore / spinlock** | A mutex grants one owner access to a protected region. A semaphore tracks a count of available resources or signals. A spinlock waits by repeatedly checking; it is suited only to contexts where waiting is expected to be very short. |
| **Deadlock / race condition / starvation** | Deadlock is a cycle of waits that prevents progress. A race condition occurs when behavior depends on uncontrolled timing. Starvation is prolonged denial of a resource or execution opportunity. |
| **Atomic operation** | An operation observed as indivisible with respect to specified concurrent observers. Atomicity and memory-order guarantees depend on the language and hardware contract. |
| **Shared memory / IPC** | Shared memory lets processes access a common mapped region. Interprocess communication (IPC) includes mechanisms such as pipes, sockets, message queues, and shared memory. |
| **`mmap` / memory-mapped I/O (MMIO)** | `mmap` maps files or devices into a process address space on supported systems. MMIO accesses device registers through designated addresses and must follow platform-specific mapping and ordering rules. |

**References:** [Linux man-pages: pthreads(7)](https://man7.org/linux/man-pages/man7/pthreads.7.html); [Linux man-pages: mmap(2)](https://man7.org/linux/man-pages/man2/munmap.2.html); [Linux kernel memory management](https://www.kernel.org/doc/html/latest/admin-guide/mm/index.html); [Linux kernel Driver API](https://docs.kernel.org/driver-api/index.html).
