# The CC/CT Project — Architecture

**Continuous Capture / Continuous Training**

Three interactive architecture diagrams, published as one static site. No build step, no server, no dependencies — open `index.html` or serve the folder from any static host.

| Tab | Diagram | Licence of the thing it describes |
|---|---|---|
| **Overall Product** | How both engines fit together, and the loop that closes between them | — |
| **Continuous Capture** | The collector pipeline: tap, assemble, redact, join signals, emit | Apache-2.0 |
| **Continuous Training** | The model engine: refine, train, evaluate, gate, deliver | Proprietary |

## The seam

Capture ends when a clean, redacted event lands in a sink the customer controls. Training begins by deciding which 2–5% of it is worth learning from. The boundary between them is the canonical event schema `event.v1` — a technical fault line rather than a commercial one, which is why it holds.

Capture runs inside the customer's network, never touches the request path, and writes JSONL for a log shipper they already run. Training refines, trains, and proves the result beats both the base model and the frontier baseline before any weights are released.

## Using the site

- Tabs switch engines; keys `1` `2` `3` do the same
- Deep links: `#overview`, `#capture`, `#training`
- **About** opens the seam explanation and the validation receipts
- Each diagram has its own theme toggle, guided views, search, edge tracing, presentation mode, and PNG/SVG/WebM export

## Layout

```
index.html                       the site shell
diagrams/overview.html           architecture · 8 components, 2 regions
diagrams/capture.html            dataflow · 5 stages, 12 nodes
diagrams/training.html           workflow v2 · 6 lanes, 8 nodes
src/overview.architecture.json   diagram specification, for future edits
```

Each diagram is a self-contained artifact embedded byte-for-byte as delivered. All three passed showcase validation at 9/9 checks with zero errors and zero warnings.

Diagrams generated with [archify](https://skills.sh/tt-a1i/archify).
