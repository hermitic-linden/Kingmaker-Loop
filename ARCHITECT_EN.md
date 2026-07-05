# ARCHITECT.md

> **Runtime Compressed Memory for the SOP Cycle**
>
> Essence: not a log, not a checklist, but an executable snapshot.
> Purpose: truncation recovery, context anchoring, sole basis for execution progression.
> Reading order: top to bottom; the topmost layer with STATUS ≠ NOT REACHED is the current execution point.
>
> ***
>
> ## Write Contract

> Each layer must obey the following three rules:
>
> 1. **State and content are bound** — Never write `STATUS: DONE` without documenting "what was done"
> 2. **Each layer has a minimum deliverable** — Empty placeholders must not exceed 3 lines (see Schema below)
> 3. **Inter-layer data flow is traceable** — Upstream output must be downstream input; no fabrication

## STATE

### Runtime Pointers

| Field              | Value                   | Description                         |
| ------------------ | ----------------------- | ----------------------------------- |
| `CURRENT_LAYER`    | `INIT`                  | Current SOP layer                   |
| `CURRENT_STEP`     | `—`                     | Sub-step within the current layer   |
| `CYCLE_COUNT`      | `0`                     | Completed full SOP cycles           |
| `LAST_ACTION`      | `File initialization`   | Last write action                   |
| `LAST_TIMESTAMP`   | `YYYY-MM-DDT__:__:__`   | Last write timestamp                |
| `RESUME_POINT`     | `STATE`                 | Resume from this line if context lost |

### State Machine Definition

```
INIT → OBSERVE → MODEL → PLAN → EXECUTE → REVIEW → (back to OBSERVE for new cycle)
  ↓        ↓         ↓        ↓          ↓         ↓
 BLOCK   BLOCK     BLOCK    BLOCK      BLOCK     BLOCK
```

**Transition Guards:**

| Transition         | Pre-condition                                 | Post-action                                   |
| ------------------ | --------------------------------------------- | --------------------------------------------- |
| INIT → OBSERVE     | `CURRENT_LAYER == INIT` and receives a concrete task | Clear all `_ [waiting to fill]` placeholders        |
| OBSERVE → MODEL    | OBSERVE layer has ≥ 3 non-empty deliverables  | Convert OBSERVE's "gaps" into MODEL's "variable screening scope" |
| MODEL → PLAN       | MODEL layer DAG has at least 2 verified edges | Inject MODEL's "operable variables" into PLAN's "path candidates" |
| PLAN → EXECUTE     | PLAN layer conflict targets resolved (low-risk continue / high-risk escalate) | Split milestones into sub-tasks, write EXECUTE task tree |
| EXECUTE → REVIEW   | EXECUTE layer all milestones status ≠ NOT\_STARTED | Collect deliverables, prepare audit         |
| REVIEW → OBSERVE   | REVIEW layer gap analysis complete            | New cycle; reduce granularity if gaps shrink, increase if gaps widen |
| Any layer → BLOCK  | 3 consecutive retries failed                  | Mark BLOCK, escalate to human decision        |

### Checkpoint Summary

| Checkpoint          | Pass Condition                                    | Current Status         |
| ------------------- | ------------------------------------------------- | ---------------------- |
| CP-1: Task directive clear | User input contains actionable domain/target     | `_pending_`            |
| CP-2: Backup ready  | `.bak` created before execution                   | `_not_needed_yet_`     |
| CP-3: Tools available | MCP/Skill list loaded                           | `_loaded_at_init_`     |

***

## OBSERVE

> **Corresponds to SOP Section I · Observation SOP**
>
> Input: User-specified domain/problem
> Output: Ideal state definition + reality gap report
> Guard: ≥ 3 objective metrics + traceable sources

### 1.1 Ideal State

#### Excellent State Indicators (3\~5 items, observable, orthogonal)

| #   | Indicator Name  | Measurement Method | Target Value  | Source/Case      |
| --- | --------------- | ------------------ | ------------- | ---------------- |
| O-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| O-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| O-3 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| O-4 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| O-5 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Success Cases (real, specific, linkable)

| ID   | Case Name       | Related Indicator | Key Success Factor | Source Link      |
| ---- | --------------- | ----------------- | ------------------ | ---------------- |
| SC-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| SC-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Failure Cases (real, specific, linkable)

| ID   | Case Name       | Related Indicator | Key Failure Factor | Source Link      |
| ---- | --------------- | ----------------- | ------------------ | ---------------- |
| FC-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| FC-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Dimension Structure Matrix

```
Dimension A ──→ [Indicator O-1]  [Indicator O-2]  [Indicator O-3]
Dimension B ──→ [Indicator O-4]  [Indicator O-5]  —
Dimension C ──→ —                —                —
```

> ⚠️ **Never preset "how to achieve"** — Here only define "what is good"

**STATUS: PENDING**
**FILLED\_ITEMS: 0/5**

***

### 1.2 Current State

#### Current Data

| Source        | Data Type     | Collection Time | Key Value     | Credibility    |
| ------------- | ------------- | --------------- | ------------- | -------------- |
| _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Identified Weaknesses

| #    | Weakness Description | Related Indicator | Quantified Gap | Evidence Source  |
| ---- | -------------------- | ----------------- | -------------- | ---------------- |
| SH-1 | _[waiting to fill]_ | O-_\[]_          | _[waiting to fill]_ | _[waiting to fill]_ |
| SH-2 | _[waiting to fill]_ | O-_\[]_          | _[waiting to fill]_ | _[waiting to fill]_ |

#### Identified Strengths

| #    | Strength Description | Related Indicator | Quantified Advantage | Reusability      |
| ---- | -------------------- | ----------------- | -------------------- | ---------------- |
| ST-1 | _[waiting to fill]_ | O-_\[]_          | _[waiting to fill]_ | _[waiting to fill]_ |

> ⚠️ **Never preset "action recommendations"** — Here only record "what is now"

**STATUS: PENDING**
**FILLED\_ITEMS: 0/3**

***

### 1.3 Gap Report

#### Gap Matrix

| #   | Dimension   | Ideal Value   | Current Value | Gap Amount    | Urgency      |
| --- | ----------- | ------------- | ------------- | ------------- | ------------ |
| G-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| G-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| G-3 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Gap Attribution (preliminary, no actions)

```
G-1 ← [Cause A?] [Cause B?]
G-2 ← [Cause C?]
G-3 ← [Cause D?] [Cause E?] [Cause F?]
```

**STATUS: PENDING**
**FILLED\_ITEMS: 0/3**

***

## MODEL

> **Corresponds to SOP Section II · Research SOP**
>
> Input: Gap report from OBSERVE output
> Output: Clean variables + minimal hypotheses + DAG
> Guard: Variable atomicity, hypothesis falsifiability, DAG with verification marks

### 2.1 Clean Variables

#### Variable Inventory (First Principles Decomposition)

| ID | Variable Name | Type      | Definition | Value Range | Relation to Others | Occam Score* |
| -- | ------------- | --------- | ---------- | ----------- | ------------------ | ------------ |
| V1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| V2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| V3 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

> \*Occam Score: 1=necessary and indivisible, 2=mergeable, 3=removable

#### Variable Merge Record

```
Original Concept A + Original Concept B → V1 (reason: _)
Original Concept C → V2 (kept independent)
Original Concept D [removed: duplicate/irrelevant]
```

#### Coupling Matrix (verify high cohesion & low coupling)

| <br /> | V1 | V2 | V3 |
| ------ | -- | -- | -- |
| V1     | —  | \_ | \_ |
| V2     | \_ | —  | \_ |
| V3     | \_ | \_ | —  |

> `_` = strong coupling / weak coupling / no coupling

**STATUS: PENDING**
**FILLED\_ITEMS: 0/3**

***

### 2.2 Minimal Hypotheses

#### Hypothesis List (High Effect × Few Variables)

| ID | Hypothesis Statement | Involved Variables | Predicted Outcome | Falsifiability Condition | Confidence Mark* |
| -- | -------------------- | ------------------ | ----------------- | ------------------------ | ---------------- |
| H1 | _[waiting to fill]_ | V\_\[\_]          | _[waiting to fill]_ | _[waiting to fill]_     | _[waiting to fill]_ |
| H2 | _[waiting to fill]_ | V\_\[\_]          | _[waiting to fill]_ | _[waiting to fill]_     | _[waiting to fill]_ |

> ⚠️ **Never preset confidence** — Mark as `_unverified_`, determined by adversarial review

#### DAG (Causal Graph)

```
[V1] ──→ [H1] ──→ [Outcome A]  (Verified ✓ / Hypothesis △ / Untested ?)
  │           │
  ▼           ▼
[V2] ──→ [H2] ──→ [Outcome B]
                    │
                    ▼
                  [Outcome C]
```

#### DAG Screening Checklist

| Screening Item       | Finding           | Handling         |
| -------------------- | ------------------- | ---------------- |
| Missing variables    | _[waiting to fill]_ | _[waiting to fill]_ |
| Hidden assumptions   | _[waiting to fill]_ | _[waiting to fill]_ |
| Backdoor paths       | _[waiting to fill]_ | _[waiting to fill]_ |
| Collider points      | _[waiting to fill]_ | _[waiting to fill]_ |
| Temporal sequence contradiction | _[waiting to fill]_ | _[waiting to fill]_ |

**STATUS: IN PROGRESS**
**FILLED\_ITEMS: 0/2**

***

### 2.3 Adversarial Review

#### Review Configuration

| Field     | Value                    |
| --------- | ------------------------ |
| Reviewed Hypothesis | H\_\[\_]        |
| Opposing Stance | _[waiting to fill]_    |
| Experiment Group | _[waiting to fill]_    |
| Control Group | _[waiting to fill]_     |
| Execution Method | New subagent, opposing stance |

#### Positive Evidence

| #    | Evidence Description | Source        | Lone Example Check* |
| ---- | -------------------- | ------------- | ------------------- |
| PE-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

> \*Lone evidence doesn't prove — Single evidence marked as `_insufficient_`

#### Negative Evidence

| #    | Evidence Description | Source        | Refutation Possibility |
| ---- | -------------------- | ------------- | ---------------------- |
| NE-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Devil's Advocate Debate Summary

```
Proponent: [Core argument of H1]
Opponent: [Counterargument]
Rebuttal: [Proponent's response]
Final: [Does H1 pass?]
```

**STATUS: PENDING**
**RESULT:** _**[waiting to fill]**_

***

## PLAN

> **Corresponds to SOP Section III · Planning SOP**
>
> Input: Verified hypotheses + clean variables from MODEL output
> Output: Path candidates + variable classification + conflict resolution + milestones
> Guard: 1\~3 paths, conflicts explicitly flagged

### 3.1 Path Candidates

#### Path List (Based on Verified Mechanisms)

| ID | Path Description | Dependent Hypothesis | Dependent Variables | ROI Rating | Confidence |
| -- | ---------------- | -------------------- | ------------------- | ---------- | ---------- |
| P1 | _[waiting to fill]_ | H\_\[\_]          | V\_\[\_]           | _[waiting to fill]_ | _[waiting to fill]_ |
| P2 | _[waiting to fill]_ | H\_\[\_]          | V\_\[\_]           | _[waiting to fill]_ | _[waiting to fill]_ |
| P3 | _[waiting to fill]_ | H\_\[\_]          | V\_\[\_]           | _[waiting to fill]_ | _[waiting to fill]_ |

#### Resource Reuse Matrix

| Resource Type | Specific Resource | Reusability | Acquisition Cost |
| ------------- | ----------------- | ----------- | ---------------- |
| In-library resources | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| Public intelligence | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| External aid | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

**STATUS: PENDING**
**SELECTED\_PATH:** _**[waiting to fill]**_

***

### 3.2 Variable Classification

#### Constants

| ID | Constant Name | Value | Immutable Reason |
| -- | ------------- | ----- | ---------------- |
| C1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Non-interferable Variables

| ID | Variable Name | Value | Impact Scope |
| -- | ------------- | ----- | ------------ |
| U1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Operable Variables

| ID | Variable Name | Current Value | Target Value | Operation Method | Risk Level |
| -- | ------------- | ------------- | ------------- | ---------------- | ---------- |
| M1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| M2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

**STATUS: PENDING**
**OPERABLE\_COUNT: 0**

***

### 3.3 Conflict Targets

| #    | Target A      | Target B      | Conflict Nature | Risk Level | Resolution |
| ---- | ------------- | ------------- | --------------- | ---------- | ---------- |
| CF-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

> **Risk Level Definition:**
>
> - Low-risk: Flag and continue
> - High-risk: **Interrupt execution, escalate to human**

**STATUS: PENDING**
**CONFLICTS\_RESOLVED: 0/_[waiting to fill]_**

***

### 3.4 Milestone Checkpoints

| ID   | Milestone Name | Spec | Acceptance Criteria | Completed | Remaining |
| ---- | -------------- | ---- | ------------------- | --------- | --------- |
| ML-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| ML-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

**STATUS: PENDING**
**TOTAL\_MILESTONES: 0**

***

## EXECUTE

> **Corresponds to SOP Section IV · Execution SOP**
>
> Input: Paths + operable variables + milestones from PLAN output
> Output: Task tree + tool declarations + backup records
> Guard: Backup first, pilot then scale, context-based task slicing

### 4.1 Backup Status

| File        | Backup Time | Backup Path                            | Status     |
| ----------- | ----------- | -------------------------------------- | ---------- |
| _[waiting to fill]_ | _[waiting to fill]_ | `_[filename]+DDHHMM-HHMMSS.bak`_ | _[waiting to fill]_ |

> **Rule:** Before irreversible changes (overwrite/delete), backup first. Naming format: `original_filename-DDHHMM-HHMMSS.bak`

**STATUS:** _**[waiting to fill]**_

***

### 4.2 Tool Declarations

| Tool Type | Selected Tool | Justification | Alternative |
| --------- | ------------- | ------------- | ----------- |
| MCP       | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| Skill     | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| Script    | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Self-built Script Quality Check

| Script       | Repetitive Pattern Confirmed | Migration Test | Sampling Result |
| ------------ | ---------------------------- | -------------- | --------------- |
| _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

***

### 4.3 Task Tree

#### Main Task Decomposition

| ID | Task Description | Responsible Party | Dependencies | Parallel/Serial | Milestone | Status |
| -- | ---------------- | ----------------- | ------------ | --------------- | --------- | ------ |
| T1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | ML-\[\_] | _[waiting to fill]_ |
| T2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | ML-\[\_] | _[waiting to fill]_ |
| T3 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | ML-\[\_] | _[waiting to fill]_ |

#### Sub-Agent Dispatch Records

| Sub-Agent | Task | Allocated Context | Token Budget | Return Result | Cross-validation |
| --------- | ---- | ----------------- | ------------ | ------------- | ---------------- |
| SA-1      | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Task Dependency Graph

```
T1 ──→ T3 ──→ T5
 │        │
 ▼        ▼
T2 ──→ T4
```

**STATUS: NOT STARTED**
**COMPLETED\_TASKS: 0**

***

## REVIEW

> **Corresponds to SOP Section V · Review SOP**
>
> Input: Deliverables from EXECUTE output
> Output: Audit results + gap analysis + STAR report + Pipeline summary
> Guard: 6 sampling points (3 deliverables + 3 milestones)

### 5.1 Audit Points

#### Final Deliverable Audit (×3)

| #    | Audit Object | Audit Dimension | Finding | Severity |
| ---- | ------------ | --------------- | ------- | -------- |
| AP-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| AP-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| AP-3 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

#### Milestone Audit (×3)

| #    | Audit Object | Acceptance Criteria | Actual Result | Deviation |
| ---- | ------------ | ------------------- | ------------- | --------- |
| AM-1 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| AM-2 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |
| AM-3 | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ |

***

### 5.2 Gap Analysis

| Dimension | Expected | Actual | Deviation | Diagnosis | Retry Count | Result |
| --------- | -------- | ------ | --------- | --------- | ----------- | ------ |
| _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | _[waiting to fill]_ | 0/3 | _[waiting to fill]_ |

> **Circuit Breaker Rule:** 3 consecutive retry failures → mark `BLOCK`, escalate to human

***

### 5.3 Report (STAR Structure)

#### Situation

_[waiting to fill]_

#### Task

_[waiting to fill]_

#### Action

_[waiting to fill]_

#### Result

_[waiting to fill]_

***

### 5.4 Summary

#### Experience Organized by Pipeline Position

| Pipeline Position | Positive Experience | Negative Experience |
| ----------------- | ------------------- | ------------------- |
| OBSERVE           | _[waiting to fill]_ | _[waiting to fill]_ |
| MODEL             | _[waiting to fill]_ | _[waiting to fill]_ |
| PLAN              | _[waiting to fill]_ | _[waiting to fill]_ |
| EXECUTE           | _[waiting to fill]_ | _[waiting to fill]_ |
| REVIEW            | _[waiting to fill]_ | _[waiting to fill]_ |

#### Document Update Record

| File           | Update Time | Update Content |
| -------------- | ----------- | -------------- |
| README.md      | _[waiting to fill]_ | _[waiting to fill]_ |
| ARCHITECT.md   | This round  | Status sync    |
| CLAUDE.md      | _[waiting to fill]_ | _[waiting to fill]_ |

**STATUS: NOT REACHED**

***

## TRANSITION LOG

> Records of every inter-layer state transition

| # | Timestamp    | From  | To      | Trigger Condition | Data Compression Summary | Anomaly |
| - | ----------- | ----- | ------- | ----------------- | ------------------------ | ------- |
| 1 | _[to fill]_ | INIT  | OBSERVE | User assigns task | _[to fill]_              | _[to fill]_ |

***

## INTEGRITY

### Content Integrity Check

| Layer     | Minimum Deliverables              | Current Count | Completeness |
| --------- | --------------------------------- | ------------- | ------------ |
| OBSERVE   | 3 (metrics) + 3 (gaps)            | 0             | 0%           |
| MODEL     | 3 (variables) + 2 (hypotheses) + 1 (DAG) | 0       | 0%           |
| PLAN      | 3 (paths) + 1 (classification) + 1 (conflict) | 0  | 0%           |
| EXECUTE   | 1 (backup) + 1 (tools) + 3 (tasks) | 0             | 0%           |
| REVIEW    | 6 (audits) + 1 (report) + 1 (summary) | 0          | 0%           |

### Inter-layer Data Flow Trace

```
OBSERVE.Gap → MODEL.VariableScope: _[Not Established]_
MODEL.DAG → PLAN.PathDependency: _[Not Established]_
PLAN.OperableVariables → EXECUTE.TaskTree: _[Not Established]_
EXECUTE.Deliverables → REVIEW.AuditObjects: _[Not Established]_
```

### Checksum Protocol

```
After each complete cycle (OBSERVE → REVIEW), compute:
CHECKSUM: <SHA-256 of all filled content>
COMPLETION_CYCLE: 0
```

***

## QUICK REFERENCE

### Status Quick Lookup

| Layer     | STATUS        | Progress        |
| --------- | ------------- | --------------- |
| STATE     | `INIT`        | Ready           |
| OBSERVE   | `PENDING`     | 0/5 metrics     |
| MODEL     | `PENDING`     | 0/3 variables   |
| PLAN      | `PENDING`     | 0/3 paths       |
| EXECUTE   | `NOT STARTED` | 0/3 tasks       |
| REVIEW    | `NOT REACHED` | 0/6 audits      |

### Common Operations Quick Reference

| Action      | Operation                                                    |
| ----------- | ------------------------------------------------------------ |
| Advance layer | Fill all `_ [waiting to fill]_` in current layer         |
| Transition layer | Check guard conditions → Update STATE → Append TRANSITION\_LOG |
| Truncate & recover | Read RESUME\_POINT → Continue from that layer          |
| Circuit breaker | 3 consecutive failures → Mark BLOCK → Escalate to human |
| Complete cycle | Compute CHECKSUM → CYCLE\_COUNT++ → Back to OBSERVE       |
