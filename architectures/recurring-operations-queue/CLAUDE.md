# Recurring Operations Queue Workspace

## What This Is
A workspace shape for handling inbound requests: the ad hoc questions and soft requests stakeholders send between formal events. "What is my current figure?" "Can you re-send my document?" "What is your view on X?" "We are thinking about expanding — who do we talk to?" This shape fits any team that fields a steady stream of stakeholder questions and wants consistent, accurate, on-voice responses without each one becoming a fire drill.

This is not transaction processing. The transactions of record — anything that changes a balance, moves money, or alters an account — are governed by your system of record, the platform that owns the data, not by an AI workspace (see Constraint 09, Platform Boundary). This workspace is for the inquiry traffic that arrives in between — informational, document, and light action requests.

## Current State
- This is a shape skeleton. No active queue.
- To use: copy the folder, edit _config files to match your team and your stakeholder base.

## Structure
```
recurring-operations-queue/
  CLAUDE.md              # You are here.
  CONTEXT.md             # Workflow routing.
  01_intake/
    CONTEXT.md           # Stage contract: receive, classify, prioritize, route.
    output/              # Classified request tickets, ready to resolve.
  02_resolve/
    CONTEXT.md           # Stage contract: gather governed data, draft, escalate.
    output/              # Drafted responses with escalation flags.
  03_respond/
    CONTEXT.md           # Stage contract: review, send, log, capture patterns.
    output/              # Sent responses and the request log.
  _config/               # Response standards, request context, FAQ bank.
  _templates/            # Reusable response templates.
```

## How to Use
1. Read CONTEXT.md for the full workflow.
2. Populate _config/ with your response standards, request context, and FAQ bank.
3. A new request enters through 01_intake. It gets classified, prioritized, and routed here.
4. The classified ticket moves to 02_resolve, where the answer is gathered from the system of record and drafted, with anything beyond the team's authority flagged for escalation.
5. The draft moves to 03_respond for an accuracy-and-tone review, then it is sent, logged, and any reusable answer is captured back into the FAQ bank.

## Key Decisions
- **Classification is the first job, not answering.** The intake stage sorts each request by type (informational / document request / action request / sensitive) before anyone drafts a word. A routine question and a "we are considering leaving" message look similar in an inbox and could not be more different in stakes. Classifying first is what keeps the sensitive ones from being answered casually.
- **The platform is the source of every figure.** A balance, a performance number, a financial figure of record — those come from the platform that owns the data, not from the model. The model retrieves and phrases; it never computes or recalls a number from memory. See Constraint 09 (Platform Boundary). This is the difference between an assistant and a liability.
- **Escalation is a designed step, not an exception.** Some requests are not the team's to answer: a departure signal, a contract interpretation, a complaint, a request that touches legal or compliance. The resolve stage flags these explicitly and routes them, rather than improvising an answer that commits the organization to something.
- **The FAQ bank compounds.** Every answered request that could recur gets captured. Over time the bank turns the same questions from research tasks into lookups, and keeps the team's answers consistent across every person who responds. This is Constraint 04 (Session Consistency) made concrete.
- **_templates is separate from _config.** Templates are response structures (acknowledgment, resolution, holding statement). Config is operating logic (what the team can answer vs. refer, the stakeholder record, the FAQ bank). They change at different rates.

## Constraints That Apply
This workspace was built against the Kit. The constraints most relevant here: the universal **06 (Layer Triage)** and **09 (Platform Boundary)**, plus **02 (Output Drift)**, **04 (Session Consistency)**, and **05 (Voice Architecture)**. Read them before customizing the stage contracts and _config.

## Layer Annotations
- CLAUDE.md: L0 (always loaded, orientation)
- CONTEXT.md: L1 (workflow routing)
- Stage CONTEXT.md files: L2 (stage contracts)
- _config/ files: L3 (reference material, response logic and stakeholder record)
- _templates/ files: L3 (reference material, response structures)
- Incoming requests and stage outputs: L4 (working artifacts)
