# Security and Reliability

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

Security controls reduce risks to systems and information. Reliability concerns correct service over time. The same design choices—clear boundaries, bounded work, good failure handling—can help both, but the goals are not identical.

## Identity and Access

| Term | Meaning and use |
|---|---|
| **Authentication / authorization / identity** | Authentication establishes which person, service, or device is acting. Authorization decides which actions that identity may perform. An identity is the subject being recognized. |
| **Privilege / least privilege / permission** | Privilege is the authority available to a subject. Least privilege grants only the access needed for a task. A permission is a specific allowed or denied action on a resource. |
| **Credential / secret / API token** | A credential proves or conveys identity or access. A secret is sensitive data such as a password or private key. An Application Programming Interface (API) token is a credential presented to an API. Store, scope, and rotate them carefully. |
| **Audit log** | A record of security-relevant actions, such as access grants or configuration changes. Protect it from unauthorized changes and avoid recording raw secrets. |

## Cryptography and Threats

| Term | Meaning and use |
|---|---|
| **Encryption / hashing / encoding** | Encryption transforms data using a key so authorized parties can recover it. Hashing maps data to a digest and is generally designed to be one-way. Encoding changes representation and is not secrecy. |
| **Digital signature / public key / private key** | A digital signature lets a verifier check that data was signed by a holder of a private key and was not altered. A public key can be shared; its matching private key must be protected. Exact properties depend on the scheme. |
| **Certificate / TLS** | A certificate binds identity information to a public key under a trust system. Transport Layer Security (TLS) protects a channel and uses certificates in common server-authenticated deployments; certificate validation must be performed correctly. |
| **Vulnerability / threat model / attack surface** | A vulnerability is a weakness that could be exploited. A threat model identifies assets, actors, trust boundaries, and likely threats. Attack surface is the set of reachable interfaces and conditions an attacker might target. |
| **Input validation / sanitization** | Validation checks input against expected rules. Sanitization transforms input for a specific safe use. Neither should be confused with output encoding or parameterized APIs; use defenses appropriate to the context. |
| **Sandbox / isolation / fault containment** | A sandbox restricts what code can access. Isolation separates components or privileges. Fault containment limits how far a failure can spread. These properties depend on implementation and configuration. |

## Security Properties and Recovery

| Term | Meaning and use |
|---|---|
| **Confidentiality / integrity / availability** | Confidentiality limits disclosure to authorized parties. Integrity protects against unauthorized change. Availability keeps a service accessible when needed. Together they are often called the confidentiality, integrity, and availability (CIA) triad. |
| **Backup / recovery** | A backup is a recoverable copy of data or configuration. Recovery restores service or data after loss; a backup is useful only if it can be restored and meets the recovery objective. |
| **Idempotency / timeout / retry / rate limiting** | Idempotency makes repeated intended operations safe under defined conditions. A timeout bounds waiting. A retry repeats selected work. Rate limiting controls request frequency. These controls limit resource use and duplicate effects. |

**Common confusion:** Authentication is “who is acting?”; authorization is “what may they do?” Hashing is not a substitute for encryption. Password storage needs password-specific protection rather than a fast general-purpose digest alone.

**References:** [NIST cybersecurity glossary](https://csrc.nist.gov/glossary); [NIST SP 800-63 glossary](https://pages.nist.gov/800-63-4/sp800-63/glossary/); [RFC 8446 TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446.html).
