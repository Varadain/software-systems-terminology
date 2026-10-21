# Everyday and Engineering Scenarios

**Navigation:** [Home](../README.md) | [Topic Index](../docs/index.md) | [Roadmap](../docs/learning-roadmap.md)

These are illustrative flows, not claims about a specific company, product, or implementation.

## Browser Opens a Page

The browser acts as a client. It resolves a domain name, establishes a secure connection, sends an HTTP request, and interprets the response. HTML, images, scripts, and API data may require additional requests. Browser developer tools can show requests, status codes, and timing.

## Banking Transfer

A mobile banking app sends a transfer request over a protected connection. The service authenticates the account, checks authorization and input, records the operation, and returns a result. A client retry after a timeout can duplicate a transfer unless the API makes retries safe, for example through an idempotency key and server-side deduplication. This is a simplified design example.

## Online Shopping

A shopping app requests cart and product information from services. A checkout request may lead to order processing, payment work, and shipping notifications. A message queue can decouple order acceptance from later tasks, but the system must define what happens if a consumer fails or processes a message twice.

## Mobile App Session

A mobile application can call a versioned API and receive structured data. Authentication credentials should be stored and transmitted according to the platform's security model. A session or token identifies access state; it is not the same thing as authorization policy.

## Linux Command Pipeline

On a Linux shell, this illustrative command selects error lines from a log and sorts them:

```sh
grep "ERROR" app.log | sort
```

The pipe connects `grep` output to `sort` input. The command's exit status and stderr are separate from its ordinary output.

## Python Data Script

```python
import json

record = json.loads('{"run_id": 105, "status": "PASS"}')
print(record["status"])
```

The parser converts JSON text into Python values. Parsing success does not prove that the value meets an application's schema; validate required keys and ranges separately.

## CI Pipeline

A change triggers a workflow that checks out a commit, installs declared dependencies, runs a build and tests, and stores an artifact if checks pass. A CI result helps reviewers; it does not guarantee that production behavior is correct or that deployment occurred.

## Test Automation and RTL Simulation

A verification sequence can request a register read, a bus-functional model can drive the transaction, and a monitor can observe it. A scoreboard compares the observed response with a reference model. A simulator records clocked signal changes in a waveform and evaluates assertions. This is a functional model; it does not by itself prove physical timing closure.

## Hardware Interface and PCIe Example

Firmware or a driver may configure a device using memory-mapped registers, provide buffers for DMA, and handle completion interrupts. In a PCI Express (PCIe) system, a Root Complex connects the host side to the hierarchy and an Endpoint represents a device function. Protocol and silicon details depend on the PCI-SIG specification revision and implementation.

**Related reading:** [APIs](../docs/topics/apis-and-communication/apis-and-communication.md), [Linux and operating systems](../docs/topics/operating-systems/operating-systems-and-linux.md), [hardware verification](../docs/topics/hardware-and-verification/hardware-and-verification.md), and [algorithms](algorithms.md).
