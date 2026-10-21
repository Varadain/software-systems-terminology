# Software and Systems Terminology Field Guide

A beginner-friendly reference for the words used in software development, operating systems, networking, hardware verification, and software/hardware integration. It is a set of learning notes, not a course that requires an application or toolchain.

> **How to use this guide:** Start with the roadmap, follow links by topic, and use the alphabetical index when you meet an unfamiliar term. Each page gives a concise definition and practical context; comparisons explain terms that are easy to mix up.

## Start Here

- [Learning roadmap](docs/learning-roadmap.md) — a flexible 12-stage reading path.
- [Topic index](docs/index.md) — browse all subject areas.
- [Glossary index](docs/reference/glossary-index.md) — find a term by name or category.
- [Quick reference](docs/reference/quick-reference.md) — short reminders for revision.
- [Flashcards and interview questions](docs/reference/flashcards.md) — check understanding.
- [Concept map](docs/reference/concept-maps.md) — see how the areas connect.
- [Algorithms and examples](examples/algorithms.md) — follow request, retry, queue, test, and CI flows.
- [Everyday and engineering scenarios](examples/everyday-scenarios.md) — see browser, banking, shopping, mobile, Linux, Python, CI, and hardware examples.
- [SVG visual gallery](docs/reference/visual-gallery.md) — review all 27 accessible diagrams by topic.

## Topic Areas

| Area | What it covers |
|---|---|
| [Software architecture](docs/topics/fundamentals/software-architecture.md) | Components, interfaces, services, and design vocabulary |
| [APIs and communication](docs/topics/apis-and-communication/apis-and-communication.md) | API styles, HTTP, data exchange, identity, and compatibility |
| [Networking](docs/topics/networking/networking-and-distributed-systems.md) | DNS, transport, intermediaries, messaging, and failure handling |
| [Programming and compilation](docs/topics/programming-and-compilation/programming-and-execution.md) | Source-to-executable flow, memory, concurrency, and language tools |
| [Operating systems](docs/topics/operating-systems/operating-systems-and-linux.md) | Processes, Linux interfaces, memory, and synchronization |
| [Data and automation](docs/topics/data-and-automation/data-configuration-and-automation.md) | Formats, configuration, logs, and scripts |
| [Git and DevOps](docs/topics/git-and-devops/git-and-devops.md) | Version control, CI/CD, containers, and deployment |
| [Testing and debugging](docs/topics/testing-and-debugging/testing-debugging-and-reliability.md) | Test levels, verification, diagnosis, and reliability |
| [Hardware and verification](docs/topics/hardware-and-verification/hardware-and-verification.md) | RTL, UVM, simulation, timing, and C/SystemVerilog integration |
| [Computer architecture](docs/topics/computer-architecture/computer-architecture-and-memory.md) | Caches, memory systems, interconnects, and ordering |
| [Security and reliability](docs/topics/security-and-reliability/security-and-reliability.md) | Identity, cryptography, secure design, and recovery |
| [Tools and environments](docs/topics/tools-and-environments/tools-and-environments.md) | Editors, shells, debuggers, build tools, and toolchains |
| [Common comparisons](docs/comparisons/index.md) | Side-by-side explanations of commonly confused concepts |

## Repository Layout

- [Topic guides](docs/topics/) are grouped by subject.
- [Comparisons](docs/comparisons/) explain commonly confused terms side by side.
- [Reference and revision](docs/reference/) contains the glossary, roadmap, flashcards, concept maps, quick reference, and SVG gallery.
- [Examples](examples/) show practical software and engineering scenarios.
- [SVG teaching diagrams](assets/images/) are collected in the linked visual gallery.

## Scope and Sources

The notes favor clear intuition over exhaustive implementation detail. Examples are illustrative unless explicitly labeled otherwise. Standards and tool behavior can vary by version; see [SOURCES.md](SOURCES.md) and the references on each topic page.

These notes are maintained as a Markdown-first field guide. See [Contributing](CONTRIBUTING.md) for writing guidance and [Sources](SOURCES.md) for the references behind the topics.

## Local Preview

No application or documentation server is required. Open `README.md` in Visual Studio Code 1.121 or later and press **Ctrl+Shift+V** to preview the Markdown; use the links to navigate the notes. The built-in preview renders Mermaid code blocks. See the [VS Code Markdown preview documentation](https://code.visualstudio.com/docs/languages/markdown) for preview controls and Mermaid support.
