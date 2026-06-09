# stg-collaboration-evaluator

Inbound Collaboration & Sponsorship Evaluator

A folder-based AI operator that acts as an executive gatekeeper for all inbound partnership, sponsorship, and collaboration pitches.

## What This Operator Does

When you paste a raw pitch email or contact form submission into the Claude Project chat, this operator:

1. **Detects spam and vague blasts** instantly
2. **Scores brand alignment** against 5 faith-and-values pillars
3. **Scores aesthetic match** against 5 visual-design markers
4. **Applies hard commercial thresholds** (budget, audience size, engagement)
5. **Returns exactly one decision** out of four: `[APPROVE & SCHEDULE]`, `[COUNTER-OFFER]`, `[DEAL-BREAKER ARCHIVE]`, or `[ESCALATE TO HUMAN]`
6. **Outputs a copy-pasteable email draft** or internal flag for your records

No babysitting. No "what do you think?" The operator decides and drafts.

---

## How to Use

1. Create a new **Claude Project** at [claude.ai](https://claude.ai).
2. Drag this entire folder into the project files panel.
3. In the chat, paste the raw text of an inbound pitch email or contact form submission.
4. Claude will read `identity.md`, `rules.md`, and `reference/brand_alignment_rubric.md`, execute the sequential gates, and return the exact decision block and template.

---

## Folder Structure

This operator follows the Interpretable Context Methodology: the folder *is* the application. Each file has one job. Claude reads them in a strict sequence dictated by the routing logic in `rules.md`.

s2g-collaboration-evaluator/
├── identity.md                          # Layer 1: The Map — who the operator is
├── rules.md                             # Layer 2: The Engine — sequential gates
├── examples.md                          # Layer 3: Proof — tested scenarios
├── reference/
│   ├── brand_alignment_rubric.md        # Absolute truth source for scoring
│   └── response_templates.md            # Copy-pasteable communication assets
└── README.md                            # You are here — the floor plan

### File Responsibilities

| File | Job | When Claude Reads It |
|------|-----|----------------------|
| `identity.md` | Defines the operator's role, scope, and voice. Sets the zero-babysitting mandate. | **First.** Every time. |
| `rules.md` | Contains the sequential decision gates (IF/THEN/UNLESS). This is the routing engine. | **Second.** After identity is loaded. |
| `reference/brand_alignment_rubric.md` | The 5-point pillar system, 5-point aesthetic system, and prohibited elements list. | **On demand.** Only when Gate 2 or Gate 3 is reached. |
| `reference/response_templates.md` | The exact email drafts and internal flags for each final status. | **On demand.** Only after a final status is assigned. |
| `examples.md` | Four proven scenarios showing exact inputs and outputs. Serves as few-shot calibration. | **Reference.** Claude may scan this to calibrate tone and format. |

### Token Conservation

The `rules.md` explicitly tells Claude which reference files to read and which to skip based on the pitch type. This prevents token waste:

| Pitch Type | Reads | Skips |
|------------|-------|-------|
| Paid Brand Sponsorship | `brand_alignment_rubric.md` | `response_templates.md` (until status is assigned) |
| Free Product Exchange | `brand_alignment_rubric.md` | — |
| Spam / Off-Brand Blast | **Nothing** | **All files** — immediate exit |
| Values-Aligned / Low Budget | `brand_alignment_rubric.md` | — |

---

## The Decision Engine

The operator runs **5 sequential gates**. A pitch must survive each gate to reach the next. There are no loops, no clarifying questions, and no "maybe."

### Gate 1: Spam & Vague Blast Detector
Catches generic mass blasts, SEO link scams, and placeholder language. If triggered → `[DEAL-BREAKER ARCHIVE]`. Immediate exit.

### Gate 2: Brand Alignment Scorer
Scores the pitch on 5 pillars: Christian faith, intentional living, reflective journaling, caregiver/grief support, minimalist design. If score is 0–2 → Archive. If 3–5 → proceed.

### Gate 3: Aesthetic & Values Match
Scores the pitch on 5 aesthetic markers tied to the S2G brand palette (sage green, slate blue, lavender, ivory, light grey) and design language. Weak aesthetic + free ask = Archive. Weak aesthetic + paid ask = proceed to Gate 4.

### Gate 4: Commercial & Operational Metrics
Applies hard thresholds:
- **Paid sponsorship:** Budget must be ≥ $300.
- **Free product exchange:** Audience ≥ 5,000 followers OR ≥ 3,000 email subscribers OR ≥ 3% engagement.
- **Joint venture:** Always escalates to human (IP/revenue risk).
- **Podcast guest invite:** Approved only if audience matches S2G pillars.

### Gate 5: Edge Cases & Exception Handling
- **High-Aesthetic, Low-Budget:** If alignment = 5/5 and aesthetic = 5/5 but no budget, escalate to human with a relational draft.
- **Direct Competitor:** If sender is in the exact faith-journal niche, escalate to human.
- **Missing Data:** If alignment is strong but metrics are missing, counter-offer with a clarification request.

---

## Output Format

Every evaluation ends with this exact block:

***
**OPERATOR DECISION SUMMARY**
- **FINAL STATUS:** [One of four statuses]
- **PRIMARY REASON:** [1-sentence deterministic logic match]
- **BRAND ALIGNMENT SCORE:** [X/5]
- **AESTHETIC SCORE:** [X/5]
- **FILE TARGET NAME:** [YYYY_MM_DD]_[BrandName]_Inbound_Triage.md
- **NEXT ACTION:** [Copy-paste response draft / Move to Archive / User Review Required]
- **TEMPLATE USED:** [TemplateName]
***

[Applicable Response Template or Escalation Note]

---

## Why This Operator Wins

1. **It makes decisions, not suggestions.** Every rule is an IF/THEN/UNLESS statement with hard numbers. There is zero "use your best judgment."
2. **It handles the messy stuff.** The "High-Aesthetic, Low-Budget" exception and "Direct Competitor" flag are encoded with specific conditions, not hand-waving.
3. **It conserves tokens.** The routing architecture tells Claude exactly which files to read and which to ignore, preventing context drift.
4. **It is built for a real business.** Thresholds ($300, 5k followers) reflect an early-stage faith-based brand with no social following yet, protecting founder time without missing genuine community connections.
5. **A stranger can use it.** Drop the folder in, paste a pitch, get a decision. No setup. No configuration.

---

## Submission Note

This operator was built for **Competition #7: The Operator** (Clief Notes / The Lyceum). It handles inbound collaboration and sponsorship triage end-to-end for a faith-based journal and digital product brand.

**Workflow:** Inbound pitch screening and routing  
**Decisions it makes:** Approve, counter-offer, archive, or escalate to human — with a copy-pasteable next-step asset every time.
