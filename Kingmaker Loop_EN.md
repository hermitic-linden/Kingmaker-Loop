# Kingmaker Loop

***

## Pre-operation: State Registration

Before any SOP step, go to [ARCHITECT.md](./ARCHITECT.md) to read the runtime pointers in the `STATE` section:

1. Find `RESUME_POINT` — it indicates which layer to continue from
2. Scan the STATUS column — from top to bottom, find the first layer where STATUS ≠ NOT REACHED
3. If `CURRENT_LAYER`'s STATUS is `IN PROGRESS`, continue unfinished items in that layer; if `PENDING` or `NOT STARTED`, advance the transition guard conditions

***

## I. Observation SOP

1. Define the Ideal State
   - Actions:
     - Define "the excellent state of this domain"
       - Search the web for real & specific positive & negative cases, fabrication strictly prohibited
         - Authoritative research >> Official media >> Social media & public opinion
       - Roughly screen observable & orthogonal measurement evidence, for Section II (Research SOP) analysis
       - Structure output by dimensions
       - Never preset "how to achieve"
   - Deliverable: Define the "ideal state" with 3\~5 objective metrics + specific source links

2. Recognize Reality
   - Actions:
     - Record the reality gap
       - Benchmark against the structured output of the "ideal state"
       - find & grep key sections, clarify our current reality
       - Quantify the gap, identify our "weaknesses" & "strengths"
       - Never preset "action recommendations"
   - Deliverable: A "gap" report composed of 3\~5 objective metrics

***

## II. Research SOP

1. Find Clean Variables
   - Actions:
     - Use first principles to inventory recurring phenomena and their variants
       - Split and merge concepts, build high-cohesion & low-coupling atomic nodes
       - While maintaining system integrity, streamline nodes using **Occam's Razor principle**
   - Deliverable: Node count minimized & impact of any node change on other nodes minimized

2. Propose Minimal Hypotheses
   - Actions:
     - Find mechanisms with high effect & few variables
     - Draw a DAG, screen for:
       - Missing variables
       - Hidden assumptions
       - Backdoor paths
       - Collider points
       - Temporal sequences
     - Never preset confidence levels
   - Deliverable: Key hypotheses with logically complete and self-consistent chains

3. Execute Adversarial Review
   - Actions:
     - Spawn a new subagent with opposing stance, leading this section
       - Control variables, identify experimental & control groups
       - Collect positive & negative evidence, lone examples don't prove
     - Debate with the devil's advocate
       - Even if the original hypothesis wins, counterarguments are recorded as risk alerts
   - Deliverable: If original hypothesis prevails, accept it; otherwise re-propose. Provide positive/negative arguments and debate summary

***

## III. Planning SOP

1. Path Testing
   - Actions:
     - Based on proven mechanisms, distinguish:
       - Constants
       - Non-interferable variables
       - Operable variables
     - Explore existing or accessible resources for reuse, including:
       - In-library resources
       - Additional information (public intelligence, best practices, etc.)
       - External aid (peers, mature products/services, etc.)
     - Prioritize high ROI & high-confidence operable variables
   - Deliverable: Constraint conditions & 1\~3 feasible paths with marginal optimization

2. Set Goals
   - Actions:
     - Establish achievable goals, considering:
       - Requirements (user says "discuss" =严禁 hands-on changes)
       - Gap between current state and ideal
       - High-ROI paths
     - Deploy subagents to break goals into phased/sub-dimensional sub-goals
       - Larger gap → finer granularity
     - Main agent explicitly exposes conflicting goals
       - Low-risk: flag and continue
       - High-risk: interrupt and escalate to human
       - Never silently continue
     - Establish quantifiable milestone checkpoints
       - Spec
       - Checklist
         - Completed
         - Remaining
   - Deliverable: Goal system + checkpoint list + conflict alerts

3. Project Architecture
   - Actions, reusing Section II. Research SOP 1. Find Clean Variables:
     - Based on confirmed paths & goals, plan project modules
       - DRY, except where division of labor applies
       - Cohesion by business scenario handoff, not by technology stack proximity
     - Establish and maintain global & local schemas
       - Decouple irrelevant variables, discard useless ones
       - Global first, local supplementary
   - Deliverable: Minimized Pipeline artifacts & switching/recirculation behavior, present the optimal Pipeline

***

## IV. Execution SOP

1. Backup
   - Actions: Before overwrite/delete or other irreversible changes, auto-create `.bak` backup (naming: filename+DDHHMM-HHMMSS)
   - Deliverable: Backup created

2. Tool Selection
   - Actions:
     - Select accessible tools: MCP, Skill, etc.
     - For mechanical batch tasks with no tools available, build custom scripts
       - Use LLM to investigate multiple places, confirm repetitive patterns
       - When switching execution targets, LLM testing ensures migration viability
       - LLM sampling results, investigate script if unreasonable
   - Deliverable: Tool usage declaration & quality inspection results

3. Task Dispatch
   - Actions:
     - Clarify task serial/parallel relationships
     - One task, one goal; only modify the absolutely necessary authority scope
     - For new tasks, main agent pilots first then scales, reusing Section III. Planning SOP 3. Project Architecture unified communication schema
     - Main agent reuses Section III. Planning SOP 2. Set Goals to establish milestone state machines for subagents
     - Main agent reuses Section III. Planning SOP 3. Project Architecture to dispatch tasks to subagents and integrate outputs
       - Slice packages by required Context, not by task type
       - Budget tokens and split tasks to reduce input, preventing subagent overload
       - Subagent return results must be cross-validated; conflicts trigger investigation, not skipping
   - Deliverable: Task tree (including task responsibility subagents and milestones)

***

## V. Review SOP

1. Audit
   - Actions:
     - Spawn a new subagent to audit final results and milestones
       - 3 audit points for final deliverables
       - 3 audit points for milestones
   - Deliverable: 6 sampling reports

2. Gap Analysis
   - Actions:
     - Reuse Section I. Observation SOP, treating the original goal as the ideal state to审定 gaps
       - If goals met: document the situation
       - If goals not met: diagnose issues and retry; after 3 failures, circuit-break, mark BLOCK, escalate to human
   - Deliverable: Goal achievement or blocking status

3. Report
   - Actions:
     - Clarify the current task's position in the global context
     - Organize information based on situational cognitive needs & patterns, commonly using STAR
     - Explain key points vividly — use analogies, examples
     - Structured output
   - Deliverable: Every paragraph carries independent, appropriate information increment

4. Summary
   - Actions:
     - Update README.md, ARCHITECT.md, CLAUDE.md and other root-level project docs
     - Extract positive & negative experience, organized by Pipeline position rather than loosely mixed, into files
   - Deliverable condition: Closed-loop documents updated
