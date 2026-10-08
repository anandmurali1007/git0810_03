---
guid: 5fd5208e-93b5-4ae4-b2fa-71a9af8079a3
title: AI agents
seo:
  title: AI agents
display:
  toc: true
  outline: true
feedback:
  comments: true
---

An AI agent is a system in which a language model decides which actions to take, takes them using tools, observes the results and repeats until it completes a goal.

## Agents compared with chat assistants

| | Chat assistant | Agent |
| --- | --- | --- |
| Output | A reply | Actions and a result |
| Steps | One | Many, chosen by the model |
| Tools | Usually none | Search, code execution, APIs, file access |

## The agent loop

1. **Plan.** The model reads the goal and decides the next step.
2. **Act.** It calls a tool, such as a search API or a function in your system.
3. **Observe.** It reads the tool's result.
4. **Repeat** until the goal is met, then report back.

## Building blocks

- **Tools** with clear names, descriptions and input schemas, so the model knows when and how to use them.
- **Memory** that carries useful facts between steps or sessions.
- **Guardrails** that limit which actions the agent can take without approval.

## Designing safe agents

- Give the agent the **fewest permissions** it needs.
- Require **human approval** for actions that are costly or hard to undo, such as sending email or deleting data.
- **Log every action** so you can review what the agent did and why.
- Set **limits** on the number of steps and the cost of a run.
- Treat content the agent reads from the web or from documents as **untrusted data**, not as instructions.
