# IndusInd Bank — Unified Insurance Platform
### Product Execution Section | Capstone Submission — E-Cell IIT Guwahati x IndusInd Bank

---

## 1. Success Metrics & North Star Metric

### North Star Metric

> **Active Protected Customers (APC): 1 Lakh IndusInd customers with at least one policy actively tracked or purchased on the platform, by Month 6 post-launch.**

I chose "Active Protected Customers" over a pure revenue or premium number for the same reason a marketplace tracks bookings, not GMV alone — it's the earliest true signal that the platform is doing its actual job: getting an existing bank customer covered and keeping them engaged with that cover, not just completing a one-time sale. Premium revenue is a lagging output of this; APC is the leading behavior.

**Why this metric and not an alternative:**
- *Not* "policies sold" — because a policy sold and never revisited is exactly the reactive, one-time-transaction problem this platform exists to fix.
- *Not* "app downloads" — vanity metric, doesn't capture protection or trust.
- APC requires the customer to have taken a real action (buy, or link an existing policy for tracking) — so it captures both cross-sell (new premium) and the "unified dashboard" value prop (linking non-IndusInd policies), which matters because linking builds daily-relevance habit even before a sale happens.

### Supporting Metric Tree

| Layer | Metric | Target (Month 6) |
|---|---|---|
| **Acquisition** | % of active digital-banking users who view a recommendation | 25% |
| **Activation** | % of viewers who buy or link ≥1 policy | 15% (→ ~1L APC off a ~7M digital-active base assumption) |
| **Engagement** | Monthly active use of the insurance dashboard (post-purchase) | 30% of APC |
| **Retention** | Renewal rate at policy expiry | 70%+ (vs. industry claims-driven churn baseline) |
| **Trust/Claims** | Claims filed digitally end-to-end (no branch/paper touch) | 80% |
| **Claims speed** | Median time to claim resolution for eligible motor/health claims | Under 48 hours |
| **Cross-sell depth** | Avg. policies per APC by Month 12 | 1.4 |

I'm intentionally keeping Claims Speed and Digital Claims % as first-class metrics, not afterthoughts — the market research is unambiguous that claims experience is the actual retention lever, and a platform that nails acquisition but fumbles claims will bleed exactly the customers it worked hardest to win.

---

## 2. GTM Strategy

### Phase 1 — Warm base activation (Month 0–3)
The unlock a bank has that no insurtech does: an existing, trusting, logged-in-weekly customer base. I'm sequencing GTM to spend that advantage first, before touching cold acquisition.

- **In-app nudges inside the existing IndusInd banking app** — a non-intrusive "Protection Score" card on the home screen (e.g., "You're 40% protected based on your profile") that opens into the insurance module. This reuses existing engagement rather than fighting for a new app install.
- **Moment-based embedding**: insurance offers triggered at contextually relevant banking events —
  - Personal/auto loan disbursal → motor or credit-life cover prompt
  - New salary account activation → starter health/accident micro-cover (this is where Farhan, the secondary persona, enters)
  - Large debit card spend abroad detected → travel insurance prompt
- **Relationship manager (RM) assisted push** for premium/priority banking segments, who trust a human nudge more than an app pop-up — RMs get a simple dashboard flagging which of their customers are "uninsured" or "under-protected."

### Phase 2 — Habit + trust building (Month 3–6)
- Launch the **"Link Your Existing Policies"** feature aggressively — even non-IndusInd insurance policies pulled into one dashboard. This is a trust-building, non-monetizing feature deliberately placed early: it proves the platform's value before asking for a purchase, mirroring how aggregators build initial engagement without commission pressure.
- WhatsApp-based renewal nudges (proven pattern from Digit/Acko) roll out here, timed 14 days pre-expiry with a pre-filled renewal quote and one-tap payment.
- First cohort of digital claims (InstaSpect/self-inspection style) go live for motor, since that's the highest-frequency, most demo-able claims moment.

### Phase 3 — Ecosystem expansion (Month 6–12)
- Layer in the ecosystem integrations named in the brief — roadside assistance, teleconsultation, home assistance — as **retention perks bundled into policies**, not separate purchases. This is how ICICI Lombard's IL TakeCare keeps daily relevance even when no one has an active claim.
- Open a **Tier-2 city push** (Lucknow-style markets) using vernacular-language chat support, since language and literacy — not lack of demand — are the real barrier to insurance penetration outside metros.
- Introduce light referral mechanics off the back of fast claims experiences — the same organic-referral effect that Digit and Acko see from same-day claim resolutions.

### Channel prioritization (not "which channel first" but "which channel earns the right to scale first")
1. Owned: in-app banking nudges (Day 1, near-zero CAC)
2. Owned: RM-assisted for premium segments (Day 1, high-trust, low-scale)
3. Earned: WhatsApp renewal + referral loops (Month 3+, scales with claims quality)
4. Paid: only after Phase 2 proves activation and retention hold — no reason to buy expensive cold traffic before the warm base is converted

---

## 3. Product Roadmap

**Guiding principle:** ship the trust-building, low-monetization features early (linking, dashboard, education), and layer in monetizing features (cross-sell, bundled add-ons) once engagement habits exist — reversing the instinct to lead with the sales funnel.

### Q1 — Foundation
- Unified insurance dashboard (view-only + link existing policies from other insurers)
- Protection Score home-screen card in the banking app
- Basic policy discovery flow using existing KYC/banking data for pre-fill
- Core motor + health cross-sell purchase flow

### Q2 — Trust & Retention
- WhatsApp/app renewal reminder engine (14-day and 3-day nudges)
- Digital claims MVP: self-inspection video upload for motor, real-time status tracker
- RM dashboard for premium-segment nudging
- Vernacular language support (Hindi + 1 regional language) for chat-based product explanations

### Q3 — Ecosystem & Depth
- Bundled ecosystem perks: roadside assistance, teleconsultation, home-assistance partner integrations
- Starter micro-policy auto-offer at salary-account onboarding (Farhan persona)
- AI-powered insurance education assistant (plain-language Q&A: "what does my policy actually cover?")
- Expansion to travel and device/cyber insurance categories

### Q4 — Scale & Intelligence
- Personalization engine: life-stage-triggered recommendations (marriage, new child, home purchase signals from banking data, consented)
- Fraud-detection layer on claims (pattern flags before payout, not customer-facing friction)
- Tier-2 city geo-expansion campaign
- Referral program tied to fast-claim NPS

---

## 4. Assumptions & Risks

### Key Assumptions
- IndusInd Bank customers are comfortable with the bank using existing financial/KYC data to power insurance recommendations, provided consent and transparency are clear upfront
- A meaningful share of customers currently hold policies with *other* insurers and would be willing to link them into a bank dashboard even without switching insurers
- IRDAI's Bima Sugam and Use-and-File reforms continue to ease product launch speed rather than reversing toward stricter pre-approval
- The bank can secure claims-processing partnerships/SLAs with underlying insurer(s) fast enough to hit the sub-48-hour claims target — this is not fully within the platform team's control since IndusInd General Insurance still depends on network hospitals/garages and surveyor partners

### Key Risks

| Risk | Why it matters | Mitigation direction |
|---|---|---|
| **Data privacy backlash** | Using banking data for insurance recommendations could feel invasive if not opt-in and transparent | Explicit consent flows, visible "why am I seeing this" explanations, easy opt-out |
| **Claims execution gap** | Every competitor's biggest weakness is claims reliability (buggy uploaders, slow surveyors) — if IndusInd's claims experience isn't genuinely faster, the whole retention thesis collapses | Start with motor self-inspection (proven pattern) before expanding to more complex health claims; hold Q2 launch until sub-48-hour SLA is demo-able |
| **Low initial trust in bank-as-insurer** | Customers may still default to buying insurance the way they always have (agent, employer, aggregator) rather than switching habits | Lead GTM with the free, non-monetizing "link your policies" feature to earn trust before asking for a purchase |
| **Channel cannibalization internally** | RM-driven insurance sales already exist informally at some banks; a digital platform could create internal channel conflict | Position the platform as an RM enablement tool (the dashboard flags leads for RMs), not a replacement |
| **Regulatory dependency** | Multi-insurer aggregation and cross-sell are shaped by IRDAI rules on corporate agency/broking licenses, which can change | Legal/compliance review baked into Q1 before deeper multi-insurer linking ships |
| **Underestimating Tier-2 language/literacy barrier** | Insurance jargon is already a stated blocker even in English-fluent metros; Tier-2 expansion without genuine vernacular design risks low adoption | Vernacular support ships in Q2, ahead of the Q3 geo-expansion push, not as an afterthought |

---

*This closes out Product Execution. Ready for Product Design (user journey, key flows, feature prioritization, wireframes/prototype walkthrough) whenever you want to move forward.*
