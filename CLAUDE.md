# Kit

You are an AI agent. Someone has handed you this repository and asked you to set up — or work
within — their operating system for working with AI. This file is what Claude Code auto-loads,
so it is your starting point.

## Where to go from here

**If `_shared-config/setup-progress.md` does not exist, setup has not run yet.** Read `SETUP.md`
and follow it. It runs the organization's one-time orientation, builds the first workspace, and then
rewrites this file into the organization's operating-system map. To begin, the user need only say
**"Run setup."**

**If `_shared-config/setup-progress.md` exists, setup has already run** — and this file should
already be the organization's OS map (see below). If you are still reading this bootstrap text,
something interrupted the first setup; re-read `SETUP.md` and resume from **After First Setup: Write
the OS Map**.

## What this repository is

Kit, a general-purpose system for putting AI behind the recurring knowledge work any
organization runs. It has three parts — `architectures/` (four reference workspace shapes plus
worked examples), `constraints/` (ten reference files), and `skill-starters/` (builder skills) —
plus `SETUP.md`, the engine that runs setup, builds workspaces, and (when you are ready) finalizes
the repo into your operating system. `SETUP.md` explains all of it; you do not need to load the
three folders yourself.

## Adding workflows, and after setup

You can keep building forever — new workflow types, or more instances of ones you already run.
Just say **"Run setup"**, **"add a workflow"**, or **"build a &lt;workflow&gt;"**; that routes to
`SETUP.md`. Once the first setup finishes, `SETUP.md` overwrites this file with the organization's
OS map, which headlines how to add a workflow and lists what is built and what is still available. An
optional, reversible **finalize** step later moves the toolkit into `_kit/` so the root reads
purely as the organization's operating system — `SETUP.md` describes it.
