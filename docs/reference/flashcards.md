# Flashcards and Interview-Style Questions

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Roadmap](../learning-roadmap.md)

Try answering before opening the short answer. The cards test relationships, not acronym recall alone.

| Question | Short answer |
|---|---|
| What does an API tell a caller? | Which operations or data are available and the rules for using them. |
| Is HTTP the same thing as an API? | No. HTTP is a protocol; an API is an interface. A web API may use HTTP. |
| What work does DNS do? | It maps names to resource records, often including addresses, through a distributed naming system. |
| What is the difference between a process and a thread? | A process is a protected running program; a thread is an execution path managed within a process. |
| When is concurrency not parallelism? | When tasks overlap in progress but run one at a time on a single execution resource. |
| What is the linker's role? | It combines object files/libraries and resolves references to produce a program or library. |
| Why use a schema? | To describe expected data structure and constraints so producers and consumers can validate it. |
| What is the purpose of a Git commit? | It records a named snapshot of staged repository content and metadata. |
| How do CI and continuous deployment differ? | CI integrates and checks changes; continuous deployment automatically releases qualifying changes to production. |
| What should a test double replace? | A dependency whose behavior the test needs to control or observe; mocks, stubs, and fakes have different roles. |
| What does a scoreboard do in a testbench? | It compares observed design results with expected behavior, often from a reference model. |
| How do simulation and emulation differ broadly? | Simulation executes a model; hardware emulation uses specialized hardware to execute a design model faster. Exact tool meanings vary. |
| Why are cache coherence and memory consistency different? | Coherence concerns agreement about one memory location across caches; consistency constrains ordering across memory operations. |
| Does hashing hide a password? | A cryptographic password hash can make recovery costly, but hashing is not reversible encryption; password storage also needs salts and suitable algorithms. |
| What makes an operation idempotent? | Repeating it has the same intended effect as doing it once, under the operation's defined conditions. |
| What is one reason to use exponential backoff? | It spaces retries increasingly to reduce load during a persistent failure. |
| How does SystemVerilog DPI help? | It defines standardized calls between SystemVerilog and foreign code such as C, with type and direction rules. |
| What is the difference between firmware and a driver? | Firmware runs on or controls a device; a driver is software that lets an OS or runtime communicate with it. |
| Why is a coverage percentage not proof of correctness? | Coverage says which measured items were exercised, not whether requirements or expected results were correct. |
| What does a reverse proxy do? | It receives client traffic in front of one or more backend services and forwards or manages those requests. |

## Practice Prompt

Pick a browser request, a Linux process, or a simulated bus transaction. Name the interface, the protocol or rules, the data format, the expected result, and one failure mode.
