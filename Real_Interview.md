# VårdAI — Clinic receptionist interview

**Author:** Ikbal Ismail
**Method:** Conversational interview, based on a direct clinic relationship
**Date:** June 2026

---

**Sample:** 10–15 calls/messages per day · Most common questions: availability and pricing · After-hours: cancellation possible, booking not possible

---

## Current workflow

**Daily routine is manual and call-driven**
Staff open the booking software each morning, review new bookings, work through a call-back to-do list, and handle incoming calls throughout the day — roughly 10–15 contacts daily.

**After-hours is asymmetric: cancel yes, book no**
Patients can leave a voicemail to cancel an existing appointment outside hours, but there's no way to book a new appointment or get questions answered during that window.

**Unreachable patients stall appointment adjustments**
When a clinic needs to adjust a booking — not just create one — they sometimes can't reach the patient to confirm the change, which causes real scheduling friction beyond just missed new bookings.

**Arabic-language patients sometimes require an ad hoc translator**
For patients who don't speak Swedish well, staff have had to ask a nearby person to help translate in the moment — an inconsistent, uncomfortable workaround for both staff and patient.

---

## Reaction to AI reception

**Trust would be built gradually, not granted upfront**
The clinic's instinct was that they wouldn't fully trust an AI to handle things well immediately — they'd want to try it for a period with a human supervising from time to time before relying on it fully.

**Appointment length can't be safely automated**
One specific limit surfaced clearly: appointment duration varies by treatment type and is determined by a clinical assessment of need. This isn't something the AI should decide on its own — it depends on a judgment call only clinical staff can make.

**Open to automating broadly, starting with FAQ-style questions**
When asked what they'd automate first, the answer was essentially "all of it" — but if forced to prioritize, general/repetitive question answering was named as the natural starting point.

---

## What this validates and changes in the PRD

**Validates:** Booking intent capture, Arabic language support, and the supervised-trust pattern (gradual rollout with human oversight) are all directly confirmed by this conversation.

**New requirement:** Appointment duration must never be fully automated — the AI should propose a duration range and flag it for staff confirmation rather than auto-booking a fixed slot length. This is a new edge case to add to the PRD.
