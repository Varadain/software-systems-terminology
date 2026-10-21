# Quick Reference

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Roadmap](../learning-roadmap.md)

## Request to Result

```text
client → API request → protocol and network → server → result/response → client
```

An Application Programming Interface (API) describes an interaction boundary. A protocol describes communication rules. Hypertext Transfer Protocol (HTTP) is an application protocol; Transmission Control Protocol (TCP) or QUIC (a secure transport protocol over User Datagram Protocol (UDP)) can carry HTTP traffic. JavaScript Object Notation (JSON) is one possible data format, not a transport protocol. Representational State Transfer (REST) and Remote Procedure Call (RPC) are API design approaches, not data formats.

## Build to Run

```text
source → compiler/front end → object code → linker → executable → loader → process
```

The exact steps depend on the language and toolchain. Interpreters and managed runtimes may add other stages.

## Test Levels

| Level | Main question |
|---|---|
| Unit | Does one small unit behave as expected? |
| Integration | Do connected units exchange data correctly? |
| System | Does the assembled system meet its requirements? |
| End-to-end | Can a user journey cross the real system boundaries? |

## Security Vocabulary

- **Authentication:** establish who or what is making a request.
- **Authorization:** decide what that identity may do.
- **Encryption:** protect confidentiality with a key.
- **Hashing:** map data to a fixed-size digest; a hash alone is not encryption.
- **Encoding:** represent data in another format; encoding alone is not secrecy.

## Execution Vocabulary

- A **process** is a running program instance with its own protected address space.
- A **thread** is an execution path within a process; threads usually share process memory.
- **Concurrency** lets work make progress in overlapping intervals; **parallelism** runs work at the same time on multiple execution resources.
- A **virtual machine** emulates a computer platform; a **container** packages isolated processes while sharing the host kernel in common container systems.

## Hardware and Verification

- **Register-Transfer Level (RTL)** describes clocked hardware behavior; **simulation** computes a model over time.
- **Design Under Test (DUT) / Device Under Verification (DUV)** is the design being tested. A **testbench** drives inputs and checks outputs.
- **Direct Programming Interface (DPI)** is a SystemVerilog foreign-language interface; **Verilog Procedural Interface (VPI)** and **Programming Language Interface (PLI)** are different simulator-facing interfaces with distinct standards and use cases.
- **Direct Memory Access (DMA)** lets a device transfer data to/from memory with CPU setup and platform-specific coordination; it does not mean the CPU is never involved.
- **Memory-Mapped I/O (MMIO)** exposes device registers through memory-addressed accesses; mapping and ordering rules depend on the architecture and OS.

## Reliability Reminder

Bound retries. Add timeouts. Use backoff to avoid synchronized retry bursts. Make repeatable operations idempotent when practical. A health check is one signal, not proof that every user operation works.
