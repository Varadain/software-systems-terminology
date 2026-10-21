# APIs and Communication

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

An API defines how a caller asks for an operation or data. A protocol defines rules for exchanging messages. A data format defines how the message content is represented. These layers often work together but are not interchangeable.

## API Styles and Web Protocols

| Term | Meaning and use |
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

## Message Parts and Exchange

| Term | Meaning and use |
|---|---|
| **Request / response** | A request communicates what a client asks for; a response reports an outcome and may include data. |
| **Header / body / payload** | Headers carry message metadata; a body carries content. Payload means the data of interest, often the body but sometimes a part of it. |
| **Status code / route / routing** | An HTTP status code summarizes the response outcome. A route maps an address and method to a handler. Routing chooses where a message should go. |
| **Serialization / deserialization** | Serialization turns in-memory data into a transferable or storable representation. Deserialization reconstructs a usable value from that representation. |
| **JSON / XML / Protocol Buffers / schema** | JSON and XML are text-based data formats; Protocol Buffers is a schema-based binary serialization system. A schema describes fields, types, and constraints. |
| **Authentication / authorization** | Authentication establishes an identity; authorization decides what it may do. See [the security page](../security-and-reliability/security-and-reliability.md). |
| **API key / bearer token / session / cookie** | An API key identifies a client or application. A bearer token grants access to whoever possesses it. A session stores state about an interaction; a cookie is browser-managed data often used to carry a session identifier. Protect all secrets and credentials. |
| **CORS** | Cross-Origin Resource Sharing is a browser security mechanism that lets a server state which cross-origin browser requests it permits. It is not a general server-to-server access-control system. |
| **Timeout / retry / rate limiting** | A timeout bounds how long a caller waits. A retry repeats an operation after selected failures. Rate limiting restricts request frequency. Retries should be bounded and safe for the operation. |
| **Idempotency** | Repeating an operation has the same intended effect as doing it once. HTTP defines method semantics, but an application may need an idempotency key for safe retry of a create/payment operation. |
| **Pagination / versioning / backward compatibility** | Pagination splits a large result into manageable portions. Versioning identifies an API or data-contract revision. Backward compatibility means newer changes continue to support defined older uses. |

### A simple request flow

1. A client builds a request for a specific endpoint.
2. It sends the request using an agreed protocol and data format.
3. The receiver validates identity, authorization, and input as appropriate.
4. The receiver returns a status and optional result or error.

Illustrative pseudocode:

```text
response = send(GET, "/runs/105")
if response.status is successful:
    show(parse_json(response.body).status)
else:
    report(response.status)
```

**Analogy:** An API is like a menu with ordering rules; HTTP is one possible delivery process; JSON is a way to write the order and result. The analogy does not define the actual protocol.

**References:** [RFC 9110](https://www.rfc-editor.org/rfc/rfc9110.html); [RFC 9114 HTTP/3](https://www.rfc-editor.org/rfc/rfc9114.html); [MDN HTTP overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview); [MDN Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API); [MDN REST glossary](https://developer.mozilla.org/en-US/docs/Glossary/REST); [MDN CORS guide](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS); [gRPC core concepts](https://grpc.io/docs/what-is-grpc/core-concepts/); [Protocol Buffers guides](https://protobuf.dev/programming-guides/); [RFC 8446 TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446.html); [RFC 9000 QUIC](https://www.rfc-editor.org/rfc/rfc9000.html).
