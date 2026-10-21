# Computer Architecture and Memory

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

Computer architecture describes how processors, memory, and devices work together. A useful mental model is a layered storage system: small nearby storage is fast and limited, while larger storage is farther away and slower.

## Processor and Memory Components

| Term | Meaning and use |
|---|---|
| **CPU / core / register** | The Central Processing Unit (CPU) executes instructions. A core is an instruction-execution unit within a processor. A register is small, fast storage directly used by instructions. |
| **Register file / ALU** | A register file is a collection of processor registers. An Arithmetic Logic Unit (ALU) performs arithmetic and logical operations. |
| **Cache / L1 / L2 / L3 / cache line** | A cache keeps copies of data near a processor to reduce average access time. L1 is usually closest and smallest; L2 and L3 are larger or shared in many designs. A cache line is the unit transferred or tracked by the cache. |
| **Cache hit / cache miss** | A hit finds requested data in a cache. A miss requires fetching it from another level or memory. |
| **RAM / DRAM / SRAM** | Random Access Memory (RAM) is addressable read/write storage. Dynamic RAM (DRAM) stores bits using capacitors and needs refresh; Static RAM (SRAM) uses circuits that retain values while powered and is often used in caches. |
| **Memory controller** | Coordinates requests between processors/devices and memory devices, following timing and protocol rules. |
| **Virtual / physical address** | A virtual address is used within a process or execution context. A physical address identifies a location in the machine's physical memory map. Translation is platform-specific. |
| **MMU / IOMMU / TLB** | A Memory Management Unit (MMU) translates CPU virtual addresses. An Input-Output MMU (IOMMU) can translate or constrain device DMA addresses. A Translation Lookaside Buffer (TLB) caches address translations. |
| **Memory hierarchy** | The arrangement of registers, caches, main memory, and storage by size, speed, cost, and distance from compute. |

## Coherence and Ordering

| Term | Meaning and use |
|---|---|
| **Cache coherence** | Rules and mechanisms that help multiple cached copies of a memory location behave consistently, especially for writes to that location. |
| **Cache consistency** | An informal term often used for whether cached values appear up to date. In architecture discussions, distinguish coherence for one location from memory consistency/order across operations. |
| **MESI** | A family of cache-coherence state names: Modified, Exclusive, Shared, and Invalid. Protocol details and extensions vary. |
| **Snooping / directory-based coherence** | Snooping has caches observe shared transactions to track copies. A directory records which agents may hold copies and coordinates requests. These are broad coordination approaches. |
| **Memory ordering / memory barrier / acquire / release** | Memory ordering defines which reads and writes may be observed before others. A memory barrier constrains ordering. Acquire and release operations establish ordering relationships around synchronization, as defined by the programming language and architecture. |
| **Atomic operation** | An operation that appears indivisible to specified observers. Atomicity alone does not describe all ordering guarantees. |

## Devices and Interconnect

| Term | Meaning and use |
|---|---|
| **DMA** | Direct Memory Access lets a device transfer data to/from memory under a platform's mapping, coherency, and ownership rules. Software usually configures and completes the transfer. |
| **Interrupt / MMIO** | An interrupt signals an event to a processor. Memory-Mapped I/O accesses device registers through address-mapped operations; use the platform's required accessors and ordering. |
| **Interconnect / bus / crossbar / NoC** | An interconnect connects components. A bus is a shared or protocol-defined communication path. A crossbar permits selected simultaneous paths between multiple inputs and outputs. A Network-on-Chip (NoC) routes traffic among on-chip components. |
| **AXI / ACE / CHI** | Arm AMBA protocols: AXI (Advanced eXtensible Interface) is an interface protocol; ACE (AXI Coherency Extensions) extends AXI with coherency-related capabilities; CHI (Coherent Hub Interface) is a coherent interconnect protocol. Exact features depend on specification revision. |

### Example: shared cached data

If two CPU cores cache the same memory line and one writes it, the system needs a coherence mechanism so the other core does not indefinitely use an obsolete copy. Memory ordering separately defines when operations on different locations may be observed. One concern does not automatically solve the other.

**References:** [Arm AMBA AXI/ACE specification](https://developer.arm.com/documentation/ihi0022/c/) (revision C is superseded; consult Arm's version list); [Linux kernel memory management](https://www.kernel.org/doc/html/latest/admin-guide/mm/index.html); [Linux kernel Driver API](https://docs.kernel.org/driver-api/index.html).
