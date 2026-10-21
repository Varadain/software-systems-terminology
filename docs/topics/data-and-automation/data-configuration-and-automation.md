# Data, Configuration, and Automation

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

Programs exchange data and settings using agreed representations. A format is not automatically a schema: the format describes how values are written, while a schema describes which values and structures are expected.

## Formats and Structure

| Term | Meaning and use |
|---|---|
| **JSON** | JavaScript Object Notation: a text format for objects, arrays, strings, numbers, booleans, and null. Common for web APIs and configuration. |
| **YAML** | YAML Ain't Markup Language: a human-readable data serialization language often used for configuration. Indentation affects structure, so whitespace matters. |
| **XML** | Extensible Markup Language: a text format using nested elements and attributes, often with schemas and namespaces. |
| **CSV** | Comma-Separated Values: a tabular text format. Delimiter, quoting, and newline conventions matter; CSV is less expressive than a nested data format. |
| **TOML / INI** | TOML (Tom's Obvious, Minimal Language) and INI (initialization) are text formats often used for configuration. TOML has defined types and table structure; INI has several conventions and dialects rather than one universal specification. |
| **Schema / data model / metadata** | A schema describes permitted fields and constraints. A data model describes the concepts and relationships represented. Metadata is data that describes other data, such as units or timestamps. |
| **Configuration / manifest / configuration file** | Configuration changes program behavior without changing its code. A manifest records information about a package, project, deployment, or resource. A configuration file stores settings in a format such as TOML or YAML. |
| **API contract** | A shared agreement about an Application Programming Interface (API)'s operations, data, and behavior. It can be described with a schema or specification, but the contract may include behavior beyond field types. |
| **Parser / serializer** | A parser reads a representation and checks or converts its structure. A serializer converts values into a representation suitable for storage or exchange. |
| **Regular expression** | A compact pattern language for finding or validating text. It is useful for bounded text patterns, not a replacement for parsing nested languages. |

## Commands, Logs, and Automation

| Term | Meaning and use |
|---|---|
| **Command-line argument / CLI flag** | A Command-Line Interface (CLI) argument is a value passed to a command. A flag is an option that changes behavior, often written `--verbose` or `-v`. |
| **Environment variable** | A named value inherited by a process from its parent environment, often used to configure paths, modes, or service locations. Treat values that contain secrets as sensitive. |
| **Exit code** | A process result code. Many shells use zero for success and nonzero for a failure, but exact meanings are program-specific. |
| **Log / logging level / structured logging** | A log is a recorded event. A logging level labels urgency or detail. Structured logging stores fields, such as JSON key/value pairs, so tools can filter them. |
| **Event / telemetry / trace / metric** | An event records something that happened. Telemetry is data collected from a running system. A trace connects operations across a flow; a metric is a measured numeric value over time or a distribution. |
| **Validation** | Checking that data meets expected type, range, format, and business rules. Validate at trust boundaries and report errors clearly. |
| **Secrets management** | Practices and tools for storing, granting, rotating, and auditing secrets such as passwords and API tokens. Do not store secrets in source files or logs. |
| **Template** | A reusable pattern with placeholders filled from data, used to generate text, configuration, or other output. Validate generated output before using it. |

### Example: validate a result record

```json
{
  "run_id": 105,
  "status": "PASS"
}
```

A schema could require an integer `run_id` and restrict `status` to known values. The JSON syntax alone does not enforce those application rules.

**Common confusion:** YAML and JSON are formats; a parser reads a format; a schema states constraints. A valid JSON document can still violate an API's schema or business rules.

**References:** [RFC 8259: JSON](https://www.rfc-editor.org/info/rfc8259/); [W3C XML 1.0](https://www.w3.org/TR/xml/); [YAML 1.2.2 specification](https://yaml.org/spec/1.2.2/); [Python `json` documentation](https://docs.python.org/3.11/library/json.html); [GitHub Actions workflow files](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows).
