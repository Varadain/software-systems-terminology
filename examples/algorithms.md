# Algorithms and Practical Examples

**Navigation:** [Home](../README.md) | [Topic Index](../docs/index.md) | [Roadmap](../docs/learning-roadmap.md)

These small pseudocode examples show the idea, not production-ready implementations. Real systems also need error types, security checks, observability, cancellation, and platform-specific rules.

## Client Request and Response

**Goal:** Ask for a test-run result and handle success or failure.

```text
request = make_request(method="GET", path="/runs/105")
response = send(request)
if response.status is 200:
    result = parse_json(response.body)
    show(result.status)
else:
    show_error(response.status)
```

## Server Request Handling

**Goal:** Route each request to a handler, or return a not-found response. **Input:** a request. **Output:** a response.

```text
while server_is_running:
    request = receive_request()
    route = find_route(request.method, request.path)
    if route does not exist:
        send_response(404, "not found")
    else:
        response = route.handle(request)
        send_response(response)
```

## Proxy and Middleware

```text
function proxy(request):
    backend = choose_backend(request.path)
    return forward(request, backend)

function authentication_middleware(request, next):
    identity = validate_credential(request.headers)
    if identity is invalid:
        return response(401, "authentication required")
    request.identity = identity
    return next(request)
```

The proxy forwards toward a backend. Middleware checks or changes a request before passing it to the next handler. Authentication does not by itself grant every permission.

## REST-Style CRUD

REST (Representational State Transfer) is a resource-oriented architectural style. CRUD means Create, Read, Update, Delete. One illustrative resource mapping is:

| Intent | Method and path | Example result |
|---|---|---|
| Create | `POST /users` | Return a created user identifier. |
| Read | `GET /users/42` | Return the user's representation. |
| Update | `PUT /users/42` | Replace the resource representation. |
| Partial update | `PATCH /users/42` | Change selected fields. |
| Delete | `DELETE /users/42` | Remove or deactivate the resource. |

Actual API contracts may define different semantics and status codes.

## RPC Call

Remote Procedure Call (RPC) represents a remote operation as a named method call.

```text
request = GetUserRequest(id=42)
reply = user_service.GetUser(request)
if reply.ok:
    display(reply.user.name)
else:
    handle_rpc_error(reply.error)
```

The caller invokes a remote operation through a generated or hand-written client. Network delay and failures still exist even if the call syntax resembles a local function.

## TCP Client/Server Exchange

```text
server_socket = create_stream_socket()
bind(server_socket, address, port)
listen(server_socket)
connection = accept(server_socket)
message = read_bytes(connection)
write_bytes(connection, make_reply(message))
close(connection)
```

TCP provides a byte stream, so an application protocol must define how messages are framed. One `read` is not necessarily one whole application message.

## Bounded Retry and Exponential Backoff

```text
attempt = 0
delay = initial_delay
while attempt < max_attempts:
    result = try_operation()
    if result.success:
        return result
    if result.is_permanent_failure:
        stop
    wait(delay + random_jitter())
    delay = min(delay * 2, max_delay)
    attempt = attempt + 1
return failure
```

Retry only failures that may succeed later. A timeout may leave it unclear whether the server completed the action; use idempotency or deduplication for repeatable effects.

## Queue and Producer/Consumer

**Goal:** Let one part of a program add work while another processes it later. **Input:** queued items. **Output:** processed items and acknowledgements.

```text
producer(item):
    queue.push(item)

consumer():
    while running:
        item = queue.pop_wait()
        process(item)
        acknowledge(item)
```

The queue separates when work is created from when it is processed. Real queues define durability, ordering, visibility timeout, and redelivery behavior.

## Simple Cache Lookup

**Goal:** Reuse a recent value when available and fetch it on a cache miss. **Input:** a key. **Output:** the value for that key.

```text
function get_run(run_id):
    key = "run:" + run_id
    if cache.contains(key):
        return cache.get(key)

    result = database.read_run(run_id)
    if result exists:
        cache.put(key, result, expires_after=short_duration)
    return result
```

For example, a second request for `run:105` can use the cached result until it expires. A cache needs an expiry or invalidation rule so old data does not appear current forever.

## Input Validation

```text
function validate_run_request(data):
    if data.run_id is not an integer:
        return invalid("run_id must be an integer")
    if data.run_id < 1:
        return invalid("run_id must be positive")
    return valid(data)
```

Validation checks the data shape and allowed values at a trust boundary. It should match the operation and data model; sanitization is context-specific and does not replace validation.

## Logging and Error Handling

```text
try:
    result = load_run(run_id)
    log_info(event="run_loaded", run_id=run_id)
    return result
catch expected_not_found:
    log_warning(event="run_missing", run_id=run_id)
    return response(404)
catch unexpected_error as error:
    log_error(event="run_load_failed", run_id=run_id, error_type=type(error))
    return response(500)
```

Use structured context that helps diagnosis, but do not log credentials or sensitive payloads.

## Testbench Check

```text
drive(dut.input, test_value)
wait_for(dut.done)
expected = reference_model(test_value)
actual = monitor(dut.output)
assert actual == expected
record_coverage(test_value, actual)
```

The reference model provides an expected result. The scoreboard or assertion reports a mismatch; coverage records whether selected scenarios occurred.

## Basic CI Pipeline

Continuous Integration (CI) runs automated checks as changes are integrated.

```text
on change:
    checkout source
    install declared dependencies
    build
    run unit tests
    run integration checks
    publish build artifact if checks pass
```

CI automates checks on changes. Publishing an artifact is not the same as deploying it to production.
