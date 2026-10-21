# Hardware and Verification: Common Comparisons

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Comparisons](index.md)

## Simulation, Emulation, and FPGA Prototyping

| Approach | How it runs | Common purpose |
|---|---|---|
| Simulation | A software tool evaluates a design model. | Detailed functional checks and waveform/debug visibility. |
| Emulation | Specialized hardware executes a mapped design model. | Faster system-level verification for suitable designs. |
| FPGA prototyping | A design is mapped onto programmable logic. | Early software bring-up and system behavior with a physical prototype. |

Speed, fidelity, capacity, and debug access trade off differently. Vendors may use these words differently; check the tool's model and project flow.

## DPI, VPI, and PLI

| Interface | Main idea | Example use |
|---|---|---|
| DPI | SystemVerilog's standardized foreign-language call interface. | Call C reference-model code from a testbench. |
| VPI | Verilog simulator programming interface for accessing design objects and simulation behavior. | A C application inspects or controls simulator objects. |
| PLI | Earlier Verilog Programming Language Interface family; includes older mechanisms and related standards. | Legacy simulator integrations. |

The exact feature set, naming, and compatibility depend on language standard and simulator. FLI and VHPI are related simulator integration names for other language/tool contexts. DPI is not a generic synonym for all foreign interfaces.

## Cache Coherence and Memory Consistency

Cache coherence governs how multiple cached copies of one memory location are kept consistent, especially when writers exist. Memory consistency (or memory ordering) defines the allowed observation order of operations across locations. A coherent system can still allow different observers to see operations in different orders under its memory model.

## Clock Gating and Power Gating

Clock gating suppresses clock activity to reduce switching power while the block remains powered. Power gating disconnects a power domain and may require state retention, isolation, and reset sequencing. Power gating has broader state and connectivity consequences.

## DMA and Programmed I/O

With programmed I/O, the CPU performs reads/writes to move data between a device interface and memory. With Direct Memory Access, a device transfers data to/from memory after software configures the operation. DMA reduces per-byte CPU work but still requires software coordination, address mapping, and synchronization. Actual cache-coherency behavior is platform-specific.

## Firmware, Driver, and Operating System

| Term | Role | Example |
|---|---|---|
| Firmware | Low-level software associated with a device or platform; may run on the device itself. | Device startup code stored in nonvolatile memory. |
| Driver | Software interface that controls or communicates with a device. | An OS PCI driver configures a device and exposes services. |
| Operating system | Manages system resources and provides execution services to applications. | Linux schedules processes and mediates device access. |

These components cooperate, but their location and responsibilities vary by platform. Firmware is not always a driver, and a driver is not the OS itself.
