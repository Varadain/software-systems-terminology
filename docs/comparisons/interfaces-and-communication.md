# Interfaces and Communication: Common Comparisons

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Comparisons](index.md)

## API, ABI, and SDK

| Term | What it describes | Example and use |
|---|---|---|
| API (Application Programming Interface) | Operations exposed to software callers. | A Python function or a web endpoint; use it to write code against a service. |
| ABI (Application Binary Interface) | Binary-level compatibility rules between compiled components. | Calling convention and data layout for a shared library; use it when independently built binaries must work together. |
| SDK (Software Development Kit) | A developer kit that may include APIs, libraries, tools, and documentation. | A cloud SDK wraps a service API and helps a developer call it. |

The API is the contract; an ABI is about compiled interoperability; an SDK is the collection of development resources. An SDK may implement or expose APIs, but the terms do not name the same thing.

## REST and RPC

| REST (Representational State Transfer) | RPC (Remote Procedure Call) |
|---|---|
| Resource-oriented architectural style with constraints such as a uniform interface. | Remote operation call model: request a named procedure on another system. |
| Example: retrieve a resource representation with `GET /users/42`. | Example: call `GetUser(id=42)` through an RPC framework. |
| Useful when resource semantics, cache behavior, and broad web interoperability fit the task. | Useful when explicit service methods, generated clients, or streaming fit the task. |

Both can run over HTTP and both need contracts, errors, authentication, and versioning. A JSON endpoint is not automatically REST, and an RPC call may use HTTP as its transport.

## HTTP, TCP, and Sockets

| Term | Layer and role | Example |
|---|---|---|
| HTTP (Hypertext Transfer Protocol) | Application protocol defining request/response semantics. | `GET /status` with an HTTP status code. |
| TCP (Transmission Control Protocol) | Transport protocol providing a reliable, ordered byte stream between endpoints. | An HTTP/1.1 or HTTP/2 connection commonly uses TCP. |
| Socket | Programming interface/endpoint abstraction used to send or receive data. | A program opens a TCP socket, then sends application data. |

HTTP is not a guarantee of TCP use: HTTP/3 uses QUIC over UDP. A socket API is not the network protocol itself.

## API and Protocol

An API defines operations a caller can use. A protocol defines the rules participants follow when communicating. A local library API may involve no network protocol; a network protocol can be implemented through several APIs.

**Example:** A socket API lets a program request network communication. TCP defines transport behavior. HTTP defines application-level message meaning.

## Client and Server

| Client | Server |
|---|---|
| Requests data or work in a particular exchange. | Receives requests and provides a response or service. |
| Example: a browser requesting a page. | Example: a web server answering that request. |

These are roles, not fixed machine types. One service can be a server toward a browser and a client toward a database.

## Endpoint, Port, and URL

| Term | Meaning | Example |
|---|---|---|
| Endpoint | A reachable interaction boundary or address; scope varies by context. | An API route such as `/users/42` or a device interface. |
| Port | A transport-layer number used to direct traffic to a service on a host. | TCP port `443`. |
| URL (Uniform Resource Locator) | A locator URI with scheme and location information. | `https://example.org:443/users/42`. |

A URL may contain a port and path, but the port is only one part of the address. The word endpoint may refer to an API operation, socket address, or protocol endpoint; state which.

## Proxy, Reverse Proxy, and Gateway

| Term | Usual role | Example and use |
|---|---|---|
| Forward proxy | Acts for clients toward external servers. | An organization routes employee browser traffic through a policy-controlled proxy. |
| Reverse proxy | Acts in front of backend servers toward clients. | A front end routes web traffic to a pool of application instances. |
| Gateway | Connects or mediates between systems or protocol domains. | A gateway translates a legacy interface into a service API. |

Products may combine these roles. Identify the direction, trust boundary, and function instead of relying on the product label.

## API Gateway and Load Balancer

An API gateway focuses on API-level policies and routing, such as identity checks, request shaping, or version routing. A load balancer distributes traffic across targets to improve capacity or availability. One product can do both; the functions are distinct.

## Middleware, Framework, and Library

| Term | Who usually controls the flow? | Example |
|---|---|---|
| Library | Your code calls library functions. | A JSON parsing library. |
| Framework | The framework often calls your code at defined extension points. | A web framework invokes a route handler. |
| Middleware | A component in a request or data path applies shared processing. | A request logger runs before a handler. |

Middleware can be provided by a framework or library. These terms describe different roles and can overlap.
