# Source Map

**Navigation:** [Home](README.md) | [Topic Index](docs/index.md)

These primary or authoritative pages were checked while preparing the notes. They are starting points, not substitutes for topic-level references. Standards can be versioned, amended, or superseded; check the linked status page before relying on a particular revision.

## Web, APIs, and Internet Protocols

- [HTTP overview — MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview) — client/server exchange and HTTP messages.
- [HTTP reference — MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference) — methods, headers, and status codes.
- [Fetch API — MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) — a browser API for network requests.
- [RFC 9110: HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html) — IETF HTTP terminology and shared semantics.
- [RFC 9114: HTTP/3](https://www.rfc-editor.org/rfc/rfc9114.html) — HTTP semantics mapped over QUIC.
- [RFC 9293: Transmission Control Protocol](https://www.rfc-editor.org/rfc/rfc9293.html) — TCP specification.
- [RFC 768: User Datagram Protocol](https://www.rfc-editor.org/rfc/rfc768) — UDP specification; updated by later RFCs for specific transport options.
- [RFC 1034: Domain Names — Concepts and Facilities](https://www.rfc-editor.org/rfc/rfc1034.html) and [RFC 1035: Implementation and Specification](https://www.rfc-editor.org/rfc/rfc1035.html) — DNS architecture and wire formats.
- [RFC 8446: TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446.html) — secure transport protocol.
- [RFC 9000: QUIC](https://www.rfc-editor.org/rfc/rfc9000.html) — secure, multiplexed transport over UDP; relevant to HTTP/3.
- [MDN REST glossary](https://developer.mozilla.org/en-US/docs/Glossary/REST) and [CORS guide](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS) — web API style and browser cross-origin behavior.
- [gRPC core concepts](https://grpc.io/docs/what-is-grpc/core-concepts/) — RPC service definitions and lifecycle.
- [Protocol Buffers programming guides](https://protobuf.dev/programming-guides/) — schema and serialization documentation.
- [RFC 8259: JSON](https://www.rfc-editor.org/info/rfc8259/) — JSON syntax and interoperability guidance.
- [W3C XML 1.0](https://www.w3.org/TR/xml/) — Extensible Markup Language specification.
- [YAML 1.2.2](https://yaml.org/spec/1.2.2/) — current YAML specification revision listed by the YAML project.

## Programming, Git, Linux, and CI

- [Python tutorial: Modules](https://docs.python.org/3/tutorial/modules.html) — modules, imports, and packages.
- [Python asyncio](https://docs.python.org/3/library/asyncio.html) and [concurrent execution](https://docs.python.org/3/library/concurrency.html) — asynchronous tasks, threads, and processes. Examples should be checked against the Python version in use.
- [Python networking and IPC](https://docs.python.org/3/library/ipc.html) — sockets and interprocess communication.
- [Python socket module](https://docs.python.org/3/library/socket.html) — low-level socket interface; platform-specific behavior is called out in the docs.
- [Python `unittest`](https://docs.python.org/3/library/unittest.html) and [`json`](https://docs.python.org/3.11/library/json.html) modules — standard testing and JSON parsing libraries.
- [Pro Git](https://git-scm.com/book/en/v2) — Git fundamentals, branching, and remotes.
- [Git branch documentation](https://git-scm.com/docs/git-branch) — branch operations.
- [GitHub Docs: Continuous integration](https://docs.github.com/en/actions/get-started/continuous-integration) and [Workflows](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows) — GitHub Actions terminology.
- [Linux man-pages: pthreads(7)](https://man7.org/linux/man-pages/man7/pthreads.7.html) — POSIX thread model.
- [Linux man-pages: mmap(2)](https://man7.org/linux/man-pages/man2/munmap.2.html) — virtual-memory mapping interface.
- [Linux kernel: Driver API](https://docs.kernel.org/driver-api/index.html) and [memory management](https://www.kernel.org/doc/html/latest/admin-guide/mm/index.html) — kernel interfaces and Linux implementation context.
- [GNU Binutils](https://www.gnu.org/software/binutils/) — assembler, linker, ELF tools, and symbols.

## Hardware, Verification, and Security

- [Accellera UVM community](https://www.accellera.org/community/uvm) — Universal Verification Methodology and its reference implementation; UVM revisions differ.
- [IEEE 1800-2023 SystemVerilog standard](https://ieeexplore.ieee.org/document/10458102) — language syntax and semantics; full standard access may require purchase or institutional access.
- [IEEE 1364-2005 Verilog standard](https://ieeexplore.ieee.org/document/1620780) — includes legacy PLI/VPI material; this standalone revision is superseded by IEEE 1800.
- [IEEE SA: IEEE 1076-2019](https://standards.ieee.org/ieee/1076/5179/) — official status page for the active VHDL language reference manual; full text is available by purchase or subscription.
- [Arm AMBA AXI/ACE specification, Issue L](https://developer.arm.com/documentation/ihi0022/l/) — Arm's version list marked Issue L as latest when checked; the full document page redirected but did not render in this review session.
- [PCI-SIG: PCI Express Basics & Background](https://pcisig.com/developer/education/pci-express-basics-background-17) — introductory session overview; its download link points to a member resource.
- [PCI-SIG specifications](https://pcisig.com/specifications) — PCI Express standards portal; members can access the online library, while non-members may purchase specifications. Availability depends on the document/revision.
- [NIST cybersecurity glossary](https://csrc.nist.gov/glossary) — security terms in the context of their source publications.
- [TLS 1.3 RFC 8446](https://www.rfc-editor.org/rfc/rfc8446.html) — certificate and secure-channel context.
- [OpenTelemetry observability primer](https://opentelemetry.io/docs/concepts/observability-primer/) — logs, metrics, traces, and service indicators.

## Access Limits

IEEE SA's public IEEE 1076-2019 page confirms the title and active status, but its full standard requires purchase or subscription. An earlier preview URL returned an access error, so no claim here depends on unseen standard clauses. Arm's AXI version list identified Issue L as latest, but its Issue L document page redirected to a page that did not render in this review session; use Arm's page for version selection and confirm tool-specific details directly. The PCI-SIG education overview is public, while the linked presentation download is member-gated; its older indexed PDF URLs returned 404 and are not linked here. Other linked pages were checked through their publishers' documentation or standards portals. This repository links to standards and does not reproduce their text.
