# Gated Decision Pipeline Workspace

## What This Is
A workspace shape for the top of a funnel: triaging inbound items fast against a known bar, so the few worth real effort advance and the many that do not get a clean, fast, defensible decline. Built for any team that sees far more opportunities, requests, or cases than it can pursue and wants to apply its decision criteria consistently instead of deciding from memory under time pressure.

This is the front door. Whatever committed effort sits downstream — a full project, a detailed analysis, a build — this shape decides which items earn that effort at all. Its output on an "advance" is the handoff that seeds the downstream work.

## Current State
- This is a shape skeleton. No active queue.
- To use: copy the folder, populate _config with your decision criteria, the bar, and your rough-evaluation assumptions.

## Structure
```
gated-decision-pipeline/
  CLAUDE.md              # You are here.
  CONTEXT.md             # Workflow routing.
  01_intake/
    CONTEXT.md           # Stage contract: normalize the inbound item.
    output/              # Standard item snapshot. Input for 02_evaluate.
  02_evaluate/
    CONTEXT.md           # Stage contract: fit, rough check, disqualifiers.
    output/              # Evaluation with an advance/decline recommendation.
  03_decide/
    CONTEXT.md           # Stage contract: the go/no-go gate and handoff or decline log.
    output/              # The decision, the handoff brief, or the decline record.
  _config/               # Decision criteria, the bar, rough-evaluation assumptions.
  _references/           # Prior evaluations, the decline log, comparables and standards.
```

## How to Use
1. Read CONTEXT.md for the full workflow.
2. Populate _config/ with your decision criteria (what you take on), your thresholds (the go/no-go bar and automatic disqualifiers), and your rough-evaluation assumptions.
3. A new item enters through 01_intake. The brief, request, or inbound note gets normalized into a standard snapshot.
4. The snapshot moves to 02_evaluate, where it is measured against the bar, given a rough sanity check, and tested for disqualifiers, producing an advance / decline / need-more recommendation.
5. The recommendation moves to 03_decide — the gate. An "advance" produces the handoff brief that seeds the downstream workspace. A "decline" is logged with its reason.

## Key Decisions
- **Decline fast is the goal, not thoroughness.** This workspace exists to spend the least possible effort reaching a defensible decline on the items that do not fit, so attention is reserved for the ones that do. The stages are deliberately lean. If an evaluation takes as long as the downstream work, the criteria are not sharp enough.
- **Evaluate against the bar, not the pitch.** The inbound materials are the requester's case. The decision criteria in _config are what the team actually takes on. The evaluation measures the item against the bar, not against the inbound framing.
- **The rough check is a filter, not the full analysis.** The quick assessment in the evaluation is a sanity check to catch obvious non-starters, run on standard assumptions for consistency. The real analysis happens downstream with the model or spreadsheet that computes the numbers. Never present a screen-stage figure as the full analysis. See Constraint 09 (Platform Boundary).
- **A decline is an output, not a non-event.** Every decline is logged with its reason in _references. This keeps decisions consistent (the same kind of item gets the same answer), creates an audit trail, and over time reveals patterns in what the team sees and rejects.
- **The advance handoff is the bridge downstream.** An "advance" does not just say yes; it produces the structured brief that becomes the downstream workspace's input, so that work starts with the evaluation's findings, not from scratch.

## Constraints That Apply
Built against the Kit. Most relevant: the universal **06 (Layer Triage)** and **09 (Platform Boundary)**, plus **02 (Output Drift)** so every evaluation comes out comparable, and **08 (Handoff Readiness)** so the workspace can be handed to a new owner. Read them before customizing the stage contracts and _config.

## Layer Annotations
- CLAUDE.md: L0 (always loaded, orientation)
- CONTEXT.md: L1 (workflow routing)
- Stage CONTEXT.md files: L2 (stage contracts)
- _config/ files: L3 (reference: criteria, the bar, assumptions)
- _references/ files: L3 (cross-item: prior evaluations, decline log, comparables)
- Inbound item materials and stage outputs: L4 (working artifacts)
