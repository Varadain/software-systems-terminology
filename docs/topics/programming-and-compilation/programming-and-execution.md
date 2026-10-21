# Programming and Execution

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

Programs pass through representations before they run. The precise path depends on the language, compiler, operating system, and runtime.

## From Text to a Running Program

| Term | Meaning and use |
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

## Values, Memory, and Errors

| Term | Meaning and use |
|---|---|
| **Garbage collection / memory allocation** | Allocation reserves memory for values. Garbage collection reclaims some allocated memory when the runtime determines it is no longer reachable; not every language uses garbage collection. |
| **Stack / heap** | Stack commonly holds call frames and local execution state. Heap commonly holds dynamically allocated objects. These are programming concepts; actual memory layout varies. |
| **Pointer / reference / value** | A pointer contains an address. A reference provides a way to access an object, with language-specific rules. A value is the data itself or a value-level representation. |
| **Scope / namespace** | Scope determines where a name can be used. A namespace groups names to avoid accidental conflicts. |
| **Exception / error / warning** | An exception is a language/runtime mechanism for reporting an unusual condition. An error indicates a failure or incorrect state. A warning reports a concern that may not stop execution. |
| **Undefined behavior** | In languages such as C and C++, this describes cases where the language specification places no requirements on the result; code relying on it may behave unpredictably across builds. |
| **Process / thread / coroutine** | A process is an executing program instance; a thread is an execution path within a process; a coroutine is a cooperative unit of work that can suspend and resume. See [process vs thread](../../comparisons/execution-and-testing.md#process-and-thread). |
| **Concurrency / parallelism / asynchronous programming** | Concurrency organizes overlapping work; parallelism executes work simultaneously on multiple resources. Asynchronous programming lets a task suspend while waiting instead of blocking its execution resource. |

### Simplified build flow

```text
source → compiler → object file → linker + libraries → executable → loader → process
```

An interpreted language may instead parse source or bytecode and execute it through a runtime. A JIT compiler may translate frequently used parts while the program runs.

**Example:** A C call to a function in a shared library may compile successfully but fail at runtime if the loader cannot find that library. This separates compile-time, link-time, and load-time problems.

**References:** [Python tutorial: Modules](https://docs.python.org/3/tutorial/modules.html); [GNU Binutils](https://www.gnu.org/software/binutils/); [Python concurrency](https://docs.python.org/3/library/concurrency.html).
