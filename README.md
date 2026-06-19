# VårdAI — Product documentation

Product management artifacts for [VårdAI](https://vardai.se), an AI-driven clinic reception and patient communication platform built for the Swedish market, with a Gulf-market expansion in progress.

These documents reflect real product decisions made while building and operating VårdAI in production — not hypothetical exercises.

## Contents

- **[PRD — AI Reception feature](./PRD.md)**
  Problem statement, user personas, success metrics, feature requirements, edge cases, and risk mitigations for VårdAI's core AI triage and booking feature.

- **[Competitive teardown](./Competitive_Teardown.md)**
  Feature and positioning comparison against Dentally and Carestream Dental, with a clear read on where VårdAI's wedge is and where incumbents still win.

- **[Roadmap](./Roadmap.md)**
  Past, present, and future feature priorities, sequenced against GDPR compliance, first paying customer, and Gulf market expansion.

- **[User interview](./Real_Interview.md)**
  Findings from a real clinic receptionist interview — covering current workflow gaps, trust requirements for AI adoption, and a key edge case (appointment duration) that fed back into the PRD.

- **[Clinic outreach findings](./Clinic_Outreach_Findings.md)**
  Field notes synthesized from informal conversations with ~20 Stockholm clinics during direct outreach — covering current reception workflows and reaction to AI-driven alternatives.

## About VårdAI

VårdAI provides 24/7 multilingual AI reception for dental and aesthetic clinics — handling patient triage, booking, and FAQs in Swedish, English, and Arabic, with automatic escalation to clinic staff when needed.

**Stack:** Next.js, TypeScript, Supabase (PostgreSQL), Groq AI, Stripe, Resend, 46elks, Vercel
**Code repository:** [github.com/unicorn123456/vardai](https://github.com/unicorn123456/vardai)

## About the author

Ikbal Ismail — licensed dentist (DDS, Karolinska Institutet), DevOps engineering student, and founder building at the intersection of healthcare, software, and the Swedish/Gulf markets.

[vardai.se](https://vardai.se) · [aurive.se](https://aurive.se)

- **[Meta Ads campaign plan](./Aurive_Meta_Ads_Campaign_Plan.md)**
  Targeting, creative, and budget specification for a planned Meta Ads test, built directly on insights from real clinic outreach conversations.

- **[SEO blog posts (English summary)](./SEO_Blog_Posts_English_Summary.md)**
  Three SEO-targeted blog posts written for aurive.se in Swedish, summarized here in English. Covers after-hours booking loss, local SEO strategy, and multilingual patient communication.

  - **[Build retrospective](./Retrospective.md)**
  A retrospective on building V\u00e5rdAI solo without a formal Scrum process — what worked, what took longer than expected (AI triage tuning), and how a definition of done would have prevented the overrun.
- **[Project plan — Linear](./Linear_Project_Plan.md)**
  A scoped Linear board for shipping Arabic language support, breaking AI-related work into concrete, prioritized issues — directly applying the lesson from the retrospective.

- **[Risk register](./Risk_Register.md)**
  Top 10 risks across regulatory, technical, and commercial categories, scored by likelihood and impact — commercial risks sourced directly from real outreach and interview findings.

- **[Stakeholder map](./Stakeholder_Map.md)**
  Maps all parties involved in a V\u00e5rdAI clinic onboarding across four groups — clinic staff, patients, external services, and regulators — and explains why each group has a different relationship to trust and risk.
