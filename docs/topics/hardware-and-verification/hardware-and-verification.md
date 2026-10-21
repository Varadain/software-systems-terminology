# Hardware and Verification

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

Hardware verification checks a design model against expected behavior before or alongside physical silicon. A simulator is a tool; a verification methodology organizes reusable test components and evidence. Tool options and standards evolve, so read the source version used by a project.

## Design and Verification Vocabulary

| Term | Meaning and use |
|---|---|
| **RTL / HDL / Verilog / SystemVerilog** | Register-Transfer Level describes how clocked state and logic transform data. A Hardware Description Language describes hardware. Verilog is an HDL; SystemVerilog extends it for design and verification. |
| **UVM** | Universal Verification Methodology: a reusable class-based methodology and library commonly used with SystemVerilog testbenches. Accellera provides a reference implementation; vendor support and revisions vary. |
| **DUT / DUV** | Design Under Test or Device Under Verification: the hardware block or system whose behavior is being checked. |
| **Testbench / BFM / VIP** | A testbench contains stimulus and checking around the DUT. A Bus Functional Model (BFM) models protocol-level activity. Verification IP (VIP) is reusable verification components, often protocol-aware. |
| **Driver / monitor / agent** | A driver applies transactions or signals. A monitor observes behavior without driving it. A UVM agent commonly groups a sequencer, driver, and monitor; *agent* has other meanings in software and distributed systems. |
| **Sequencer / sequence** | A sequencer arbitrates and supplies transactions to a driver. A sequence describes a stimulus scenario. |
| **Scoreboard / reference model** | A scoreboard compares observed results with expectations. A reference model computes an expected result from inputs or a specification. |
| **Assertion / coverage** | An assertion checks a property over time. Coverage records which conditions or scenarios occurred; code, functional, and assertion coverage answer different questions. |
| **Simulation / co-simulation / emulation / FPGA prototyping** | Simulation evaluates a model using a simulator. Co-simulation couples models or tools. Hardware emulation runs a design model on specialized emulation hardware. Field-Programmable Gate Array (FPGA) prototyping maps a design to programmable logic for system evaluation. The terms are tool-dependent and not interchangeable. |
| **Synthesis / elaboration / compilation** | Compilation translates source. Elaboration resolves parameters, hierarchy, and generated structures into a specific design instance. Synthesis transforms a hardware description into a gate-level implementation under constraints. |
| **Waveform / simulator / event-driven / cycle-accurate simulation** | A waveform displays signal values over time. A simulator evaluates the model. Event-driven simulation processes scheduled changes; cycle-accurate simulation preserves behavior at clock-cycle boundaries, with fidelity depending on model detail. |

## Timing, Clocks, and Low Power

| Term | Meaning and use |
|---|---|
| **Clock domain / reset domain** | A clock domain is logic governed by a particular clock. A reset domain is logic governed by a reset scheme. A design can contain multiple clock and reset domains. |
| **CDC / RDC** | Clock Domain Crossing and Reset Domain Crossing analysis checks signals crossing between domains with different clocks or reset behavior. Synchronizers and reset sequencing help address specific risks; tools and design rules matter. |
| **STA / timing constraint / SDC** | Static Timing Analysis checks timing paths against constraints without simulating every input sequence. A timing constraint describes clocks and path requirements. Synopsys Design Constraints (SDC) is a widely used constraint format; tool dialects may differ. |
| **Setup time / hold time** | Setup time is the minimum time data must be stable before a sampling edge; hold time is the minimum time it must remain stable after that edge. Violations can lead to incorrect sampling or metastability risk. |
| **Clock gating / power gating** | Clock gating stops clock activity to reduce dynamic switching in a block. Power gating disconnects a power domain from its supply, reducing leakage while requiring state and isolation handling. |
| **Power domain / UPF** | A power domain groups logic controlled by a power strategy. Unified Power Format (UPF) describes power intent, such as domains, isolation, and retention; supported syntax depends on standard/tool version. |
| **Retention / isolation / reset sequencing** | Retention preserves selected state across a power transition. Isolation prevents invalid signals from a powered-down domain from affecting active logic. Reset sequencing orders reset assertion and release across components. |
| **Low-power verification** | Checks that power-state transitions, isolation, retention, clock control, reset, and functional behavior meet the specified power intent. |

## Domain-Specific Meanings and PCI Express

Some short words carry different meanings across fields. Expand them when context could be unclear.

| Word | In software or networking | In hardware design or verification |
|---|---|---|
| **IP** | Internet Protocol, which routes packets between network addresses. | Intellectual Property (IP) core: a reusable design block intended for integration into a chip or system. Access and licensing vary by provider. |
| **Endpoint** | A reachable API operation, socket address, or service boundary. | In PCI Express, an Endpoint is a device/function at the edge of a PCIe hierarchy; it is distinct from a Root Complex. |
| **Driver** | Software that controls a device or offers a driver API. | In a testbench, code that drives design inputs or protocol transactions. In hardware, a signal driver is circuitry that drives a net. |
| **Agent** | A background or autonomous software participant. | A UVM verification component that usually groups stimulus and observation components. |
| **Bridge** | A component that adapts or connects two interfaces. | A hardware interconnect component that forwards or translates transactions between protocols or buses. |
| **Interface** | A software API or contract. | A set of signals and protocol rules between hardware blocks; SystemVerilog also has an `interface` construct. |

PCIe (Peripheral Component Interconnect Express) is a high-speed serial interconnect standard. A PCIe Root Complex connects the processor/memory side to the PCIe hierarchy; an Endpoint represents a device function in that hierarchy. A PCIe IP core may implement a protocol controller or other block, while PHY details and feature sets depend on the product and specification revision. The PCI-SIG specification portal identifies current PCI Express specifications; members can access its online library and non-members may purchase specifications. Its [PCI Express Basics & Background](https://pcisig.com/developer/education/pci-express-basics-background-17) session is an introductory overview; the presentation download is member-gated.

## Foreign-Language and Simulator Interfaces

| Term | Meaning and use |
|---|---|
| **DPI / DPI-C / SystemVerilog DPI** | The SystemVerilog Direct Programming Interface (SystemVerilog DPI) connects SystemVerilog code with foreign-language routines, especially C. DPI-C is the C-facing subset/convention. It specifies import/export declarations, data types, and call direction. |
| **VPI / PLI / FLI / VHPI** | The Verilog Procedural Interface (VPI) and earlier Programming Language Interface (PLI) are Verilog simulator interfaces; the Foreign Language Interface (FLI) and VHDL Procedural Interface (VHPI) belong to other language/tool contexts. They expose simulator objects or behavior differently; check simulator and standard versions. |
| **TLM** | Transaction-Level Modeling describes communication using transactions rather than individual signal transitions, often to model systems at a higher abstraction. |
| **FFI / C API / C ABI** | A Foreign Function Interface lets one language call another. A C API is a source-level interface. A C ABI is the binary calling/data convention used by compiled C-compatible components. |
| **Shared library / dynamic loading / symbol resolution** | A shared library is loaded separately from a program. Dynamic loading requests a library while execution is underway. Symbol resolution finds the implementation for a named function or object. |
| **Linker flags / include path / compiler flags / simulator flags** | Flags modify tool behavior. Include paths locate headers; compiler flags affect translation; linker flags affect library and symbol handling; simulator flags configure a simulation run. Exact syntax is tool-specific. |
| **Calling convention / data-type mapping / pointer conversion** | A calling convention defines how arguments and results cross a binary call boundary. Data-type mapping translates representations between languages. Pointer conversion must respect ownership, size, lifetime, and simulator rules. |
| **Callback / host / target** | A callback lets one side invoke a function provided by another. The host is the controlling or development environment; the target is the device or system being built or tested. These terms depend on context. |

### Simple DPI-style example

```systemverilog
import "DPI-C" function int add_from_c(input int a, input int b);
```

The declaration tells a SystemVerilog tool that a C routine can be called with compatible integer arguments. A real integration must also compile/link the routine, match ABI types, and follow the simulator's DPI rules.

## Hardware and Software Boundary

| Term | Meaning and use |
|---|---|
| **Firmware / driver API / driver** | Firmware is software stored or executed in a device or platform. A driver is software that controls a device through OS or runtime interfaces. A driver API is the boundary offered to its caller. |
| **MMIO / DMA / interrupt** | Memory-Mapped I/O exposes device registers at addresses. Direct Memory Access lets a device transfer data to/from memory after software setup and platform-specific mapping/synchronization. An interrupt notifies a processor of an event. |
| **Bus transaction / protocol adapter / hardware abstraction layer** | A bus transaction is one protocol-defined operation. A protocol adapter translates or bridges one protocol/interface to another. A Hardware Abstraction Layer (HAL) presents a software-facing interface that hides some device details. |
| **C API / C ABI / pointer conversion** | A C API can be stable at source level while a changed data layout or calling convention breaks binary compatibility. Cross-language code needs explicit, compatible representations and ownership rules. |

**Common confusion:** DPI is one language boundary; it is not a general synonym for API. A UVM agent is a verification component, while a software agent may be a background or autonomous program. A driver can be a software component, a verification component that drives pins, or a device that drives a bus—context matters.

**References:** [IEEE 1800-2023 SystemVerilog](https://ieeexplore.ieee.org/document/10458102); [IEEE 1364-2005 Verilog (legacy PLI/VPI)](https://ieeexplore.ieee.org/document/1620780); [IEEE SA: IEEE 1076-2019 VHDL status](https://standards.ieee.org/ieee/1076/5179/); [Accellera UVM](https://www.accellera.org/community/uvm); [Accellera UVM working group](https://accellera.org/activities/working-groups/uvm); [Arm AMBA AXI/ACE, Issue L](https://developer.arm.com/documentation/ihi0022/l/); [PCI-SIG Basics & Background](https://pcisig.com/developer/education/pci-express-basics-background-17); [PCI-SIG specifications](https://pcisig.com/specifications); [Linux kernel Driver API](https://docs.kernel.org/driver-api/index.html).
