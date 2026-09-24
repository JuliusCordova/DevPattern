# Pack — A2A Interoperability

## Intent

Use Agent2Agent (A2A) when independent agentic applications need to discover capabilities, exchange tasks, and collaborate across framework or vendor boundaries.

## Use when

- agents are independently deployed;
- different teams/vendors own agents;
- remote agents must remain opaque to one another;
- task lifecycle, artifacts, streaming, or asynchronous collaboration matter.

## Avoid when

- specialists run in the same process;
- a direct function/tool call is simpler;
- the agents do not need independent lifecycle or ownership.

## Structure

```text
Client Agent
    ↓
Agent Card / Discovery
    ↓
A2A
    ↓
Remote Agent
    ↓
Task / Artifact / Status
```

## FAST DEMO
- do not introduce A2A unless interoperability is the demo itself.

## MVP
- Agent Card;
- bounded skills;
- task contract;
- authentication;
- failure/retry semantics.

## PRODUCT
- signed/verified discovery where appropriate;
- authorization;
- streaming or async updates;
- task lifecycle evidence;
- compatibility tests;
- data minimization between agents.

## Key rule

> MCP connects agents to tools and context; A2A connects independently deployed agents to other agents.
