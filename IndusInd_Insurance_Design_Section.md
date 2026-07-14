# IndusInd Bank — Unified Insurance Platform
### Product Design Section | Capstone Submission — E-Cell IIT Guwahati x IndusInd Bank

---

## 1. User Journey

Mapping Priya's end-to-end journey — from being an insured-but-disengaged banking customer to an actively protected, retained one. I've split it into the same three pillars from the vision: Discover & Decide, Manage & Renew, Claim & Trust.

| Stage | Priya's experience today | Her experience on the platform |
|---|---|---|
| **Awareness** | Opens banking app for balance/UPI, never thinks about insurance | Sees a "Protection Score: 40%" card on her banking home screen — passive, non-intrusive, curiosity-driving |
| **Discovery** | Would have to Google, compare 5 insurer sites, fill 20-question forms | Taps the card → sees 2–3 pre-filled recommendations based on her existing banking profile (age, dependents inferred, existing loan/card data) — no fresh form |
| **Consideration** | Jargon (IDV, co-pay, NCB) makes her unsure what she's buying | Plain-language comparison cards ("This covers hospital stays up to ₹5L, no room-rent cap") + an AI assistant she can ask "what does this actually mean?" |
| **Purchase / Link** | Buys reactively at a showroom, or does nothing | Either buys in under 2 minutes (bank KYC pre-fills details) or links an existing policy from another insurer for free, unified tracking |
| **Ownership (steady state)** | Never opens an insurer app again until something breaks | Occasional dashboard visits triggered by useful nudges (renewal countdown, wellness perk, ecosystem service like roadside assistance) |
| **Renewal** | Missed her bike renewal last year, found out at a traffic stop | WhatsApp nudge 14 days before expiry with a one-tap renewal + pre-calculated quote |
| **Claim (moment of truth)** | Dreads this — has heard horror stories | Self-inspection video upload, real-time status tracker, resolution target under 48 hours for eligible claims |
| **Advocacy** | Has never recommended an insurer to anyone | A fast, transparent claim experience prompts an in-app referral nudge — she refers her sister |

The single most important design principle threaded through this: **every touchpoint should require less effort from Priya than the equivalent step with any competitor**, because the bank already has the data others have to ask for.

---

## 2. Key User Flows

I designed four core flows — these map directly to the 12-screen prototype.

### Flow A — Discover & Buy (new cross-sell)
`Banking Home → Protection Score card → Recommendation feed → Policy detail (plain-language) → Pre-filled purchase form (KYC auto-pulled) → Payment → Confirmation + added to dashboard`

### Flow B — Link an Existing Policy (trust-building, non-monetizing)
`Insurance Dashboard → "Add a policy" → Select insurer from list / upload policy doc → OCR or manual entry extracts key details → Policy appears on unified dashboard with renewal date tracked`

### Flow C — Renew
`WhatsApp/push notification (T-14 days) → Deep link to pre-filled renewal quote → One-tap UPI payment → Confirmation`
*(Deliberately short — friction here is the #1 cause of unwanted lapse, not a moment to add steps.)*

### Flow D — Claim
`Dashboard → "File a claim" → Select policy → Guided self-inspection video capture (motor) or document upload (health) → Real-time status tracker with plain-language stage labels ("Under review" → "Approved" → "Payout initiated") → Resolution`

---

## 3. Feature Prioritization (RICE Framework)

I used RICE (Reach × Impact × Confidence ÷ Effort) rather than MoSCoW here, because the roadmap decisions are genuinely about sequencing trade-offs across a large feature backlog, not a binary must/should split for a single release.

| Feature | Reach (1–10) | Impact (1–3) | Confidence (%) | Effort (person-months) | RICE Score | Priority |
|---|---|---|---|---|---|---|
| Unified dashboard (link + view policies) | 9 | 3 | 90% | 3 | 24.3 | **P0** |
| Protection Score home-screen card | 10 | 2 | 85% | 2 | 8.5 | **P0** |
| Pre-filled cross-sell purchase flow | 8 | 3 | 80% | 3 | 6.4 | **P0** |
| WhatsApp renewal nudges | 7 | 3 | 90% | 2 | 9.5 | **P0** |
| Motor self-inspection claims | 5 | 3 | 70% | 4 | 2.6 | **P1** |
| AI plain-language assistant | 6 | 2 | 65% | 3 | 2.6 | **P1** |
| RM-assisted dashboard | 3 | 2 | 80% | 2 | 2.4 | **P1** |
| Vernacular language support | 5 | 2 | 75% | 3 | 2.5 | **P1** |
| Ecosystem perks (roadside/telemedicine bundling) | 4 | 2 | 60% | 3 | 1.6 | **P2** |
| Fraud detection layer | 3 | 2 | 55% | 4 | 0.8 | **P2** |
| Referral program | 4 | 1 | 70% | 1 | 2.8 | **P2** |
| Personalization engine (life-stage triggers) | 5 | 2 | 50% | 4 | 1.25 | **P2** |

**Read on this:** the P0 set is deliberately trust-and-habit features (dashboard, score card, renewal nudges) plus one monetizing flow (cross-sell purchase) — not a features-first backlog. Claims automation is P1, not P0, because it needs real insurer-side SLA partnerships to work honestly; shipping a self-inspection flow that still takes 5 days behind the scenes would be worse than not shipping it yet.

---

## 4. Low/High Fidelity Wireframes & Prototype Walkthrough

The clickable prototype (12 screens) walks through the four flows above:

1. **Banking Home** — Protection Score card embedded above the usual balance/UPI tiles
2. **Protection Score detail** — breakdown of what's covered vs. gap, in plain language
3. **Recommendation feed** — 2–3 cards, each with a one-line plain-English summary
4. **Policy detail** — coverage, exclusions, and price with an "Ask AI" affordance
5. **Purchase form (pre-filled)** — shows what's auto-pulled vs. editable
6. **Payment confirmation**
7. **Unified Dashboard** — all policies (IndusInd + linked external), color-coded by renewal urgency
8. **Add/Link policy flow** — insurer selection + document upload
9. **Renewal nudge (WhatsApp mock)** — pre-filled quote, one-tap pay
10. **Claim initiation** — policy selector
11. **Self-inspection capture** — guided video/photo instructions
12. **Claim status tracker** — plain-language stage progress bar

Design principles applied throughout:
- **No insurance jargon on primary screens** — technical terms only appear behind an "Ask AI" tap, never as the default label
- **Progress and status are always visible** — especially in claims, where anxiety is highest and silence is the biggest trust-breaker
- **Every form is pre-filled where the bank already has the data** — this is the structural advantage over every competitor studied

---
