# Recurring Document Production Workspace

## What This Is
A workspace shape for producing reader-facing communications (a recurring report, a board report, statements, scheduled notices) from data through drafting through distribution. Built for any team that reports to stakeholders on a recurring cycle and needs a consistent voice without rebuilding the process every period.

## Current State
- This is a shape skeleton. No active reporting cycle.
- To use this workspace: copy the folder, populate _config with your voice, format, and constraints, and start with stage 01.

## Structure
```
recurring-document-production/
  CLAUDE.md              # You are here. Workspace map and entry point.
  CONTEXT.md             # Workflow routing. How stages connect.
  01_data/
    CONTEXT.md           # Stage contract: gather and verify the numbers.
    output/              # Verified data pack. Becomes input for 02_draft.
  02_draft/
    CONTEXT.md           # Stage contract: write the report or notice.
    output/              # Drafts. Becomes input for 03_distribution.
  03_distribution/
    CONTEXT.md           # Stage contract: finalize, format, distribute.
    output/              # Reader-ready files.
  _config/               # Reference material. Voice, format, constraints.
  _prompts/              # Reusable prompt fragments for common tasks.
```

## How to Use
1. Read CONTEXT.md to understand the full workflow.
2. Populate _config/: the team voice comes from the shared `_shared-config/voice-and-tone.md` (this workspace's voice-and-tone.md just points to it and adds the report register); fill format patterns and constraints here (see Constraint 05 in the Kit).
3. Start in 01_data. Follow the stage contract. Drop output into 01_data/output/. If more than one version of a source export exists, confirm the authoritative one before pulling figures (Constraint 10, Source Provenance).
4. Move to 02_draft. The stage contract tells you which files from 01_data/output/ to use.
5. Move to 03_distribution. Same pattern.
6. Human review happens between every stage. The numbers and the language both get read before they go to a reader.

## Key Decisions
- **Three stages, not five or seven.** Most reporting workflows have more detail than this, but three stages is the minimum viable decomposition. Gathering the numbers, writing the narrative, and distributing are distinct modes of work. Combining them produces worse output in all three, and mixing data assembly with drafting is how a wrong figure ends up in a report to stakeholders. You can add stages (e.g., 02a_review between draft and distribution) when your process earns the complexity.
- **_config is separate from stages.** Voice, constraints, and format patterns are reference material (L3 in ICM terms). They are configured once and stay stable across cycles. Keeping them outside the numbered stages means updating your disclosure language does not require touching stage contracts.
- **Output directories are the handoff points.** Stage 01 writes the verified data pack to 01_data/output/. Stage 02 writes from there. This makes the data flow explicit and gives you a clear place to reconcile numbers before they reach the narrative.
- **No upstream analysis in this shape.** Producing the figures is a different workflow. This workspace reports on figures the platform already owns. Mixing the analysis with the reporting clutters the data stage.

## Constraints That Apply
Built against the Kit. Most relevant: the universal **06 (Layer Triage)** and **09 (Platform Boundary)** so the model narrates verified figures and never generates or adjusts a number, plus **01 (AI Writing Patterns)** and **02 (Output Drift)** so the report reads clean and stays consistent cycle to cycle, and **05 (Voice Architecture)** so it sounds like the team regardless of who runs the cycle. Pull **10 (Source Provenance)** when more than one version of an export is in play.

## Layer Annotations
- CLAUDE.md: L0 (always loaded, ~800 tokens, orientation)
- CONTEXT.md: L1 (loaded on workspace entry, routing)
- Stage CONTEXT.md files: L2 (loaded per-task, stage contract)
- _config/ files: L3 (reference, loaded selectively per stage)
- Source data and stage outputs: L4 (working artifacts, loaded selectively)
