# Learning Loop Workspace

## What This Is
A workspace shape for learning, systematically, why the team wins or loses competitive outcomes — and turning that into reusable intelligence. When a competitive process resolves (we won, or we lost), this workspace assembles the factual record, runs a consistent forensic on what actually decided the outcome, and captures a structured record into an accumulating store. The store is the point: over many records it reveals which kinds of cases the team wins, where its bids fall short, which dimension (price, certainty, structure) actually decides outcomes, and whose feedback to trust. Built for any team that wants its outcomes to compound — more cases won means more of whatever success looks like — instead of relearning the same lessons one process at a time.

This is not a tracking system and it does not own the pipeline — your CRM and the downstream workspaces own that. This workspace does the one thing those do not: it explains *why* a competitive outcome happened, and remembers.

## A Different Shape: the Learning Loop
The other shapes in this toolkit are linear — a request or a case or a reporting cycle flows through stages and the output leaves: a notice sent, a case decided, a report distributed. This workspace is a **loop**. Its output does not leave; it is deposited into the workspace's own memory (`_store/`) and read back to inform future runs and other workspaces. Three properties make it different:
- **The flow is circular.** `01_signal` and `02_analysis` read from the store for context; `03_capture` writes back to it. The output's destination is the system's own future input.
- **The deliverable is the store, not the per-run record.** A single win/loss write-up is nearly worthless alone. The asset is the accumulating corpus and the patterns that emerge across it.
- **It is retrospective.** It is triggered by an outcome that already happened, and it exists to digest that outcome, not to produce a forward deliverable.

If you have used the decline log in the gated-decision-pipeline shape or the FAQ bank in the recurring-operations-queue shape, this is that write-back instinct made into the whole workflow — pointed at the outcome record.

## Current State
- This is a shape skeleton. The store is empty.
- To use: copy the folder, populate _config with your win/loss question set, taxonomy (including your controlled counterparty list), and store schema, then run the loop each time a competitive process resolves.

## Structure
```
learning-loop/
  CLAUDE.md              # You are here.
  CONTEXT.md             # Workflow routing. How the loop closes.
  01_signal/
    CONTEXT.md           # Stage contract: assemble the record from the source system + debrief + outcome.
    output/              # The factual record for one process.
  02_analysis/
    CONTEXT.md           # Stage contract: forensic on why, against the canonical questions.
    output/              # The structured analysis for one process.
  03_capture/
    CONTEXT.md           # Stage contract: validate the why, write to the store, update the patterns.
    output/              # Capture log: what was written and which patterns moved.
  _config/               # Win/loss questions, taxonomy, store schema.
  _store/                # THE ASSET. Accumulating records + the rolled-up patterns.
```

## How to Use
1. Read CONTEXT.md to understand how the loop closes.
2. Populate _config/ with your canonical win/loss questions, your taxonomy (case type, size band, process type, counterparty type, your controlled counterparty list, domain), and your store schema.
3. When a competitive process resolves — won or lost — start in 01_signal. Assemble the record from the source system, the debrief, and the final outcome.
4. Move to 02_analysis. Run the forensic against the canonical questions so this record is comparable to every other, keeping the counterparty's *stated* reason distinct from your *assessed* real reason.
5. Move to 03_capture. The team lead validates the "why," then the record is written to the store and the patterns are updated.
6. Read `_store/patterns.md` before the next attempt, before chasing a process, or whenever you set strategy — that is the loop paying off.

## Key Decisions
- **The store is the deliverable.** Treat the per-process record as an input to the asset, not the asset. Resist the urge to make any single write-up perfect; invest instead in making records comparable so the corpus is queryable.
- **Comparability over richness.** Every record answers the same canonical questions from _config, in the same structure, tagged by the same taxonomy. A pile of beautifully written but non-comparable narratives cannot reveal a pattern. This is Constraint 04 (Session Consistency) as the core design principle.
- **The source system and the record are the source; the model never invents the record.** Our entry, our terms, and our bid come from the record; the outcome comes from the debrief or public record. The model assembles and analyzes; it does not recall a process from memory. See Constraint 09 (Platform Boundary).
- **Counterparty "why you lost" feedback is often a polite fiction.** "They had a higher bid" frequently masks the real reason — "they didn't trust our certainty." The single most damaging thing this workspace can do is capture that spin as the real reason and let it shape future attempts. Two defenses: question 5 forces the *stated* reason and the *assessed* real reason apart, and the human validation gate at capture stops an unvalidated "why" from entering the store.
- **A human validates the why before it is captured.** The analysis is the model's proposed explanation. Causal claims about why we won or lost are exactly the thing that, if wrong, poisons the store. The team lead confirms the "why" before it becomes institutional memory.
- **The store feeds other workspaces.** `_store/patterns.md` is meant to be read by the decision and strategy workspaces — not just by this one. The loop is triggered *by* their outcomes and pays back into them.
- **Treat the store as sensitive intelligence.** Our behavior, our gap to the winning outcome, and our read on specific counterparty relationships are confidential. Handle and store accordingly.

## Constraints That Apply
Built against the Kit. Most relevant: the universal **06 (Layer Triage)** and **09 (Platform Boundary)**, plus **04 (Session Consistency)** — the load-bearing one here, **03 (Context Hygiene)**, and **08 (Handoff Readiness)**. Pull **10 (Source Provenance)** when more than one version of the record is in play.

## Layer Annotations
- CLAUDE.md: L0 (always loaded, orientation)
- CONTEXT.md: L1 (workflow routing)
- Stage CONTEXT.md files: L2 (stage contracts)
- _config/ files: L3 (reference: questions, taxonomy, schema)
- _store/ files: L3/L4 hybrid — persistent memory read by future runs (L3-like) and written each run (L4-like). This dual role is the signature of the learning-loop shape.
- The source-record / debrief / outcome data and per-run stage outputs: L4 (working artifacts)
