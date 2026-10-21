# Networking and Distributed Systems

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

A distributed system has parts that communicate across process or machine boundaries. The network can delay, lose, duplicate, reorder, or reject work, so a design must describe how it detects and handles failure.

## Communication Basics

| Term | Meaning and use |
|---|---|
| **Client-server architecture** | Components take requester and provider roles for an exchange. Those are roles, not permanent types of machine. |
| **Peer-to-peer (P2P)** | Participants communicate as peers and may both provide and request resources. |
| **Connection-oriented / connectionless** | Connection-oriented communication maintains connection state and may provide delivery guarantees. Connectionless communication sends independent messages without establishing that state. |
| **Packet / frame / segment / datagram** | A frame is a link-layer unit; an Internet Protocol (IP) packet carries network-layer data; a Transmission Control Protocol (TCP) segment carries TCP data; a User Datagram Protocol (UDP) datagram carries UDP data. Exact encapsulation varies. |
| **DNS resolution** | A resolver queries the Domain Name System (DNS) to obtain records for a name, such as an address. Cached results may be reused until their time-to-live policy expires. |
| **TCP handshake / TLS handshake** | A TCP handshake establishes transport state. A Transport Layer Security (TLS) handshake negotiates a secure session and authenticates the server (and optionally the client); it is a separate protocol exchange. |
| **Routing / switching** | Routing selects a path between IP networks. Switching forwards frames within a local network using link-layer information. |
| **Firewall / NAT** | A firewall applies traffic rules. Network Address Translation (NAT) rewrites address information between network domains, often to share addresses; it is not itself a security policy. |

## Intermediaries and Service Patterns

| Term | Meaning and use |
|---|---|
| **Load balancer** | Distributes requests or connections across multiple targets according to a policy and health information. |
| **Reverse proxy** | Accepts traffic for backend services and forwards it, often handling TLS, routing, caching, or request limits. |
| **Service discovery** | Finds the current address or identity of a service instance, which may move or scale over time. |
| **Message queue / message broker / event bus** | A queue stores messages for consumers to process; a message broker mediates message exchange; an event bus distributes event notifications among producers and subscribers. |
| **Publish-subscribe (pub/sub)** | Publishers emit messages under a topic or channel; subscribers receive messages for topics they follow. Delivery, ordering, and durability depend on the system. |
| **Synchronous / asynchronous communication** | Synchronous callers wait for a result as part of the interaction. Asynchronous communication lets work proceed and returns results later or through another channel. |
| **Polling / streaming** | Polling asks repeatedly whether new data is available. Streaming delivers a continuing sequence of data or events over time. |
| **Heartbeat / health check** | A heartbeat signals that a component is still communicating. A health check asks whether a service meets a specific readiness or liveness condition. Neither proves every operation works. |

## Failures and Distributed Behavior

| Term | Meaning and use |
|---|---|
| **Circuit breaker** | A client-side pattern that stops repeatedly calling a failing dependency for a period, then permits a limited recovery check. |
| **Retry policy / exponential backoff** | A retry policy selects which failures to retry and how many times. Exponential backoff increases the wait between attempts, often with jitter to avoid synchronized retries. |
| **Eventual consistency** | Replicas may temporarily disagree but are expected to converge if updates stop and communication resumes. It does not mean every read is immediately current. |
| **Replication / failover** | Replication keeps copies of data or service state. Failover moves work to a backup after a failure; safe failover depends on state and coordination. |
| **Fault tolerance** | A system continues to provide defined behavior despite selected faults. It is bounded by the faults the design anticipates. |
| **Distributed tracing** | A trace links timed operations across services to help explain one request's path. Traces complement logs and metrics. |

### Example: a request crossing services

A browser resolves a service name through DNS, establishes a transport connection, and sends an application request. A reverse proxy routes it to a healthy service. If a dependency is temporarily unavailable, a bounded retry policy may help; unlimited retries can worsen the outage.

**Common confusion:** A timeout means the caller did not receive a result in time; it does not prove the server failed to perform the operation. A retry can therefore duplicate work unless the operation is idempotent or deduplicated.

**References:** [RFC 1034 DNS concepts](https://www.rfc-editor.org/rfc/rfc1034.html); [RFC 9293 TCP](https://www.rfc-editor.org/rfc/rfc9293.html); [RFC 768 UDP](https://www.rfc-editor.org/rfc/rfc768); [RFC 8446 TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446.html); [Python networking and IPC](https://docs.python.org/3/library/ipc.html).
