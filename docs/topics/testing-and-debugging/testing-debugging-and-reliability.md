# Testing, Debugging, and Reliability

**Navigation:** [Home](../../../README.md) | [Topic Index](../../index.md) | [Roadmap](../../learning-roadmap.md)

Testing compares observed behavior with an expectation. Debugging uses evidence to find why behavior differs. Reliability describes whether a system keeps providing useful behavior under expected conditions and failures.

## Planning and Running Tests

| Term | Meaning and use |
|---|---|
| **Test case / test suite / test plan** | A test case specifies inputs, conditions, and expected results. A suite groups tests. A test plan describes scope, approach, resources, risks, and schedule. |
| **Testbench / fixture / setup / teardown** | A testbench supplies stimulus and checks a design or system. A fixture provides shared test data or environment. Setup prepares state; teardown cleans it up. |
| **Assertion / expected result / actual result** | An assertion checks a condition. The expected result is the requirement-derived outcome; the actual result is what execution produced. |
| **Pass / fail / skip / flaky test** | A pass meets the test's checks. A failure violates one. A skipped test is intentionally not run. A flaky test changes outcome across runs without a relevant code change, often due to timing or shared state. |
| **Reproduction steps / debugging / breakpoint / stack trace** | Reproduction steps describe how to trigger an issue. Debugging investigates it. A breakpoint pauses execution. A stack trace shows a call path associated with an event or failure. |
| **Log analysis / root cause analysis** | Log analysis looks for evidence in recorded events. Root cause analysis investigates underlying contributing conditions rather than stopping at a symptom. |
| **Defect / bug / issue / incident** | A defect or bug is a flaw in a product or process. An issue is a tracked item or problem. An incident is an operational event affecting service or users. Teams may define these terms differently. |
| **Severity / priority / regression** | Severity describes impact; priority describes urgency or ordering of work. A regression is a previously working behavior that breaks after a change, or a test that checks for such a break. |

## Test Levels and Purposes

| Term | Main question | Example |
|---|---|---|
| **Unit test** | Does one small function or component behave as expected? | Check a parser with valid and invalid text. |
| **Integration test** | Do connected components exchange data correctly? | Verify an API handler and its database adapter work together. |
| **System test** | Does the assembled system meet specified behavior? | Check a full test-results service against its contract. |
| **End-to-end test** | Can a user-level path cross the real system boundaries? | Create a test run in a UI and retrieve its result. |
| **Regression test** | Does a previously fixed behavior stay fixed after changes? | Re-run a test for an earlier parser defect. |
| **Smoke test** | Does a build or service pass a small set of basic checks? | Start the service and request its health endpoint. |

These labels can overlap. An end-to-end test can also be a regression test, and a smoke test may operate at system level. Choose the term that explains both the scope and purpose.

## Coverage and Test Techniques

| Term | Meaning and use |
|---|---|
| **Code coverage / branch coverage / functional coverage** | Code coverage measures which code executed. Branch coverage measures decision outcomes. Functional coverage measures whether specified behaviors, values, or scenarios were exercised. Coverage does not prove correctness. |
| **Mock / stub / fake / test double / mocking** | A test double replaces a dependency. A stub returns prepared responses; a mock records or verifies expected interactions; a fake is a lightweight working substitute. Mocking is the practice of replacing or observing dependencies with mock objects. Exact usage can vary by testing community. |
| **Fault injection / negative testing / boundary testing / fuzz testing** | Fault injection deliberately introduces failures. Negative testing checks invalid or rejected input. Boundary testing checks edges of ranges. Fuzz testing generates many varied inputs to find robustness defects. |
| **Static analysis / dynamic analysis / lint / sanitizer / profiling** | Static analysis examines code without running the target program. Dynamic analysis observes execution. A linter checks likely defects or style rules. A sanitizer detects selected runtime errors. Profiling measures resource use and performance. |
| **Monitoring / observability / alert** | Monitoring tracks known signals and conditions. Observability is the ability to investigate internal behavior from external outputs such as logs, metrics, and traces. An alert notifies when a defined condition is met. |
| **SLI / SLO / SLA** | A Service Level Indicator is a measurement of service behavior. A Service Level Objective is a target for an indicator. A Service Level Agreement is an external or contractual commitment, often with consequences. |
| **Availability / reliability / recovery** | Availability asks whether a service is usable when needed. Reliability asks whether it performs correctly over time. Recovery is restoring useful behavior after disruption. A service can be available yet unreliable. |

### A small test example

```text
input: add(2, 3)
expected: 5
actual: call function and record result
assert actual == expected
```

This checks one case. It does not prove behavior for all inputs, integration with other modules, or the correctness of the requirement itself.

**References:** [Python `unittest`](https://docs.python.org/3/library/unittest.html); [GitHub Actions CI](https://docs.github.com/en/actions/get-started/continuous-integration); [OpenTelemetry observability primer](https://opentelemetry.io/docs/concepts/observability-primer/).
