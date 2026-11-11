# Go / Streaming Telemetry Router

### Streaming telemetry with bounded fan-out and explicit failure behavior.

**Go** &nbsp;·&nbsp; **Engineering lab** &nbsp;·&nbsp; **Inspect, run, learn**

---

## Why this project matters

A small standard-library-only concurrent SSE server. Go channels separate the producer, detection engine and bounded subscribers; slow clients cannot stall ingestion. 5xx anomalies are detected using per-source sliding event-time windows.

The repository is intentionally small enough to read through, with the runtime behavior and design choices visible in the source files.

## Getting started

```bash
go test ./...
go run .
```

## Read the implementation

| Path | Role |
|--|--|
| [`README.md`](./README.md) | Background and documentation |
| [`go.mod`](./go.mod) | Go module metadata |
| [`main.go`](./main.go) | Core implementation |
| [`main_test.go`](./main_test.go) | Tests and expected behavior |

## A good way to explore it

1. Run the example using the instructions above.
2. Change a controlled input or simulated condition.
3. Compare what you observe with the source and existing tests.

## Scope

This is an illustrative, local engineering project rather than an independently audited production service. Synthetic data and test scenarios are for learning; do not rely on them for real-world operational guarantees.

<details>
<summary><strong>Detailed original notes and commands</strong></summary>

# Go / Streaming Telemetry Router

A small standard-library-only concurrent SSE server. Go channels separate the producer, detection engine and bounded subscribers; slow clients cannot stall ingestion. 5xx anomalies are detected using per-source sliding event-time windows.

```bash
go test ./...
go run .
# in another terminal
curl -N http://127.0.0.1:8088/events
```

Architecture: ticker → bounded channel → detector + fanout → SSE clients. Runs on localhost only. **Synthetic telemetry, not production logs.**

</details>

---

<sub>From [Sharanya Pal's engineering projects](https://github.com/sharanyapal?tab=repositories).</sub>
