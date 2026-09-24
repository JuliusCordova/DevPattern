# Pack — MCP Integration

## Intent

Expose or consume tools, resources, and reusable context through the Model Context Protocol (MCP).

MCP is appropriate when a capability should be portable across agent frameworks, coding assistants, or enterprise agent runtimes.

## Use when

- a tool should be reused by multiple agents or clients;
- capabilities should be discoverable through a standard interface;
- the integration must remain decoupled from one agent framework;
- enterprise routing, authorization, metering, or governance benefits from a standard tool surface.

## Avoid when

- the capability is local and used by one agent only;
- a direct in-process function is simpler;
- protocol overhead adds no material value.

## Structure

```text
Agent / Client
    ↓
MCP Client
    ↓
MCP Server
 ├─ Tools
 ├─ Resources
 └─ Prompts / Extensions
    ↓
Enterprise Systems
```

## FAST
- direct tools preferred;
- introduce MCP only for a real reuse/integration need.

## MVP
- explicit schemas;
- versioned tool/resource contracts;
- authorization;
- contract tests;
- error semantics.

## PRODUCT
- current MCP protocol version;
- stateless deployment where supported;
- gateway authorization/rate limits;
- observability;
- approval for high-risk operations;
- compatibility/conformance testing.

## 2026 note

MCP 2026-07-28 introduces a stateless protocol core, stronger authorization guidance, cacheable capability listings, and an extension model. Long-running work can use the MCP Tasks extension.

## Key rule

> Use MCP to standardize reusable capabilities — not to wrap every local function.
