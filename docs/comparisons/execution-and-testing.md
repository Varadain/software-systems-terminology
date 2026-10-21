# Execution and Testing: Common Comparisons

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Comparisons](index.md)

## Process and Thread

A process is a running program instance with an address space and OS-managed resources. A thread is an execution path inside a process; threads generally share that process's memory while keeping their own execution state. Use processes for stronger isolation or separate address spaces; threads can share data more directly but require coordination.

## Concurrency and Parallelism

Concurrency means multiple tasks can make progress during overlapping periods. Parallelism means tasks execute at the same time on separate execution resources. A single CPU core can interleave concurrent tasks without running them in parallel.

## Unit, Integration, and System Tests

| Test level | Main boundary | Example |
|---|---|---|
| Unit | One small function, class, or module. | Check a parser on a known input. |
| Integration | Two or more connected components. | Verify a service stores and reads a result. |
| System | The assembled system against requirements. | Verify a test platform reports a completed run. |

An end-to-end test follows a user-facing journey through real boundaries. A smoke test is a small check that a build or service is basically usable. A regression test detects previously fixed behavior breaking again. These are dimensions of test scope and purpose, not mutually exclusive test levels.

## Mock, Stub, and Fake

All are test doubles: substitutes for dependencies used by a test.

| Double | Typical role | Example |
|---|---|---|
| Stub | Returns prepared data. | A fake response from a weather API. |
| Mock | Records or verifies expected calls/interactions. | Check a payment client was called once. |
| Fake | Working but simplified implementation. | An in-memory store in place of a database. |

Testing communities sometimes use *mock* broadly for any substitute. Describe what the test double actually does.

## Error, Exception, and Fault

An error is a broad failure or incorrect condition. An exception is a language/runtime mechanism that reports and may propagate an unusual condition. A fault is an underlying defect or abnormal condition that can cause an error or failure. Some domains define these terms more precisely; hardware fault models are not identical to programming-language exceptions.

## Monitoring and Observability

Monitoring watches chosen signals and thresholds for known conditions, such as error rate exceeding a limit. Observability is the ability to investigate system behavior using outputs such as logs, metrics, and traces, including cases not anticipated when alerts were written. Observability needs useful instrumentation; a dashboard alone does not provide it.
