# IndusInd Bank — Unified Insurance Platform
### Bonus Section | Capstone Submission — E-Cell IIT Guwahati x IndusInd Bank

---

## 1. AI-Powered Experiences

I'm scoping AI into three customer-facing roles, each tied to a specific trust or friction problem identified in the research — not AI for its own sake.

**a) Plain-Language Insurance Assistant**
A conversational layer sitting on every policy detail and claims screen, answering questions like "what does co-pay mean?" or "is this covered if I'm hospitalized for dengue?" in simple language, grounded in the actual policy wording (not generic insurance knowledge) so answers are accurate to what Priya bought. This directly targets the jargon problem flagged as a top reason customers disengage from insurance.

**b) Recommendation Engine**
Uses existing, consented banking signals — income band, loan/EMI activity, card spend categories, life-stage proxies like a new home loan or a large travel booking — to suggest the right cover at the right moment, instead of a generic 20-question intake form. This is the single biggest structural advantage a bank has over Digit, Acko, or Policybazaar, none of whom start with this data.

**c) AI-Assisted Claims Triage**
For motor claims, a computer-vision layer reviews the self-inspection video to estimate damage severity and route: minor, clearly-covered damage goes to fast-track approval; ambiguous or high-value damage routes to a human surveyor. This mirrors the pattern Digit pioneered with AI-assessed self-inspection claims, and is the mechanism that makes the sub-48-hour claims target operationally realistic rather than aspirational.

---

## 2. Claims Automation

Claims is the single highest-leverage investment area — the research is unambiguous that a bad claims experience is the top driver of non-renewal industry-wide, so I'm treating automation here as a retention system, not a cost-cutting exercise.

**Automated flow for motor (fast-track path):**
1. Customer opens "File a Claim" → selects policy
2. Guided self-inspection: app walks them through capturing front, sides, and damage close-up
3. Computer vision model estimates damage severity and cross-checks against policy coverage terms
4. If damage is minor and clearly covered → auto-approved, payout to network garage initiated within hours
5. If damage is major, ambiguous, or a potential fraud flag → routed to human surveyor with the video pre-attached (removing the "wait for a visit" step entirely, since the surveyor reviews footage first)

**Automated flow for health (documentation-assist path):**
- OCR-based document intake — customer photographs hospital bills/discharge summary, system extracts and pre-fills the claim form rather than requiring manual entry
- Real-time status tracker with plain-language stage labels, replacing the black-box "under process" status that drives the most claims-related anxiety

**What I'm deliberately not automating in v1:** full end-to-end approval for high-value or complex health claims — these still route to a human. Over-automating claims decisions before the model is proven erodes exactly the trust this platform is trying to build.

---

## 3. Fraud Detection Concepts

Fraud detection needs to be invisible to legitimate customers and only ever add friction for genuinely suspicious patterns — a fraud layer that slows down honest claims defeats the entire claims-speed thesis.

**Signal-based flagging (not customer-facing):**
- Claim frequency anomalies (e.g., multiple claims across policies in a short window)
- Video/document inconsistencies (metadata mismatches, signs of image manipulation, timestamps inconsistent with the reported incident)
- Behavioral signals from banking data already available to the bank — e.g., a claim inconsistent with the policyholder's actual usage pattern (a "stolen vehicle" claim on a vehicle with recent toll/FASTag activity)
- Network-level pattern detection — the same garage or hospital appearing disproportionately across flagged claims

**Design principle:** flags trigger additional human review, not automatic denial. False positives that block or delay a genuine claim are reputationally worse than a small amount of fraud leakage, given how central claims trust is to this platform's retention thesis.

---

## 4. Personalization Engine

Building on the recommendation engine in Section 1, the personalization layer is what keeps the platform relevant between transactions — the "daily relevance" gap identified in the competitive research (customers otherwise only open an insurance app when something breaks).

**Triggers driving personalization (all consent-gated):**
- Life-stage signals: new home loan → home insurance nudge; marriage-linked joint account → life/health bundle suggestion; new dependent added to health declarations → family floater upsell
- Spend-pattern signals: recurring high-value electronics purchases → device insurance; frequent international card usage → travel cover
- Protection Score decay: if a linked external policy is nearing expiry and hasn't been renewed, the score visibly drops, creating a gentle, non-nagging nudge to act

**Guardrail:** personalization should feel like a bank that knows you, not a bank that's watching you — every recommendation includes a visible "why am I seeing this" explanation, and customers can turn off specific signal categories without losing core functionality.

---

## 5. Monetization Strategy

Three revenue layers, sequenced to match the roadmap's trust-first philosophy:

| Layer | Mechanism | When it activates |
|---|---|---|
| **Direct premium (core)** | Commission/margin on policies sold directly through the platform (IndusInd General Insurance underwritten products) | Day 1 |
| **Cross-sell & bundling** | Ecosystem perks (roadside assistance, telemedicine) bundled into premium tiers, increasing average premium per policy without a separate purchase | Q3 (once base engagement is proven) |
| **Referral/affiliate on linked policies** | Where a customer links a competitor's policy for tracking, the platform can (with disclosure) offer a switch-and-save comparison at the customer's next renewal — monetizing the trust built through the free linking feature | Month 9+, only after linking adoption is meaningfully high |

**Deliberately not monetizing in v1:** the "link your policies" feature and the Protection Score itself stay commission-free and ad-free indefinitely — these are trust infrastructure, and monetizing them directly would undercut the exact advantage (bank-native trust) the whole platform is built on.

---

## 6. Technical Architecture (High-Level)

I'm keeping this at a PM-appropriate level of abstraction — directionally correct, not an engineering spec.

```
                    ┌─────────────────────────┐
                    │   IndusInd Banking App    │
                    │  (existing shell + new    │
                    │   Insurance module)       │
                    └────────────┬────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   Insurance Platform      │
                    │   API Gateway             │
                    └──┬─────────┬───────────┬─┘
           ┌───────────┘         │           └────────────┐
┌──────────▼─────────┐ ┌─────────▼────────┐ ┌─────────────▼──────────┐
│ Recommendation &     │ │ Policy & Claims   │ │ Partner Insurer         │
│ Personalization      │ │ Management        │ │ Integration Layer       │
│ Engine (reads        │ │ Service (unified   │ │ (APIs to IndusInd Gen.  │
│ consented banking     │ │ dashboard, linking,│ │ Insurance + external    │
│ data via internal      │ │ renewal engine)    │ │ insurers for linking)   │
│ data platform)        │ │                    │ │                         │
└──────────────────────┘ └─────────┬──────────┘ └─────────────────────────┘
                                    │
                         ┌──────────▼───────────┐
                         │ Claims AI Layer        │
                         │ (self-inspection CV,   │
                         │  OCR document intake,   │
                         │  fraud signal scoring)  │
                         └────────────────────────┘
```

**Key architectural principles:**
- The recommendation engine reads from the bank's existing data platform through a consented, permissioned interface — it does not duplicate or independently store sensitive banking data
- The Partner Insurer Integration Layer is what makes "linking" possible — a lightweight API/document-ingestion contract with major insurers (or manual OCR fallback where no API exists) so the unified dashboard genuinely works across providers, not just IndusInd's own products
- Claims AI is a separate service from core policy management, so a change to the vision model doesn't risk destabilizing renewal or payment flows

---

## 7. Data & Analytics Instrumentation

To make the North Star Metric and supporting metric tree (from the Execution section) actually trackable, the platform needs event-level instrumentation from day one, not retrofitted later.

**Core events to instrument:**
- `protection_score_viewed`, `recommendation_shown`, `recommendation_clicked` — funnel from awareness to consideration
- `policy_purchased`, `policy_linked` — the two paths to becoming an Active Protected Customer
- `dashboard_session` (post-purchase) — engagement/habit tracking
- `renewal_nudge_sent`, `renewal_completed`, `renewal_lapsed` — retention funnel
- `claim_filed`, `claim_ai_reviewed`, `claim_approved`, `claim_payout_initiated`, `claim_resolved` — full claims funnel with timestamps at each stage, which is what makes the sub-48-hour SLA measurable rather than aspirational
- `fraud_flag_raised`, `fraud_flag_reviewed` — for tuning the fraud model's false-positive rate over time

**Why this matters for the metrics I committed to:** claims speed and digital claims % are core targets in the Execution section, but they're unmeasurable without stage-level timestamps on every claim — this instrumentation is what turns "claims resolved under 48 hours" from a marketing promise into an operational number the team can actually track weekly and be held to.

---
