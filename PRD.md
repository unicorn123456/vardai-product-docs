# VårdAI — AI Reception PRD

**Author:** Ikbal Ismail
**Version:** 1.0
**Status:** In production
**Date:** June 2026

---

## 1. Problem statement

Swedish dental and aesthetic clinics lose an estimated 20–35% of potential bookings outside office hours. Receptionists handle repetitive triage questions (opening hours, pricing, what to expect before a procedure), leaving less time for complex patient interactions. Clinics with Arabic-speaking patients face an additional gap: no affordable tool exists that handles triage in Arabic within a Swedish regulatory context.

VårdAI's AI Reception feature solves this by providing a 24/7 multilingual AI agent embedded in the clinic's workflow — triaging, booking, and escalating to staff only when necessary.

---

## 2. User personas

### Sara — Clinic receptionist
*Age 28–42 · Stockholm · Non-technical*

Handles 60–80 patient contacts per day. Frustrated by after-hours missed calls. Wants AI to handle routine questions without her needing to configure it. Fears it will say the wrong thing to patients.

### Ahmed — Arabic-speaking patient
*Age 25–55 · MENA background · Mobile-first*

Searches for dental care in Arabic. Often gives up when clinic websites are Swedish-only. Wants to ask basic questions and book without language anxiety. High trust barrier — needs warmth and clarity.

### Maria — Clinic owner
*Age 35–55 · Decision maker · ROI-focused*

Runs 1–3 locations. Evaluates tools by cost saved vs revenue added. Wants oversight — can she see what the AI said? Can she override it? IVO and GDPR compliance are non-negotiable concerns.

### Out of scope (v1)

Direct EHR integration, prescribing advice, emergency triage, insurance claims processing, multi-location shared inbox.

---

## 3. Success metrics

| Metric | Target |
|---|---|
| First response time | < 2s (p95) |
| Queries resolved without escalation | ≥ 80% at 30 days |
| Patient satisfaction (CSAT) | ≥ 4.0 / 5.0 |
| Languages supported at launch | 3 (SV / EN / AR) |
| Medical advice incidents | 0 — hard zero tolerance |
| Trial-to-paid conversion | ≥ 25% within 30-day window |

---

## 4. Feature requirements

| Feature | Description | Priority |
|---|---|---|
| Multilingual AI chat (SV/EN/AR) | Auto-detects patient language from first message. Responds in the same language. RTL rendering for Arabic. Powered by Groq llama-3.3-70b-versatile. | **P0 — must have** |
| Clinic-scoped knowledge base | Each clinic's AI only knows about that clinic. Pricing, hours, services configured per tenant. Row-level security enforced at Supabase level. | **P0 — must have** |
| Hard triage guardrails | AI must never diagnose, prescribe, or give medical advice. Symptom descriptions trigger escalation to staff. Enforced at prompt and output-validation level. | **P0 — must have** |
| Booking intent capture | Collects name, contact, preferred time, treatment type. Passes structured summary to clinic via email (Resend) and SMS (46elks). | P1 — should have |
| Conversation history per session | Grouped by session ID. Staff can review full logs in dashboard. No cross-session continuity for patients (GDPR). | P1 — should have |
| 30-day trial gate | Full feature access for 30 days. On day 31 without Stripe payment, AI is suspended and an automated offboarding email is sent. | P1 — should have |
| Clinic admin dashboard | View all conversations, AI accuracy flags, captured contact details, usage stats. CSV export. | P2 — nice to have |

---

## 5. Edge cases

- **Patient asks for a diagnosis.** AI responds: "I can't give medical advice, but I can help you book an appointment with our dentist who can assess this for you."
- **Patient writes in mixed languages (e.g. Arabizi).** AI defaults to Arabic response. If undetectable, defaults to English.
- **Clinic hasn't configured their knowledge base yet.** AI is disabled — widget shows a "Contact us by phone" fallback to prevent hallucinated clinic details.
- **Groq API outage.** Chat widget shows a maintenance message. Error logged to Supabase. Clinic notified by email. No silent failure.
- **Patient describes an emergency** (chest pain, severe bleeding). AI immediately displays: "This sounds urgent — please call 112 or go to your nearest emergency room."
- **Trial expires mid-conversation.** Current conversation completes. Next session blocked with an upgrade prompt shown to the clinic admin, not the patient.

---

## 6. Risks & mitigations

| Risk | Likelihood | Severity | Mitigation |
|---|---|---|---|
| AI gives incorrect medical info | Medium | Critical | System prompt guardrails + output validation layer |
| GDPR: conversation data stored improperly | Medium | Critical | Per-clinic RLS in Supabase + 90-day auto-delete policy |
| Groq API cost overrun | Low | Medium | Token limits per session + usage cap alerts |
| Clinics distrust AI-generated patient communication | High | Medium | Framed as "AI-assisted reception," full log visibility, easy escalation |

---

## 7. Tech stack

- **Frontend:** Next.js 14, TypeScript, Tailwind CSS
- **Auth & DB:** Supabase (PostgreSQL + RLS)
- **AI:** Groq API (llama-3.3-70b-versatile)
- **Payments:** Stripe
- **Email:** Resend
- **SMS:** 46elks
- **Hosting:** Vercel
- **Repo:** github.com/unicorn123456/vardai
