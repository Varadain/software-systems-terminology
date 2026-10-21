# Flexible Learning Roadmap

**Navigation:** [Home](../README.md) | [Topic Index](index.md)

Study one stage at a time. Skip material you already know, and return to a prerequisite when a later term becomes unclear. For each stage, explain one idea in your own words and use the review boxes as a short revision checklist.

## Stage 1 — Computer and Software Basics

- **Objective:** Recognize a program, component, interface, and runtime.
- **Prerequisites:** None.
- **Read:** [Software architecture](topics/fundamentals/software-architecture.md) → [Tools and environments](topics/tools-and-environments/tools-and-environments.md).
- **Knowledge check:** How can an interface remain stable while its implementation changes?
- **Review:** [ ] Define component and API. [ ] Give an example of a runtime. [ ] Name one way components integrate.
- **Connect:** [API vs protocol](comparisons/interfaces-and-communication.md#api-and-protocol).

## Stage 2 — Client/Server and APIs

- **Objective:** Trace requests, responses, resources, and API styles.
- **Prerequisites:** Stage 1.
- **Read:** [APIs and communication](topics/apis-and-communication/apis-and-communication.md) → [interfaces comparisons](comparisons/interfaces-and-communication.md).
- **Knowledge check:** What is an API responsible for, and what does HTTP add?
- **Review:** [ ] Trace a request and response. [ ] Distinguish REST from RPC. [ ] Name one API error case.
- **Connect:** [HTTP and transport](topics/networking/networking-and-distributed-systems.md).

## Stage 3 — Networking and Distributed Systems

- **Objective:** Understand names, connections, messages, intermediaries, and failure handling.
- **Prerequisites:** Stage 2.
- **Read:** [Networking](topics/networking/networking-and-distributed-systems.md) → [request algorithms](../examples/algorithms.md).
- **Knowledge check:** What does a timeout tell a client, and what does it not tell the client?
- **Review:** [ ] Distinguish DNS, TCP, UDP, and IP. [ ] Explain proxy vs gateway. [ ] Name a safe retry condition.
- **Connect:** [Reliability and delivery](comparisons/delivery-and-reliability.md).

## Stage 4 — Programming Languages and Builds

- **Objective:** Follow source code through compilation, linking, loading, and execution.
- **Prerequisites:** Stage 1; Stage 2 is helpful for API examples.
- **Read:** [Programming and execution](topics/programming-and-compilation/programming-and-execution.md) → [compiler/tool comparisons](comparisons/data-languages-and-security.md).
- **Knowledge check:** Which stage resolves a reference to a function in another object file?
- **Review:** [ ] Order compiler, assembler, linker, and loader. [ ] Distinguish object file and executable. [ ] Explain one ABI issue.
- **Connect:** [Toolchains](topics/tools-and-environments/tools-and-environments.md).

## Stage 5 — Operating Systems, Processes, and Memory

- **Objective:** Understand OS services, process/thread execution, virtual memory, and synchronization.
- **Prerequisites:** Stage 4.
- **Read:** [Operating systems and Linux](topics/operating-systems/operating-systems-and-linux.md) → [computer architecture](topics/computer-architecture/computer-architecture-and-memory.md).
- **Knowledge check:** How can threads share data, and what problem can that create?
- **Review:** [ ] Distinguish process and thread. [ ] Describe a system call. [ ] Explain a page fault and a mutex.
- **Connect:** [Execution comparisons](comparisons/execution-and-testing.md).

## Stage 6 — Data, Configuration, and Automation

- **Objective:** Recognize common data formats, schemas, configuration, and telemetry.
- **Prerequisites:** Stage 1.
- **Read:** [Data and automation](topics/data-and-automation/data-configuration-and-automation.md) → [data format comparisons](comparisons/data-languages-and-security.md).
- **Knowledge check:** Can syntactically valid JSON still violate an API contract?
- **Review:** [ ] Compare JSON, XML, and YAML. [ ] Explain schema vs format. [ ] Distinguish log, metric, and trace.
- **Connect:** [API contracts](topics/apis-and-communication/apis-and-communication.md).

## Stage 7 — Git, CI/CD, and Deployment

- **Objective:** Understand version history, code review, automated checks, artifacts, and release.
- **Prerequisites:** Stages 1 and 4.
- **Read:** [Git and DevOps](topics/git-and-devops/git-and-devops.md) → [delivery comparisons](comparisons/delivery-and-reliability.md).
- **Knowledge check:** Why can CI pass without deploying a release?
- **Review:** [ ] Describe working tree, staging, and commit. [ ] Distinguish CI, delivery, and deployment. [ ] Explain rollback.
- **Connect:** [CI examples](../examples/algorithms.md#basic-ci-pipeline).

## Stage 8 — Testing, Debugging, and Reliability

- **Objective:** Choose test levels and use evidence to investigate failures.
- **Prerequisites:** Stages 4 and 7 are helpful.
- **Read:** [Testing and debugging](topics/testing-and-debugging/testing-debugging-and-reliability.md) → [execution and testing comparisons](comparisons/execution-and-testing.md).
- **Knowledge check:** What does a coverage result tell you, and what does it not prove?
- **Review:** [ ] Compare unit, integration, system, and end-to-end tests. [ ] Explain mock vs stub vs fake. [ ] Distinguish SLI, SLO, and SLA.
- **Connect:** [Observability and reliability](topics/security-and-reliability/security-and-reliability.md).

## Stage 9 — Hardware/Software Integration and Verification

- **Objective:** Understand RTL verification, simulation, and language boundaries.
- **Prerequisites:** Stages 4 and 5.
- **Read:** [Hardware and verification](topics/hardware-and-verification/hardware-and-verification.md) → [hardware comparisons](comparisons/hardware-and-verification.md) → [engineering scenarios](../examples/everyday-scenarios.md).
- **Knowledge check:** What does DPI connect, and how is it different from a simulator API such as VPI?
- **Review:** [ ] Trace stimulus to scoreboard. [ ] Distinguish simulation, emulation, and FPGA prototype. [ ] Explain MMIO and DMA.
- **Connect:** [Computer architecture](topics/computer-architecture/computer-architecture-and-memory.md).

## Stage 10 — Computer Architecture and Power

- **Objective:** Connect processor caches, memory, interconnects, ordering, and low-power terms.
- **Prerequisites:** Stage 5.
- **Read:** [Computer architecture and memory](topics/computer-architecture/computer-architecture-and-memory.md) → [hardware verification](topics/hardware-and-verification/hardware-and-verification.md).
- **Knowledge check:** Why does cache coherence not define the full order of all memory operations?
- **Review:** [ ] Explain cache hit/miss. [ ] Distinguish coherence from consistency. [ ] Compare clock gating and power gating.
- **Connect:** [Memory comparison](comparisons/hardware-and-verification.md#cache-coherence-and-memory-consistency).

## Stage 11 — Security Fundamentals

- **Objective:** Recognize identity, access, cryptography, and trust boundaries.
- **Prerequisites:** Stages 2 and 3.
- **Read:** [Security and reliability](topics/security-and-reliability/security-and-reliability.md) → [security comparisons](comparisons/data-languages-and-security.md).
- **Knowledge check:** Why does an authenticated user still need an authorization decision?
- **Review:** [ ] Distinguish authentication and authorization. [ ] Compare encryption, hashing, and encoding. [ ] Name one secret-handling practice.
- **Connect:** [API security terms](topics/apis-and-communication/apis-and-communication.md).

## Stage 12 — Common Confusions and Revision

- **Objective:** Explain relationships between terms across domains.
- **Prerequisites:** Any earlier stages relevant to your goals.
- **Read:** [All comparisons](comparisons/index.md) → [quick reference](reference/quick-reference.md) → [flashcards](reference/flashcards.md) → [glossary index](reference/glossary-index.md).
- **Knowledge check:** Choose one term, name a related term, and explain one failure mode.
- **Review:** [ ] Answer five flashcards without notes. [ ] Revisit missed comparisons. [ ] Explain one software example and one hardware example aloud.
- **Connect:** [Concept maps](reference/concept-maps.md).
