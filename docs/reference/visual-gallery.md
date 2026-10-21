# SVG Visual Gallery

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Roadmap](../learning-roadmap.md)

This page collects the repository's teaching diagrams in one place for review. Each SVG is also available as a standalone file in [`assets/images/`](../../assets/images). The diagrams use a consistent palette and include an accessible title and description.

## APIs, Protocols, and Data

### Request and response

![A client sends a request through a server and receives a response.](../../assets/images/request-flow.svg)

### API, ABI, and SDK

![API describes a software interface, ABI describes a binary-level contract, and an SDK packages tools and libraries.](../../assets/images/api-abi-sdk.svg)

### REST and RPC

![REST models resources and representations; RPC models calling remote operations.](../../assets/images/rest-and-rpc.svg)

### HTTP, TCP, and sockets

![HTTP messages use a transport such as TCP, while a socket is a programming endpoint for communication.](../../assets/images/http-tcp-socket.svg)

### Proxy, gateway, and load balancer

![A proxy mediates requests, a gateway connects systems, and a load balancer distributes traffic.](../../assets/images/proxy-gateway-load-balancer.svg)

### JSON, XML, and YAML

![The same small data structure represented as JSON, XML, and YAML.](../../assets/images/json-xml-yaml.svg)

## Programming and Operating Systems

### From code to execution

![Source code passes through compilation and linking before a program runs.](../../assets/images/code-to-execution.svg)

### Process and thread

![A process owns resources and can contain one or more threads that execute within it.](../../assets/images/process-and-thread.svg)

### Concurrency and parallelism

![Concurrency interleaves tasks on one worker; parallelism runs tasks simultaneously on separate workers.](../../assets/images/concurrency-parallelism.svg)

### Operating system boundary

![An application requests operating system services through system calls.](../../assets/images/operating-system-boundary.svg)

### Virtual address translation

![The memory management unit and page table map a process virtual address to a physical frame.](../../assets/images/virtual-address-translation.svg)

## Building, Testing, and Reliability

### Git commit flow

![Working tree changes are staged in the index and recorded in a repository commit.](../../assets/images/git-commit-flow.svg)

### CI/CD pipeline

![A CI/CD pipeline builds and tests changes before delivery and deployment.](../../assets/images/ci-cd-pipeline.svg)

### Test levels

![Unit, integration, and end-to-end tests cover progressively broader system behavior.](../../assets/images/test-levels.svg)

### Testbench architecture

![A driver sends transactions to a design under test while a monitor and scoreboard check behavior.](../../assets/images/testbench-architecture.svg)

### Test doubles

![A stub, mock, and fake replace dependencies in different ways during tests.](../../assets/images/test-doubles.svg)

### Retry and backoff

![A failed operation is retried with increasing delays and eventually succeeds or stops at a limit.](../../assets/images/retry-backoff.svg)

### Reliability and observability

![Logs, metrics, and traces provide evidence for understanding system health and failures.](../../assets/images/reliability-observability.svg)

## Security

### Authentication and authorization

![Authentication establishes identity; authorization checks what that identity may do.](../../assets/images/authentication-authorization.svg)

### Encryption, hashing, and encoding

![Encryption is reversible with a key, hashing creates a digest, and encoding changes representation.](../../assets/images/encryption-hashing-encoding.svg)

## Hardware and Architecture

### Cache coherence and memory ordering

![Cache coherence keeps shared cached values consistent; memory ordering constrains how operations are observed.](../../assets/images/cache-coherence-memory-ordering.svg)

### Programmed I/O and DMA

![Programmed I/O has the CPU move data; DMA lets a device transfer data with less CPU involvement.](../../assets/images/programmed-io-vs-dma.svg)

### Simulation, emulation, and FPGA prototyping

![Simulation models behavior, emulation accelerates a hardware model, and FPGA prototyping runs mapped logic.](../../assets/images/simulation-emulation-fpga.svg)

### DPI, VPI, and PLI

![DPI, VPI, and PLI provide different ways to connect code with a hardware simulator.](../../assets/images/dpi-vpi-pli.svg)

### SystemVerilog interface and modports

![A SystemVerilog interface groups signals and modports define how connected components use them.](../../assets/images/systemverilog-interfaces.svg)

### PCIe hierarchy

![A Root Complex connects the host platform to a PCIe switch and endpoint devices.](../../assets/images/pcie-hierarchy.svg)

### Clock and power gating

![Clock gating reduces switching activity; power gating shuts off a power domain.](../../assets/images/clock-and-power-gating.svg)
