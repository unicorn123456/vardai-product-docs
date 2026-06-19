# VårdAI — Build retrospective

**Author:** Ikbal Ismail
**Scope:** Solo build, May–June 2026
**Date:** June 2026

---

VårdAI was built solo, end to end, without a formal Scrum process — no written backlog, no sprint boundaries, just sequential building based on what felt most urgent at each point. The build went smoothly overall, with one consistent exception: AI triage and prompt tuning took meaningfully longer than expected relative to every other part of the system.

---

## What went well

**Infrastructure and integrations were predictable**
Next.js, Supabase, Stripe, Resend, and 46elks all integrated close to expected effort. These are well-documented, well-bounded problems with clear success criteria — "is the payment processed," "did the SMS send" — which made estimating and building them straightforward even without formal sprints.

**Sequential building matched a solo developer's reality**
Without a team to coordinate, a written backlog added overhead without clear benefit — building the next most urgent thing, in order, was actually the right call for a single person moving fast.

---

## What took longer than expected, and why

**AI triage and prompt tuning had no clear "done"**
Unlike integrations with binary success criteria, triage logic is inherently fuzzy — there's no single test that confirms the AI is "behaving correctly" across every patient scenario. Each round of testing surfaced new edge cases (mixed-language input, ambiguous symptom descriptions, patients testing the system's limits) that weren't visible until real-feeling conversations were tried.

**No defined "definition of done" for AI behavior specifically**
Every other feature had an implicit definition of done (the form submits, the SMS arrives). AI triage didn't — there was no checklist of "these N scenarios must be handled correctly" to test against, so the work kept expanding because there was no clear finish line.

---

## If this were run as a formal Scrum project

Here's how I'd structure it differently, applying what the SFC™ (Scrum Fundamentals) framework would suggest for a project with this exact failure pattern:

**Sprint 1 — Infrastructure foundation**
Next.js setup, Supabase schema, auth, deployment pipeline. Same as actual build order — this part didn't need to change.

**Sprint 2 — AI triage, scoped with a written edge case backlog**
Before writing prompts, define 15–20 specific test scenarios (mixed language, emergency symptoms, vague questions, trial-expired sessions) as backlog items with explicit acceptance criteria. Treat each edge case as its own ticket, not as part of "build the AI feature."

**Sprint 3 — Integrations (Stripe, Resend, 46elks)**
Run in parallel with sprint 2's edge case testing — these have clear definitions of done and don't block on triage logic being finished.

**Sprint 4 — Multilingual support and RLS hardening**
Sequenced last since it builds on top of triage logic already being stable — adding a second/third language to an unstable triage system would have multiplied the debugging surface.

---

## Definition of done — AI triage (in hindsight)

This is the artifact that was missing during the actual build. If written in advance, it would have turned an open-ended task into a checklist:

- Correctly identifies and responds in Swedish, English, and Arabic
- Never provides a diagnosis or treatment recommendation
- Escalates to staff on any emergency-coded language
- Handles mixed-language input without breaking
- Gracefully handles questions outside the clinic's configured knowledge base
- Logs every conversation for staff review

---

## Key takeaway

The lesson isn't "use Scrum for everything" — sequential building was the right call for most of this project. The specific lesson is narrower: for any feature with fuzzy, subjective success criteria (especially AI behavior), write the definition of done as a concrete test list before starting, even on a team of one. That single artifact would have turned an open-ended task into a finite one.
