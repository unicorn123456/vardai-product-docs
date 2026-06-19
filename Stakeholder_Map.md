# VårdAI — Clinic onboarding stakeholder map

**Author:** Ikbal Ismail
**Scope:** All parties involved in onboarding a clinic to VårdAI
**Date:** June 2026

---

## Stakeholder groups

### Clinic-side people

**Clinic owner** — decision maker, evaluates by ROI. Wants oversight and confidence the AI won't create liability.

**Receptionist** — daily operator and the primary trust gate. Per the real clinic interview, wants a supervised rollout period before fully trusting the AI with patients.

**Dentist / clinician** — owns all clinical judgment calls. Per the same interview, appointment duration and any diagnosis-adjacent decision must stay with this stakeholder, never the AI.

### End users

**Patients** — need trust, clarity, and a fast resolution. The PRD's success metrics (CSAT, resolution rate) are written from this stakeholder's perspective.

**Arabic-speaking patients** — an underserved subgroup specifically, confirmed through both the real interview (the ad hoc translator problem) and the outreach findings. A distinct enough need to call out separately from "patients" in general.

### External services

**Stripe** — payment processing for clinic subscriptions.

**Groq** — AI inference provider powering the triage and conversation engine. A dependency risk (see risk register, item 5).

**Resend / 46elks** — email and SMS delivery for booking confirmations and staff notifications.

### Regulatory bodies

**IVO** (Health and Social Care Inspectorate) — oversees healthcare-adjacent services in Sweden. The top-rated risk in the risk register stems directly from this stakeholder's potential scrutiny.

**IMY** (Swedish Authority for Privacy Protection, GDPR enforcement) — governs how patient data is stored, processed, and retained. Directly shapes the row-level security and data-retention requirements already built into VårdAI.

---

## Why this grouping matters

Each group has a different relationship to risk and trust:

- **Clinic-side people** are the adoption gatekeepers — if the receptionist or owner doesn't trust the system, it never gets used regardless of how well it performs technically.
- **Patients** are the end beneficiaries, but have no direct say in the purchase decision — their experience has to be advocated for by the clinic-side stakeholders.
- **External services** are dependencies, not decision-makers — but their reliability and terms directly constrain what VårdAI can promise.
- **Regulatory bodies** don't interact with the product directly but define the boundaries everything else has to operate inside — which is why the two highest-impact items in the risk register are both regulatory.
