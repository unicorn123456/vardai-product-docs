# VårdAI — Top 10 risks

**Author:** Ikbal Ismail
**Categories:** Regulatory, Technical, Commercial
**Date:** June 2026

---

## Regulatory

**1. IVO scrutiny over AI giving health-adjacent responses**
*Likelihood: Medium · Impact: Critical*
Mitigation: Hard prompt-level and output-validation guardrails preventing diagnosis or treatment advice; full conversation logging for audit; legal review of triage language before scaling beyond pilot clinics.

**2. GDPR violation via improper patient data handling**
*Likelihood: Medium · Impact: Critical*
Mitigation: Per-clinic row-level security in Supabase, 90-day auto-delete policy, no cross-session patient data retention.

**3. Tandvårdslagen marketing restrictions misapplied to AI-generated content**
*Likelihood: Low · Impact: Medium*
Mitigation: AI responses restricted to informational content only — no pricing promises or treatment-influencing language, consistent with rules that already govern human clinic marketing.

---

## Technical

**4. AI gives an incorrect or unsafe response**
*Likelihood: Medium · Impact: Critical*
Mitigation: System prompt guardrails, output validation layer, mandatory escalation on any symptom or emergency language.

**5. Groq API outage or rate-limit disruption**
*Likelihood: Low · Impact: Medium*
Mitigation: Graceful fallback to a maintenance message, error logging to Supabase, clinic notified automatically by email.

**6. Cross-clinic data leakage from a multi-tenant bug**
*Likelihood: Low · Impact: Critical*
Mitigation: Row-level security enforced at the database layer, not just application logic — tested explicitly as part of the per-clinic isolation workstream already in progress.

**7. Single-developer bottleneck — no redundancy if founder is unavailable**
*Likelihood: Medium · Impact: Medium*
Mitigation: Maintain clear documentation (this portfolio itself is part of that), prioritize infrastructure-as-code over manual configuration so the system is reproducible by someone else if needed.

---

## Commercial

**8. Clinics perceive the product as redundant alongside existing tools**
*Likelihood: High · Impact: Medium*
Mitigation: Confirmed directly in outreach conversations. Reposition messaging around what existing tools (receptionist, Bokadirekt) don't cover — after-hours and Arabic support — rather than competing head-on.

**9. Difficulty converting trial clinics to paying customers**
*Likelihood: High · Impact: Critical*
Mitigation: Prioritize smaller clinics without dedicated reception capacity (confirmed as the clearer ICP in outreach) over larger, well-staffed practices for early conversions.

**10. Trust barrier delays clinic adoption even after signing up**
*Likelihood: Medium · Impact: Medium*
Mitigation: Confirmed directly in the real clinic interview. Offer a supervised rollout period where staff review AI conversations before granting full autonomy.

---

## Note

Risks 8, 9, and 10 are sourced directly from real conversations — outreach findings and the clinic interview — not hypothetical guesses. They're rated High likelihood because they've already been observed, not projected.
