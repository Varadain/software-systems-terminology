# Development Tools and Environments

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

A toolchain is the collection of programs used to edit, build, test, debug, and run software. A development environment is the configured workspace in which those tools and dependencies are available.

| Term | Meaning and use |
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

**Practical check:** When a command is “not found,” confirm the program is installed, the expected environment is active, and its directory is included in the correct `PATH`. When a build differs between machines, compare tool versions, environment variables, and dependency versions.

**References:** [Python modules and packages](https://docs.python.org/3/tutorial/modules.html); [GNU Binutils](https://www.gnu.org/software/binutils/); [GitHub Actions workflows](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows).
