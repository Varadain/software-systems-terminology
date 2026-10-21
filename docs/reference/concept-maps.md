# Concept Maps

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Roadmap](../learning-roadmap.md)

![A client sends a request through an API and network to a server, then receives a response.](../../assets/images/request-flow.svg)

## Software Request Path

```mermaid
flowchart LR
  U[User or client] -->|starts request| A[API boundary]
  A -->|uses rules| P[Protocol: HTTP or RPC]
  P -->|uses names and transport| N[Network]
  N -->|routes traffic| G[Proxy or gateway]
  G -->|forwards request| S[Server or service]
  S -->|reads or updates| D[Data store or device]
  S -->|creates result| R[Response and status]
  R -->|returns to caller| U
```

This path shows how a caller's request crosses an interface and protocol, may pass through an intermediary, and reaches a service that returns a result.

## From Code to Execution

```mermaid
flowchart LR
  Src[Source code] -->|translates or interprets| Front[Compiler or interpreter]
  Front -->|emits| Obj[Object code or bytecode]
  Obj -->|links or loads| Link[Linker or runtime loader]
  Link -->|starts| Run[Process and threads]
  Run -->|requests services from| OS[Operating system]
  OS -->|manages access to| HW[CPU, memory, and devices]
```

This is a simplified route from source text to a running program. Interpreters and runtimes can combine or repeat stages, so not every language creates the same intermediate files.

## Verification Loop

```mermaid
flowchart LR
  Req[Requirement] -->|defines expected behavior| Model[Reference model]
  Req -->|defines scenarios| Stim[Sequence and driver]
  Stim -->|drives inputs| Dut[Design under test]
  Dut -->|produces signals| Mon[Monitor]
  Mon -->|observed values| Check[Scoreboard]
  Model -->|expected values| Check
  Dut -->|is checked over time| Assert[Assertions]
  Dut -->|records exercised cases| Cov[Coverage]
  Check -->|reports pass or mismatch| Result[Regression results]
  Assert -->|reports property results| Result
  Cov -->|reports scenario totals| Result
```

Requirements guide both the scenarios and expected behavior. The monitor observes the design, the scoreboard compares actual and expected values, assertions check properties, and coverage records what was exercised.

## API Request Sequence

```mermaid
sequenceDiagram
  participant C as Client
  participant G as API Gateway
  participant S as Service
  participant D as Data Store
  C->>G: Send request
  G->>S: Validate and route
  S->>D: Read requested record
  D-->>S: Return record
  S-->>G: Build response
  G-->>C: Return status and body
```

The sequence makes the order explicit: the client waits for the gateway, service, and data store to finish their part before it receives the response.

## Request Retry States

```mermaid
stateDiagram-v2
  [*] --> Created
  Created --> Sent: send request
  Sent --> Processing: accepted
  Sent --> TimedOut: deadline exceeded
  Processing --> Succeeded: response received
  Processing --> Failed: permanent error
  TimedOut --> Retrying: attempts remain
  Retrying --> Sent: backoff elapsed
  TimedOut --> Failed: retry limit reached
  Succeeded --> [*]
  Failed --> [*]
```

The request succeeds, fails, or times out. A timeout can enter a bounded retry path; only retry operations that are safe to repeat, or protect them with idempotency or deduplication.

These diagrams are simplified: real systems may use several protocols, components, tool stages, clocks, and verification mechanisms. They are orientation aids, not implementation diagrams.
