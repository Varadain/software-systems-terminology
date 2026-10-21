# Software and Systems Quick Guide

Short explanations for common software, networking, operating-system, hardware, and development terms.

**Find a term:** Press **Ctrl+F** (Windows/Linux) or **Cmd+F** (Mac), then type a word or acronym.

## Contents

- [Software foundations and architecture](#software-foundations-and-architecture)
- [APIs and communication](#apis-and-communication)
- [Networking and distributed systems](#networking-and-distributed-systems)
- [Programming and execution](#programming-and-execution)
- [Operating systems and Linux](#operating-systems-and-linux)
- [Data, configuration, and automation](#data-configuration-and-automation)
- [Git, CI, and delivery](#git-ci-and-delivery)
- [Testing, debugging, and reliability](#testing-debugging-and-reliability)
- [Hardware and verification](#hardware-and-verification)
- [Computer architecture and memory](#computer-architecture-and-memory)
- [Security and reliability](#security-and-reliability)
- [Tools and environments](#tools-and-environments)

## Software foundations and architecture

Software architecture describes the major parts of a system and the ways they interact. Think of a system as a workshop: tools have jobs, shared rules let people hand work off, and the arrangement affects how easily the workshop can change.

### People, Boundaries, and Reusable Parts

| Term | Quick explanation |
|---|---|
| **Client** | A program or component that requests data or work from another component. A browser is a client when it requests a page. |
| **Server** | A program or component that accepts requests and returns data or performs work. These are roles for a particular interaction; one program can take both roles. |
| **API** | Application Programming Interface: the operations and rules a software component exposes to callers. A test tool may ask a service API for a run result. |
| **ABI** | Application Binary Interface: low-level rules that let separately compiled pieces work together, such as calling conventions, symbol names, and data layout. |
| **SDK** | Software Development Kit: APIs plus tools, libraries, examples, and documentation for building against a platform or service. |
| **CLI / GUI** | Command-Line Interface accepts typed commands and arguments; Graphical User Interface presents controls such as windows and buttons. Both are user interfaces. |
| **Interface / contract** | An interface is an agreed boundary for interaction; a contract states the expected inputs, outputs, and behavior. The word *interface* also has hardware and language-specific meanings. |
| **Abstraction / implementation** | An abstraction presents the useful idea while hiding details; an implementation is the concrete code or hardware that realizes it. |
| **Module / component** | A module is a named unit of organization, often within one program or package. A component is a replaceable part with defined responsibilities and boundaries. |
| **Library / framework** | A library supplies reusable functions that your code calls. A framework supplies structure and often calls your code at defined extension points. |
| **Package / dependency** | A package is a distributable unit of code or metadata. A dependency is something a component needs, such as another package, service, or tool. |
| **Plugin / extension** | An optional add-on loaded by a host to provide extra behavior. The exact term depends on the host ecosystem. |
| **Runtime / daemon / service** | A runtime provides the environment that executes a program. A daemon is a background process; a service is a broader function made available to other programs or users. |
| **Microservice / monolith** | A microservice is a separately operated service organized around a limited responsibility. A monolith is an application built and deployed as one unit. Either design can be appropriate; size alone is not the deciding factor. |
| **Callback / hook** | A callback is a function supplied to run after an event or operation. A hook is an exposed extension point where custom behavior can be attached. |
| **Coupling / cohesion** | Coupling describes how strongly parts depend on one another; cohesion describes how closely a part's responsibilities belong together. Designs often aim for manageable coupling and focused cohesion. |
| **Design pattern / architecture** | A design pattern is a reusable approach to a recurring design problem. Architecture is the higher-level structure and important decisions of a system. |
| **Integration** | Connecting components so they exchange data or work together. An interface contract helps reduce surprises at the boundary. |

### Intermediaries and Adaptation

| Term | Quick explanation |
|---|---|
| **Middleware** | Software in a request or data path that applies shared behavior, such as logging or authorization. It is a role, not a specific product. |
| **Adapter / wrapper / facade** | An adapter translates one interface into another; a wrapper encloses an object or function to add or change access; a facade offers a simpler front to a more complex subsystem. |
| **Proxy** | An intermediary that sends requests on behalf of another party. A forward proxy is commonly configured by clients; a reverse proxy fronts servers. |
| **Gateway / API gateway** | A gateway connects systems or networks and may translate protocols. An API gateway commonly centralizes API routing and related policies such as authentication or rate limits. |
| **Bridge** | A component that connects two systems or domains, often translating between their interfaces or representations. In hardware, *bridge* may name a protocol or bus interconnect component. |
| **Broker / agent / orchestrator** | A broker mediates messages or service access. An agent is a context-dependent participant that performs work for a framework or system. An orchestrator coordinates multiple components or tasks. |

## APIs and communication

An API defines how a caller asks for an operation or data. A protocol defines rules for exchanging messages. A data format defines how the message content is represented. These layers often work together but are not interchangeable.

### API Styles and Web Protocols

| Term | Quick explanation |
|---|---|
| **Application Programming Interface (API)** | A defined set of operations, inputs, outputs, and behavior available to a caller. Example: `GET /runs/105` asks a test service for a run. |
| **REST / RESTful API** | REST (Representational State Transfer) is an architectural style that uses resource-oriented interactions and constraints. A RESTful API follows those constraints to some degree; a JSON-over-HTTP endpoint is not automatically REST. |
| **RPC / gRPC / XML-RPC** | RPC (Remote Procedure Call) makes a remote operation feel like a procedure call. gRPC is a remote-call framework that commonly uses Protocol Buffers and HTTP/2. XML-RPC is an RPC convention that encodes calls and results in Extensible Markup Language (XML). |
| **HTTP / HTTPS** | HTTP (Hypertext Transfer Protocol) defines request/response semantics. HTTPS (HTTP Secure) is HTTP carried over a secure transport, typically Transport Layer Security (TLS). |
| **HTTP/1.1, HTTP/2, HTTP/3** | HTTP versions have different message framing and transport behavior while sharing core semantics. HTTP/1.1 and HTTP/2 commonly use TCP; HTTP/3 uses QUIC over UDP. |
| **TCP / UDP / IP** | Transmission Control Protocol provides an ordered byte stream with connection state. User Datagram Protocol sends datagrams with fewer transport guarantees. Internet Protocol routes packets between network addresses. |
| **DNS / TLS / SSH** | Domain Name System resolves names using records. Transport Layer Security protects a communication channel. SSH (Secure Shell) provides authenticated remote login and related secure communication. |
| **WebSocket / socket** | WebSocket provides a long-lived, bidirectional web connection. A socket is an OS or language interface for communication endpoints; it can use local or network transports. |
| **URI / URL / endpoint** | A Uniform Resource Identifier (URI) names a resource; a Uniform Resource Locator (URL) is a URI form that gives a way to locate it. An endpoint is a particular interface or address where a service can be reached. |

### Message Parts and Exchange

| Term | Quick explanation |
|---|---|
| **Request / response** | A request communicates what a client asks for; a response reports an outcome and may include data. |
| **Header / body / payload** | Headers carry message metadata; a body carries content. Payload means the data of interest, often the body but sometimes a part of it. |
| **Status code / route / routing** | An HTTP status code summarizes the response outcome. A route maps an address and method to a handler. Routing chooses where a message should go. |
| **Serialization / deserialization** | Serialization turns in-memory data into a transferable or storable representation. Deserialization reconstructs a usable value from that representation. |
| **JSON / XML / Protocol Buffers / schema** | JSON and XML are text-based data formats; Protocol Buffers is a schema-based binary serialization system. A schema describes fields, types, and constraints. |
| **Authentication / authorization** | Authentication establishes an identity; authorization decides what it may do. |
| **API key / bearer token / session / cookie** | An API key identifies a client or application. A bearer token grants access to whoever possesses it. A session stores state about an interaction; a cookie is browser-managed data often used to carry a session identifier. Protect all secrets and credentials. |
| **CORS** | Cross-Origin Resource Sharing is a browser security mechanism that lets a server state which cross-origin browser requests it permits. It is not a general server-to-server access-control system. |
| **Timeout / retry / rate limiting** | A timeout bounds how long a caller waits. A retry repeats an operation after selected failures. Rate limiting restricts request frequency. Retries should be bounded and safe for the operation. |
| **Idempotency** | Repeating an operation has the same intended effect as doing it once. HTTP defines method semantics, but an application may need an idempotency key for safe retry of a create/payment operation. |
| **Pagination / versioning / backward compatibility** | Pagination splits a large result into manageable portions. Versioning identifies an API or data-contract revision. Backward compatibility means newer changes continue to support defined older uses. |

## Networking and distributed systems

A distributed system has parts that communicate across process or machine boundaries. The network can delay, lose, duplicate, reorder, or reject work, so a design must describe how it detects and handles failure.

### Communication Basics

| Term | Quick explanation |
|---|---|
| **Client-server architecture** | Components take requester and provider roles for an exchange. Those are roles, not permanent types of machine. |
| **Peer-to-peer (P2P)** | Participants communicate as peers and may both provide and request resources. |
| **Connection-oriented / connectionless** | Connection-oriented communication maintains connection state and may provide delivery guarantees. Connectionless communication sends independent messages without establishing that state. |
| **Packet / frame / segment / datagram** | A frame is a link-layer unit; an Internet Protocol (IP) packet carries network-layer data; a Transmission Control Protocol (TCP) segment carries TCP data; a User Datagram Protocol (UDP) datagram carries UDP data. Exact encapsulation varies. |
| **DNS resolution** | A resolver queries the Domain Name System (DNS) to obtain records for a name, such as an address. Cached results may be reused until their time-to-live policy expires. |
| **TCP handshake / TLS handshake** | A TCP handshake establishes transport state. A Transport Layer Security (TLS) handshake negotiates a secure session and authenticates the server (and optionally the client); it is a separate protocol exchange. |
| **Routing / switching** | Routing selects a path between IP networks. Switching forwards frames within a local network using link-layer information. |
| **Firewall / NAT** | A firewall applies traffic rules. Network Address Translation (NAT) rewrites address information between network domains, often to share addresses; it is not itself a security policy. |
| **Port** | A numbered network endpoint that directs traffic to a service on a device. For example, TCP port 443 is commonly used for HTTPS. |

### Intermediaries and Service Patterns

| Term | Quick explanation |
|---|---|
| **Load balancer** | Distributes requests or connections across multiple targets according to a policy and health information. |
| **Reverse proxy** | Accepts traffic for backend services and forwards it, often handling TLS, routing, caching, or request limits. |
| **Service discovery** | Finds the current address or identity of a service instance, which may move or scale over time. |
| **Message queue / message broker / event bus** | A queue stores messages for consumers to process; a message broker mediates message exchange; an event bus distributes event notifications among producers and subscribers. |
| **Publish-subscribe (pub/sub)** | Publishers emit messages under a topic or channel; subscribers receive messages for topics they follow. Delivery, ordering, and durability depend on the system. |
| **Synchronous communication / asynchronous communication** | Synchronous callers wait for a result as part of the interaction. Asynchronous communication lets work proceed and returns results later or through another channel. |
| **Polling / streaming** | Polling asks repeatedly whether new data is available. Streaming delivers a continuing sequence of data or events over time. |
| **Heartbeat / health check** | A heartbeat signals that a component is still communicating. A health check asks whether a service meets a specific readiness or liveness condition. Neither proves every operation works. |

### Failures and Distributed Behavior

| Term | Quick explanation |
|---|---|
| **Circuit breaker** | A client-side pattern that stops repeatedly calling a failing dependency for a period, then permits a limited recovery check. |
| **Retry policy / exponential backoff** | A retry policy selects which failures to retry and how many times. Exponential backoff increases the wait between attempts, often with jitter to avoid synchronized retries. |
| **Eventual consistency** | Replicas may temporarily disagree but are expected to converge if updates stop and communication resumes. It does not mean every read is immediately current. |
| **Replication / failover** | Replication keeps copies of data or service state. Failover moves work to a backup after a failure; safe failover depends on state and coordination. |
| **Fault tolerance** | A system continues to provide defined behavior despite selected faults. It is bounded by the faults the design anticipates. |
| **Distributed tracing** | A trace links timed operations across services to help explain one request's path. Traces complement logs and metrics. |

## Programming and execution

Programs pass through representations before they run. The precise path depends on the language, compiler, operating system, and runtime.

### From Text to a Running Program

| Term | Quick explanation |
|---|---|
| **Source code / machine code / assembly** | Source code is a human-oriented program text. Machine code is instructions for a processor architecture. Assembly is a readable notation for machine instructions. |
| **Lexer / token / parser / syntax / semantics** | A lexer groups characters into tokens. A parser checks their grammatical structure. Syntax describes allowed structure; semantics describes what that structure means. |
| **Abstract Syntax Tree (AST)** | A tree representation of parsed program structure, with details such as punctuation usually removed. |
| **Compiler / interpreter / assembler** | A compiler translates a program into another representation, often native code. An interpreter executes source or an intermediate form. An assembler translates assembly into machine-level object code. Real tools can combine these roles. |
| **Preprocessor** | Handles source directives before or during compilation, such as conditional inclusion or macro expansion. Exact behavior is language-specific. |
| **Intermediate representation (IR) / bytecode** | An Intermediate Representation (IR) is a compiler's internal or shared representation. Bytecode is an instruction format designed for a virtual machine or runtime rather than one physical CPU. |
| **JIT / AOT** | Just-in-time (JIT) compilation translates code during execution. Ahead-of-time (AOT) compilation translates it before execution. Toolchains may combine both. |
| **Object file / executable / binary** | An object file contains compiled code and metadata for later linking. An executable is prepared to run by a system. *Binary* broadly means a non-text representation and is sometimes used loosely for either file. |
| **Linker / loader** | A linker combines object files and libraries and resolves references. A loader maps a program and its dependencies into memory and begins execution. |
| **Symbol / symbol table** | A symbol names a function, variable, or other entity. A symbol table records names and associated metadata used by compilers, linkers, loaders, and debuggers. |
| **Static / dynamic linking** | Static linking copies needed library code into a program at link time. Dynamic linking resolves and loads shared code separately, commonly at load time or while running. |
| **Shared library / DLL / ELF** | A shared library can serve multiple programs through dynamic linking. DLL is the common Windows term for a dynamic-link library. ELF (Executable and Linkable Format) is a widely used executable and object-file format on Unix-like systems. |
| **ABI compatibility** | Binary compatibility means compiled components agree on conventions such as calling rules, symbol names, and data layout. Source compatibility alone does not guarantee ABI compatibility. |
| **Build system / build target / dependency graph** | A build system runs steps to produce outputs. A build target is a requested output or action. A dependency graph records which inputs must be ready before each output. |
| **Package manager** | Installs, updates, and tracks software packages and dependencies. It may resolve versions and platform constraints. |
| **Virtual machine** | A software environment that executes a defined instruction set or presents a virtual computer. The term can mean a process runtime (such as a bytecode VM) or a whole-system virtual machine. |

### Values, Memory, and Errors

| Term | Quick explanation |
|---|---|
| **Garbage collection / memory allocation** | Allocation reserves memory for values. Garbage collection reclaims some allocated memory when the runtime determines it is no longer reachable; not every language uses garbage collection. |
| **Stack / heap** | Stack commonly holds call frames and local execution state. Heap commonly holds dynamically allocated objects. These are programming concepts; actual memory layout varies. |
| **Pointer / reference / value** | A pointer contains an address. A reference provides a way to access an object, with language-specific rules. A value is the data itself or a value-level representation. |
| **Scope / namespace** | Scope determines where a name can be used. A namespace groups names to avoid accidental conflicts. |
| **Exception / error / warning** | An exception is a language/runtime mechanism for reporting an unusual condition. An error indicates a failure or incorrect state. A warning reports a concern that may not stop execution. |
| **Undefined behavior** | In languages such as C and C++, this describes cases where the language specification places no requirements on the result; code relying on it may behave unpredictably across builds. |
| **Process / thread / coroutine** | A process is an executing program instance; a thread is an execution path within a process; a coroutine is a cooperative unit of work that can suspend and resume. |
| **Concurrency / parallelism / asynchronous programming** | Concurrency organizes overlapping work; parallelism executes work simultaneously on multiple resources. Asynchronous programming lets a task suspend while waiting instead of blocking its execution resource. |

## Operating systems and Linux

An operating system (OS) manages shared hardware resources and offers services to programs. Linux names both an OS kernel and, commonly, a family of systems built around that kernel plus user-space tools.

### Processes and OS Interfaces

| Term | Quick explanation |
|---|---|
| **Operating system (OS) / kernel / user space / kernel space** | An operating system (OS) manages hardware resources and offers common services. The kernel is its privileged core. User space runs ordinary applications with restricted privileges; kernel space is where the kernel executes privileged code. |
| **System call** | A controlled request from a program to the kernel, such as opening a file or creating a process. A library API may wrap one or more system calls. |
| **Process / thread / scheduler / context switch** | A process is a running program with resources and an address space. Threads are execution paths within a process. The scheduler selects runnable work; a context switch changes the active execution state. |
| **Interrupt / exception / signal** | A hardware interrupt asks the CPU to handle an event. A processor exception arises from instruction execution, such as a page fault. A Unix signal is an OS notification delivered to a process or thread. These names belong to different layers. |
| **File descriptor / file system** | A file descriptor is a small process-local handle for an open file, socket, pipe, or other resource on Unix-like systems. A file system organizes names and persistent data. |
| **Permissions** | Rules controlling access to a resource, such as read, write, and execute rights. The model and details differ across operating systems and file systems. |

### Shell and Command-Line Terms

| Term | Quick explanation |
|---|---|
| **Shell / terminal** | A shell interprets commands and scripts. A terminal is a text input/output interface; a terminal emulator hosts a shell window. |
| **Standard input / standard output / standard error** | Conventionally file descriptors 0, 1, and 2 for input, ordinary output, and diagnostics respectively. Programs may redirect them. |
| **Pipe / redirection** | A pipe connects one program's output to another's input. Redirection sends input or output to a file or another destination. |
| **Environment variable** | A named value inherited by a process from its environment, often used for configuration such as `PATH`. Avoid putting secrets in logs or command histories. |
| **Daemon / service manager** | A daemon is a background process. A service manager starts, stops, and supervises system services; systemd is one common Linux example, not the only one. |
| **Driver / device tree / bootloader / firmware** | A driver controls or communicates with a device. A device tree describes hardware for an OS, especially in embedded systems. A bootloader starts the system and loads later software. Firmware is low-level software associated with a device or platform. |

### Memory and Coordination

| Term | Quick explanation |
|---|---|
| **Virtual memory / page table / page fault / TLB** | Virtual memory gives a process an address space mapped to physical memory. Page tables describe mappings. A page fault occurs when access needs OS handling. A Translation Lookaside Buffer (TLB) caches address translations. |
| **Mutex / semaphore / spinlock** | A mutex grants one owner access to a protected region. A semaphore tracks a count of available resources or signals. A spinlock waits by repeatedly checking; it is suited only to contexts where waiting is expected to be very short. |
| **Deadlock / race condition / starvation** | Deadlock is a cycle of waits that prevents progress. A race condition occurs when behavior depends on uncontrolled timing. Starvation is prolonged denial of a resource or execution opportunity. |
| **Atomic operation** | An operation observed as indivisible with respect to specified concurrent observers. Atomicity and memory-order guarantees depend on the language and hardware contract. |
| **Shared memory / IPC** | Shared memory lets processes access a common mapped region. Interprocess communication (IPC) includes mechanisms such as pipes, sockets, message queues, and shared memory. |
| **`mmap` / memory-mapped I/O (MMIO)** | `mmap` maps files or devices into a process address space on supported systems. MMIO accesses device registers through designated addresses and must follow platform-specific mapping and ordering rules. |

## Data, configuration, and automation

Programs exchange data and settings using agreed representations. A format is not automatically a schema: the format describes how values are written, while a schema describes which values and structures are expected.

### Formats and Structure

| Term | Quick explanation |
|---|---|
| **JSON** | JavaScript Object Notation: a text format for objects, arrays, strings, numbers, booleans, and null. Common for web APIs and configuration. |
| **YAML** | YAML Ain't Markup Language: a human-readable data serialization language often used for configuration. Indentation affects structure, so whitespace matters. |
| **XML** | Extensible Markup Language: a text format using nested elements and attributes, often with schemas and namespaces. |
| **CSV** | Comma-Separated Values: a tabular text format. Delimiter, quoting, and newline conventions matter; CSV is less expressive than a nested data format. |
| **TOML / INI** | TOML (Tom's Obvious, Minimal Language) and INI (initialization) are text formats often used for configuration. TOML has defined types and table structure; INI has several conventions and dialects rather than one universal specification. |
| **Schema / data model / metadata** | A schema describes permitted fields and constraints. A data model describes the concepts and relationships represented. Metadata is data that describes other data, such as units or timestamps. |
| **Configuration / manifest / configuration file** | Configuration changes program behavior without changing its code. A manifest records information about a package, project, deployment, or resource. A configuration file stores settings in a format such as TOML or YAML. |
| **API contract** | A shared agreement about an Application Programming Interface (API)'s operations, data, and behavior. It can be described with a schema or specification, but the contract may include behavior beyond field types. |
| **Parser / serializer** | A parser reads a representation and checks or converts its structure. A serializer converts values into a representation suitable for storage or exchange. |
| **Regular expression** | A compact pattern language for finding or validating text. It is useful for bounded text patterns, not a replacement for parsing nested languages. |

### Commands, Logs, and Automation

| Term | Quick explanation |
|---|---|
| **Command-line argument / CLI flag** | A Command-Line Interface (CLI) argument is a value passed to a command. A flag is an option that changes behavior, often written `--verbose` or `-v`. |
| **Environment variable** | A named value inherited by a process from its parent environment, often used to configure paths, modes, or service locations. Treat values that contain secrets as sensitive. |
| **Exit code** | A process result code. Many shells use zero for success and nonzero for a failure, but exact meanings are program-specific. |
| **Log / logging level / structured logging** | A log is a recorded event. A logging level labels urgency or detail. Structured logging stores fields, such as JSON key/value pairs, so tools can filter them. |
| **Event / telemetry / trace / metric** | An event records something that happened. Telemetry is data collected from a running system. A trace connects operations across a flow; a metric is a measured numeric value over time or a distribution. |
| **Validation** | Checking that data meets expected type, range, format, and business rules. Validate at trust boundaries and report errors clearly. |
| **Secrets management** | Practices and tools for storing, granting, rotating, and auditing secrets such as passwords and API tokens. Do not store secrets in source files or logs. |
| **Template** | A reusable pattern with placeholders filled from data, used to generate text, configuration, or other output. Validate generated output before using it. |

## Git, CI, and delivery

Git records changes to files so people can compare, restore, and combine work. GitHub is one hosted collaboration service that can store Git repositories and add reviews, issues, and automation.

### Git Vocabulary

| Term | Quick explanation |
|---|---|
| **Git / repository** | Git is a distributed version control system. A repository stores project content and its version history. |
| **Working tree / staging area / commit** | The working tree is the checked-out files. The staging area selects content for the next snapshot. A commit records a snapshot and metadata. |
| **Branch / merge / rebase / cherry-pick** | A branch is a movable name for a line of history. A merge joins histories. A rebase reapplies commits onto another base. Cherry-pick applies selected commit changes elsewhere. Rebase rewrites commit identities; use care with shared history. |
| **Tag** | A named reference commonly used to mark a release or other important commit. |
| **Remote / clone / fetch / pull / push** | A remote names another repository. Clone creates a local copy. Fetch retrieves updates without integrating them. Pull fetches and integrates according to configuration. Push sends local refs and objects to a remote. |
| **Pull request / code review / merge conflict** | A pull request proposes changes for discussion and integration on a hosting platform. Code review examines a change. A merge conflict means Git cannot automatically combine edits that overlap or interact. |
| **`.gitignore` / GitHub** | `.gitignore` patterns tell Git which untracked files to ignore; it does not remove already tracked files. GitHub is a hosting and collaboration platform, not Git itself. |

### CI/CD and Release Terms

| Term | Quick explanation |
|---|---|
| **CI / continuous integration** | Continuous Integration (CI) frequently integrates changes and runs checks to detect problems early. |
| **CD / continuous delivery / continuous deployment** | Continuous Delivery (CD) keeps changes in a releasable state, with release commonly gated by a human. Continuous Deployment (also abbreviated CD) automatically releases qualifying changes to production. Expand *CD* because it can mean either practice. |
| **Pipeline / stage / job / workflow / runner** | A pipeline is a sequence of automated work. A stage groups work; a job is a unit scheduled for execution; a workflow defines automation and triggers; a runner executes jobs. Terms vary among platforms. |
| **Build artifact / release / versioning / semantic versioning** | A build artifact is an output such as a package or binary. A release makes a version available. Versioning labels revisions; Semantic Versioning gives a convention for communicating compatibility through major, minor, and patch numbers. |
| **Container / container image / registry** | A container is an isolated process environment. An image is a packaged template used to start containers. A registry stores and distributes images. Container isolation shares the host kernel in common implementations. |
| **Virtual machine / infrastructure as code (IaC)** | A virtual machine emulates a computer platform and can run its own guest operating system. Infrastructure as Code (IaC) describes infrastructure in machine-readable files that tools can apply. |
| **Deployment / rollback / environment** | Deployment makes a version available in a target environment. Rollback returns to a previous version or configuration. Development, staging, and production are common environments with different purposes and controls. |
| **Canary release** | A release strategy exposes a new version to a limited share of traffic or users before wider rollout, so behavior can be observed and risk contained. |

## Testing, debugging, and reliability

Testing compares observed behavior with an expectation. Debugging uses evidence to find why behavior differs. Reliability describes whether a system keeps providing useful behavior under expected conditions and failures.

### Planning and Running Tests

| Term | Quick explanation |
|---|---|
| **Test case / test suite / test plan** | A test case specifies inputs, conditions, and expected results. A suite groups tests. A test plan describes scope, approach, resources, risks, and schedule. |
| **Testbench / fixture / setup / teardown** | A testbench supplies stimulus and checks a design or system. A fixture provides shared test data or environment. Setup prepares state; teardown cleans it up. |
| **Assertion / expected result / actual result** | An assertion checks a condition. The expected result is the requirement-derived outcome; the actual result is what execution produced. |
| **Pass / fail / skip / flaky test** | A pass meets the test's checks. A failure violates one. A skipped test is intentionally not run. A flaky test changes outcome across runs without a relevant code change, often due to timing or shared state. |
| **Reproduction steps / debugging / breakpoint / stack trace** | Reproduction steps describe how to trigger an issue. Debugging investigates it. A breakpoint pauses execution. A stack trace shows a call path associated with an event or failure. |
| **Log analysis / root cause analysis** | Log analysis looks for evidence in recorded events. Root cause analysis investigates underlying contributing conditions rather than stopping at a symptom. |
| **Defect / bug / issue / incident** | A defect or bug is a flaw in a product or process. An issue is a tracked item or problem. An incident is an operational event affecting service or users. Teams may define these terms differently. |
| **Severity / priority / regression** | Severity describes impact; priority describes urgency or ordering of work. A regression is a previously working behavior that breaks after a change, or a test that checks for such a break. |

### Test Levels and Purposes

| Term | Quick explanation |
|---|---|
| **Unit test** | Does one small function or component behave as expected? | Check a parser with valid and invalid text. |
| **Integration test** | Do connected components exchange data correctly? | Verify an API handler and its database adapter work together. |
| **System test** | Does the assembled system meet specified behavior? | Check a full test-results service against its contract. |
| **End-to-end test** | Can a user-level path cross the real system boundaries? | Create a test run in a UI and retrieve its result. |
| **Regression test** | Does a previously fixed behavior stay fixed after changes? | Re-run a test for an earlier parser defect. |
| **Smoke test** | Does a build or service pass a small set of basic checks? | Start the service and request its health endpoint. |

### Coverage and Test Techniques

| Term | Quick explanation |
|---|---|
| **Code coverage / branch coverage / functional coverage** | Code coverage measures which code executed. Branch coverage measures decision outcomes. Functional coverage measures whether specified behaviors, values, or scenarios were exercised. Coverage does not prove correctness. |
| **Mock / stub / fake / test double / mocking** | A test double replaces a dependency. A stub returns prepared responses; a mock records or verifies expected interactions; a fake is a lightweight working substitute. Mocking is the practice of replacing or observing dependencies with mock objects. Exact usage can vary by testing community. |
| **Fault injection / negative testing / boundary testing / fuzz testing** | Fault injection deliberately introduces failures. Negative testing checks invalid or rejected input. Boundary testing checks edges of ranges. Fuzz testing generates many varied inputs to find robustness defects. |
| **Static analysis / dynamic analysis / lint / sanitizer / profiling** | Static analysis examines code without running the target program. Dynamic analysis observes execution. A linter checks likely defects or style rules. A sanitizer detects selected runtime errors. Profiling measures resource use and performance. |
| **Monitoring / observability / alert** | Monitoring tracks known signals and conditions. Observability is the ability to investigate internal behavior from external outputs such as logs, metrics, and traces. An alert notifies when a defined condition is met. |
| **SLI / SLO / SLA** | A Service Level Indicator is a measurement of service behavior. A Service Level Objective is a target for an indicator. A Service Level Agreement is an external or contractual commitment, often with consequences. |
| **Availability / reliability / recovery** | Availability asks whether a service is usable when needed. Reliability asks whether it performs correctly over time. Recovery is restoring useful behavior after disruption. A service can be available yet unreliable. |

## Hardware and verification

Hardware verification checks a design model against expected behavior before or alongside physical silicon. A simulator is a tool; a verification methodology organizes reusable test components and evidence. Tool options and standards evolve, so read the source version used by a project.

### Design and Verification Vocabulary

| Term | Quick explanation |
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

### Timing, Clocks, and Low Power

| Term | Quick explanation |
|---|---|
| **Clock domain / reset domain** | A clock domain is logic governed by a particular clock. A reset domain is logic governed by a reset scheme. A design can contain multiple clock and reset domains. |
| **CDC / RDC** | Clock Domain Crossing and Reset Domain Crossing analysis checks signals crossing between domains with different clocks or reset behavior. Synchronizers and reset sequencing help address specific risks; tools and design rules matter. |
| **STA / timing constraint / SDC** | Static Timing Analysis checks timing paths against constraints without simulating every input sequence. A timing constraint describes clocks and path requirements. Synopsys Design Constraints (SDC) is a widely used constraint format; tool dialects may differ. |
| **Setup time / hold time** | Setup time is the minimum time data must be stable before a sampling edge; hold time is the minimum time it must remain stable after that edge. Violations can lead to incorrect sampling or metastability risk. |
| **Clock gating / power gating** | Clock gating stops clock activity to reduce dynamic switching in a block. Power gating disconnects a power domain from its supply, reducing leakage while requiring state and isolation handling. |
| **Power domain / UPF** | A power domain groups logic controlled by a power strategy. Unified Power Format (UPF) describes power intent, such as domains, isolation, and retention; supported syntax depends on standard/tool version. |
| **Retention / isolation / reset sequencing** | Retention preserves selected state across a power transition. Isolation prevents invalid signals from a powered-down domain from affecting active logic. Reset sequencing orders reset assertion and release across components. |
| **Low-power verification** | Checks that power-state transitions, isolation, retention, clock control, reset, and functional behavior meet the specified power intent. |

### Domain-Specific Meanings and PCI Express

| Term | Quick explanation |
|---|---|
| **IP** | Internet Protocol, which routes packets between network addresses. | Intellectual Property (IP) core: a reusable design block intended for integration into a chip or system. Access and licensing vary by provider. |
| **Endpoint** | A reachable API operation, socket address, or service boundary. | In PCI Express, an Endpoint is a device/function at the edge of a PCIe hierarchy; it is distinct from a Root Complex. |
| **Driver** | Software that controls a device or offers a driver API. | In a testbench, code that drives design inputs or protocol transactions. In hardware, a signal driver is circuitry that drives a net. |
| **Agent** | A background or autonomous software participant. | A UVM verification component that usually groups stimulus and observation components. |
| **Bridge** | A component that adapts or connects two interfaces. | A hardware interconnect component that forwards or translates transactions between protocols or buses. |
| **Interface** | A software API or contract. | A set of signals and protocol rules between hardware blocks; SystemVerilog also has an `interface` construct. |

### Foreign-Language and Simulator Interfaces

| Term | Quick explanation |
|---|---|
| **DPI / DPI-C / SystemVerilog DPI** | The SystemVerilog Direct Programming Interface (SystemVerilog DPI) connects SystemVerilog code with foreign-language routines, especially C. DPI-C is the C-facing subset/convention. It specifies import/export declarations, data types, and call direction. |
| **VPI / PLI / FLI / VHPI** | The Verilog Procedural Interface (VPI) and earlier Programming Language Interface (PLI) are Verilog simulator interfaces; the Foreign Language Interface (FLI) and VHDL Procedural Interface (VHPI) belong to other language/tool contexts. They expose simulator objects or behavior differently; check simulator and standard versions. |
| **TLM** | Transaction-Level Modeling describes communication using transactions rather than individual signal transitions, often to model systems at a higher abstraction. |
| **FFI / C API / C ABI** | A Foreign Function Interface lets one language call another. A C API is a source-level interface. A C ABI is the binary calling/data convention used by compiled C-compatible components. |
| **Shared library / dynamic loading / symbol resolution** | A shared library is loaded separately from a program. Dynamic loading requests a library while execution is underway. Symbol resolution finds the implementation for a named function or object. |
| **Linker flags / include path / compiler flags / simulator flags** | Flags modify tool behavior. Include paths locate headers; compiler flags affect translation; linker flags affect library and symbol handling; simulator flags configure a simulation run. Exact syntax is tool-specific. |
| **Calling convention / data-type mapping / pointer conversion** | A calling convention defines how arguments and results cross a binary call boundary. Data-type mapping translates representations between languages. Pointer conversion must respect ownership, size, lifetime, and simulator rules. |
| **Callback / host / target** | A callback lets one side invoke a function provided by another. The host is the controlling or development environment; the target is the device or system being built or tested. These terms depend on context. |

### Hardware and Software Boundary

| Term | Quick explanation |
|---|---|
| **Firmware / driver API / driver** | Firmware is software stored or executed in a device or platform. A driver is software that controls a device through OS or runtime interfaces. A driver API is the boundary offered to its caller. |
| **MMIO / DMA / interrupt** | Memory-Mapped I/O exposes device registers at addresses. Direct Memory Access lets a device transfer data to/from memory after software setup and platform-specific mapping/synchronization. An interrupt notifies a processor of an event. |
| **Bus transaction / protocol adapter / hardware abstraction layer** | A bus transaction is one protocol-defined operation. A protocol adapter translates or bridges one protocol/interface to another. A Hardware Abstraction Layer (HAL) presents a software-facing interface that hides some device details. |
| **C API / C ABI / pointer conversion** | A C API can be stable at source level while a changed data layout or calling convention breaks binary compatibility. Cross-language code needs explicit, compatible representations and ownership rules. |

## Computer architecture and memory

Computer architecture describes how processors, memory, and devices work together. A useful mental model is a layered storage system: small nearby storage is fast and limited, while larger storage is farther away and slower.

### Processor and Memory Components

| Term | Quick explanation |
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

### Coherence and Ordering

| Term | Quick explanation |
|---|---|
| **Cache coherence** | Rules and mechanisms that help multiple cached copies of a memory location behave consistently, especially for writes to that location. |
| **Cache consistency** | An informal term often used for whether cached values appear up to date. In architecture discussions, distinguish coherence for one location from memory consistency/order across operations. |
| **MESI** | A family of cache-coherence state names: Modified, Exclusive, Shared, and Invalid. Protocol details and extensions vary. |
| **Snooping / directory-based coherence** | Snooping has caches observe shared transactions to track copies. A directory records which agents may hold copies and coordinates requests. These are broad coordination approaches. |
| **Memory ordering / memory barrier / acquire / release** | Memory ordering defines which reads and writes may be observed before others. A memory barrier constrains ordering. Acquire and release operations establish ordering relationships around synchronization, as defined by the programming language and architecture. |
| **Atomic operation** | An operation that appears indivisible to specified observers. Atomicity alone does not describe all ordering guarantees. |

### Devices and Interconnect

| Term | Quick explanation |
|---|---|
| **DMA** | Direct Memory Access lets a device transfer data to/from memory under a platform's mapping, coherency, and ownership rules. Software usually configures and completes the transfer. |
| **Interrupt / MMIO** | An interrupt signals an event to a processor. Memory-Mapped I/O accesses device registers through address-mapped operations; use the platform's required accessors and ordering. |
| **Interconnect / bus / crossbar / NoC** | An interconnect connects components. A bus is a shared or protocol-defined communication path. A crossbar permits selected simultaneous paths between multiple inputs and outputs. A Network-on-Chip (NoC) routes traffic among on-chip components. |
| **AXI / ACE / CHI** | Arm AMBA protocols: AXI (Advanced eXtensible Interface) is an interface protocol; ACE (AXI Coherency Extensions) extends AXI with coherency-related capabilities; CHI (Coherent Hub Interface) is a coherent interconnect protocol. Exact features depend on specification revision. |

## Security and reliability

Security controls reduce risks to systems and information. Reliability concerns correct service over time. The same design choices—clear boundaries, bounded work, good failure handling—can help both, but the goals are not identical.

### Identity and Access

| Term | Quick explanation |
|---|---|
| **Authentication / authorization / identity** | Authentication establishes which person, service, or device is acting. Authorization decides which actions that identity may perform. An identity is the subject being recognized. |
| **Privilege / least privilege / permission** | Privilege is the authority available to a subject. Least privilege grants only the access needed for a task. A permission is a specific allowed or denied action on a resource. |
| **Credential / secret / API token** | A credential proves or conveys identity or access. A secret is sensitive data such as a password or private key. An Application Programming Interface (API) token is a credential presented to an API. Store, scope, and rotate them carefully. |
| **Audit log** | A record of security-relevant actions, such as access grants or configuration changes. Protect it from unauthorized changes and avoid recording raw secrets. |

### Cryptography and Threats

| Term | Quick explanation |
|---|---|
| **Encryption / hashing / encoding** | Encryption transforms data using a key so authorized parties can recover it. Hashing maps data to a digest and is generally designed to be one-way. Encoding changes representation and is not secrecy. |
| **Digital signature / public key / private key** | A digital signature lets a verifier check that data was signed by a holder of a private key and was not altered. A public key can be shared; its matching private key must be protected. Exact properties depend on the scheme. |
| **Certificate / TLS** | A certificate binds identity information to a public key under a trust system. Transport Layer Security (TLS) protects a channel and uses certificates in common server-authenticated deployments; certificate validation must be performed correctly. |
| **Vulnerability / threat model / attack surface** | A vulnerability is a weakness that could be exploited. A threat model identifies assets, actors, trust boundaries, and likely threats. Attack surface is the set of reachable interfaces and conditions an attacker might target. |
| **Input validation / sanitization** | Validation checks input against expected rules. Sanitization transforms input for a specific safe use. Neither should be confused with output encoding or parameterized APIs; use defenses appropriate to the context. |
| **Sandbox / isolation / fault containment** | A sandbox restricts what code can access. Isolation separates components or privileges. Fault containment limits how far a failure can spread. These properties depend on implementation and configuration. |

### Security Properties and Recovery

| Term | Quick explanation |
|---|---|
| **Confidentiality / integrity / availability** | Confidentiality limits disclosure to authorized parties. Integrity protects against unauthorized change. Availability keeps a service accessible when needed. Together they are often called the confidentiality, integrity, and availability (CIA) triad. |
| **Backup / recovery** | A backup is a recoverable copy of data or configuration. Recovery restores service or data after loss; a backup is useful only if it can be restored and meets the recovery objective. |
| **Idempotency / timeout / retry / rate limiting** | Idempotency makes repeated intended operations safe under defined conditions. A timeout bounds waiting. A retry repeats selected work. Rate limiting controls request frequency. These controls limit resource use and duplicate effects. |

## Tools and environments

A toolchain is the collection of programs used to edit, build, test, debug, and run software. A development environment is the configured workspace in which those tools and dependencies are available.

### Common terms

| Term | Quick explanation |
|---|---|
| **IDE / editor** | An Integrated Development Environment combines editing with features such as navigation, building, and debugging. An editor focuses on changing text and may gain features through extensions. |
| **Terminal / shell** | A terminal is a text interface; a shell interprets commands, expands variables, and runs scripts. They are related but not the same thing. |
| **Debugger / debugger adapter** | A debugger controls execution and inspects state. A debugger adapter connects an editor or IDE's debugging UI to a specific debugger backend. |
| **Compiler / interpreter / simulator** | A compiler translates programs, an interpreter executes code or an intermediate form, and a simulator models a system's behavior. Their roles can be combined in a toolchain. |
| **Linter / formatter** | A linter checks code for selected style issues or likely mistakes. A formatter rewrites code into a consistent layout. Neither proves correctness. |
| **Package manager / virtual environment** | A package manager obtains and tracks reusable software. A virtual environment isolates project-specific dependencies or execution context; its exact meaning depends on the language or tool. |
| **Notebook** | An interactive document combining executable cells, results, and explanatory text, often used for exploration and teaching. |
| **Build tool / task runner** | A build tool determines and runs steps that produce outputs. A task runner invokes named tasks, which may or may not form a dependency-aware build. |
| **Language server** | A background tool that provides language-aware editor features such as completion, diagnostics, and navigation. |
| **Extension / plugin** | Optional functionality loaded into a host editor, IDE, or application. The host defines its extension model and permissions. |
| **Configuration / workspace / environment** | Configuration changes tool behavior. A workspace is the project or set of files opened in a tool. An environment is the available runtime, variables, dependencies, and settings. |
| **Command / script / CLI flag / command-line argument** | A command invokes a program or shell operation. A script is a file of instructions. A CLI flag is an option; a command-line argument supplies a value or operand. |
| **Executable path / PATH** | An executable path identifies a program file. `PATH` is an environment variable listing directories that a shell or OS search mechanism may use to find commands; rules differ by platform. |
| **Toolchain** | The coordinated set of tools that transforms source or specifications into a tested or deployable result, such as compiler, linker, simulator, and scripts. |

---

Use the contents links to jump by subject, or use your browser's Find command to locate a term anywhere on this page.
