# Kingmaker Loop

***

## Design Philosophy

Guessing, discussing, trial and error, handoff — an AI's thinking chain is long and messy. That's normal, and so is humans'. But—

**Never hand the sketchboard to the lord.**

Kingmaker Loop builds a lightweight agent state machine loop as an auditable patch for Codex, CC, Openclaw and other Harnesses. Rather than asking "Grill Me," why not white-box the AI? Humans govern from above, intervening at any moment.

***

## File Structure

| File             | Role          | Modifiable?            |
| -------------- | ------- | ------------- |
| `Kingmaker Loop.md`    | System rules    | ❌ Never modify, inject into prompts  |
| `ARCHITECT.md` | Runtime state snapshot | ✅ Writable file, placed in workspace |

***

## Execution Model

```
Parse rules from Kingmaker Loop.md
    → Read ARCHITECT.md state
    → Derive next action
    → Produce changes
    → Human reviews diff
    → Update ARCHITECT.md
```

***

## Quick Start

1. Put the content of Kingmaker Loop.md into the agent prompt
2. Place `ARCHITECT.md` in the project root
3. Chat with the agent, let it define the project for the first time
4. Fill layer by layer, advance, review

***

## Design Tradeoff Statements

### 1. The Strategist Is Not Registered as a Skill — Manual Dispatch is Forced

Kingmaker Loop **should not register as a Skill**. This is an intentional design decision:

- Human in the loop, not AI alone — A strategist without a lord is useless.

### 2. No Cross-layer Interaction Logic — Encourage Each to Fulfill Their Role

Kingmaker Loop **does not embed multi-layer ARCHITECT.md interaction logic**:

- **Everyone manages = No one manages** — Each ARCHITECT.md only handles its own layer, never overstepping to upper or lower levels.
- **Human scheduling** — In practice, you can place individual `ARCHITECT.md` files at any level (different-sized folders) within a project. Humans decide when and how to coordinate across layers.

This design keeps the strategist focused at a single granularity while preserving humans' ability to freely orchestrate across granularities.

### 3. ARCHITECT.md Is Not Split Into Files — Compels Holistic Thinking

Kingmaker Loop **does not split ARCHITECT.md into multiple files**:

- **Single source of truth** — All state, deliverables, and transition records are in one file, giving humans and agents a clear global view
- **Version control friendly** — A single diff reveals all changes across a full SOP cycle

This design keeps global state always visible, avoiding the execution blind spot of "seeing trees but not the forest."

***

> Kingmaker Loop v1.0 · 2026-07-05
