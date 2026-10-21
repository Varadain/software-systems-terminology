# Data, Languages, and Security: Common Comparisons

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Comparisons](index.md)

## JSON, XML, and YAML

| Format | Typical strengths | Example use |
|---|---|---|
| JSON (JavaScript Object Notation) | Small, widely supported, explicit strings, numbers, arrays, objects, booleans, and null. | Web API request/response body. |
| XML (Extensible Markup Language) | Nested elements, attributes, namespaces, and mature schema/tooling ecosystems. | Document formats and systems with XML-based contracts. |
| YAML (YAML Ain't Markup Language) | Human-oriented configuration syntax with indentation and richer scalar conventions. | A configuration or workflow file. |

Each format represents data; none is automatically a protocol or a complete schema. YAML indentation is significant; XML and JSON also have precise syntax rules.

## Compiler, Interpreter, Assembler, and Linker

| Tool | Main job | Simplified example |
|---|---|---|
| Compiler | Translates a source language to another representation. | C source to object code. |
| Interpreter | Executes source or an intermediate representation. | A language runtime evaluating a script. |
| Assembler | Translates assembly into machine-level object code. | `.s` source to an object file. |
| Linker | Combines object files/libraries and resolves references. | Object files plus a library to create an executable. |

Real toolchains can combine stages. A compiler driver may invoke a preprocessor, compiler, assembler, and linker. A language runtime may compile some code just in time.

## Static and Dynamic Linking

Static linking places needed library code into the linked output. Dynamic linking resolves separately stored shared libraries, often when a program loads or runs. Static linking can simplify deployment of those library bytes but may increase output size; dynamic linking can share libraries and updates but adds runtime dependency/version concerns. Actual behavior depends on platform and tool options.

## Authentication and Authorization

Authentication asks **who or what is acting?** Authorization asks **what is that identity allowed to do?** A successful login can authenticate a user while authorization still denies access to an administrator-only setting.

## Encryption, Hashing, and Encoding

| Operation | Reversible with what? | Primary purpose |
|---|---|---|
| Encryption | A suitable key and algorithm. | Confidentiality. |
| Hashing | Normally not reversed; compare or verify a digest. | Integrity checks or other cryptographic constructions. Password storage needs a password-specific hash scheme. |
| Encoding | A decoding rule, not a secret key. | Represent data in a format such as Base64 or UTF-8. |

Encoding is not encryption. A hash is not a substitute for encryption. Digital signatures and message authentication codes add authenticity properties through other constructions; see [security notes](../topics/security-and-reliability/security-and-reliability.md).
