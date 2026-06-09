# Decision Rules & Routing Logic

Every input must pass through the gates in exact sequential order. Do not skip a gate. Do not ask the user for missing information. If data is missing, apply the rule for missing data exactly as written.

## Gate 1: Spam & Vague Blast Detector

**IF** the email subject or body contains generic placeholders (`Dear Admin`, `Dear Webmaster`, `Hi there`, `To whom it may concern`, `Love your site`, `your platform`)  
**AND** the sender fails to mention the exact brand name "Simplify to Glorify" or a specific S2G product (Prayer Journal, Gratitude Journal, Grief Journal, Caregiver Journal, Care Board)  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]`  
**AND** output: `No response required. File as spam.`  
**UNLESS** the sender explicitly references a specific blog post, product description, or brand value from simplifytoglorify.com. Then proceed to Gate 1B.

**IF** the email is clearly a mass-blast affiliate template (contains "we work with hundreds of creators," "our AI tool," "SEO partnership," "permanent link")  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]` immediately. Do not proceed.

## Gate 1B: Structural Genericism Check (Flattery Bypass Detector)

**IF** the pitch mentions one or more S2G brand pillars (intentional living, mindfulness, minimalist design, gratitude, faith, scripture, grief support, caregiver support)  
**AND** the pitch pairs those mentions with generic, mass-scalable deliverables (`backlinks`, `SEO partnership`, `portfolio of lifestyle sites`, `guaranteed impressions`, `content syndication`, `permanent do-follow link`, `link insertion`, `guest post`, `link placement`)  
**THEN** treat as a **vague blast regardless of keyword match**.  
**Assign:** `STATUS: [DEAL-BREAKER ARCHIVE]`  
**AND** output: `Flattery bypass detected. Keywords scraped but deliverables reveal mass-blast intent. No response.`

**IF** the pitch mentions brand pillars but provides **zero specific detail** about *which* product, *which* blog post, or *why* the alignment matters to their specific brand  
**AND** the sender's domain or past work is not verifiable via a clean portfolio link  
**THEN** reduce Brand Alignment Score by 2 points (minimum 0) before Gate 2 scoring.  
**RATIONALE:** Generic flattery without proof of understanding is a spam indicator, not alignment.

## Gate 2: Brand Alignment Scorer

Read the pitch against `reference/brand_alignment_rubric.md`. Score it on the 5-point Pillar System. Each pillar is binary (1 point if clearly present, 0 if absent or contradicted).

**Pillars:**
1. Christian faith integration or scripture-centered wellness
2. Intentional living, slow living, or mindfulness (non-New-Age)
3. Reflective journaling, prayer, gratitude, or structured organization
4. Caregiver support, grief support, or hospice/family care
5. Minimalist design aesthetic or human-centered storytelling

**IF** the pitch contradicts any Prohibited Element (crypto, gambling, dropshipping, MLM, adult content, manifesting/astrology/law-of-attraction, aggressive growth-hacking, "get rich quick")  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]` regardless of other scores.  
**AND** output: `Prohibited category detected. No response.`

**IF** Brand Alignment Score is 0, 1, or 2 out of 5  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]`  
**AND** apply the `Polite_Decline` template.

**IF** Brand Alignment Score is 3, 4, or 5 out of 5  
**THEN** proceed to Gate 3.

## Gate 3: Aesthetic & Values Match

Score the pitch on the 5-point Aesthetic System from the rubric. Use the **Text-Based Aesthetic Surrogates** in `reference/brand_alignment_rubric.md` to score text-only pitches accurately.

**Markers:**
1. References sage green, slate blue, lavender, ivory, or light grey palette
2. Mentions watercolor, organic, or hand-drawn motifs
3. Describes breathable layouts, white space, or calm simplicity
4. Uses minimalist typography or non-clinical tone
5. Centers human emotion, testimony, or quiet reflection over hype

**IF** Aesthetic Score is 0 or 1 out of 5  
**AND** the pitch is a paid sponsorship  
**THEN** proceed to Gate 4 (money can override weak aesthetic if alignment is strong).  
**IF** Aesthetic Score is 0 or 1 out of 5  
**AND** the pitch is a free exchange or collaboration  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]`.

**IF** Aesthetic Score is 2, 3, 4, or 5 out of 5  
**THEN** proceed to Gate 4.

## Gate 4: Commercial & Operational Metrics

Determine the ask type from the pitch text.

### Ask Type A: Paid Sponsorship
**IF** the brand explicitly states a budget  
**AND** budget is &gt;= $300  
**THEN** assign `STATUS: [APPROVE & SCHEDULE]`  
**AND** draft the `Onboarding_Response` template.

**IF** budget is stated and &lt; $300  
**THEN** assign `STATUS: [COUNTER-OFFER]`  
**AND** draft the `Rate_Card_Counter` template.

**IF** no budget is stated but the brand is established (mentions PR agency, prior campaigns, or recognizable name)  
**THEN** assign `STATUS: [COUNTER-OFFER]`  
**AND** draft the `Rate_Card_Counter` template requesting budget confirmation.

### Ask Type B: Free Product Exchange ("Send us free products for exposure")
**IF** the creator/brand offers "product for post," "gifted in exchange for content," or "review copy"  
**AND** their stated audience is &gt;= 5,000 Instagram followers OR &gt;= 3,000 email subscribers OR &gt;= 3% engagement rate  
**AND** Brand Alignment Score &gt;= 4  
**THEN** assign `STATUS: [APPROVE & SCHEDULE]`  
**AND** draft the `Product_Collab_Onboarding` template.

**IF** audience is below the threshold  
**AND** Aesthetic Score &gt;= 4  
**AND** Brand Alignment Score &gt;= 4  
**THEN** proceed to Gate 5 (High-Aesthetic Low-Budget Exception).

**IF** audience is below the threshold  
**AND** (Aesthetic Score &lt;= 3 OR Brand Alignment Score &lt;= 3)  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]`  
**AND** apply `Polite_Decline`.

### Ask Type C: Joint Venture, Bundle, or Cross-Promotion
**IF** the pitch proposes a bundle, shared launch, or co-created product  
**AND** the partner has an active, verifiable audience or customer base  
**AND** Brand Alignment Score &gt;= 4  
**THEN** assign `STATUS: [ESCALATE TO HUMAN]`  
**AND** draft the `Partnership_Flag` internal note.  
**REASON:** Bundles involve IP and revenue splits. Founder must review personally.

**IF** the partner has no verifiable audience or the proposal is vague ("let's collab")  
**THEN** assign `STATUS: [COUNTER-OFFER]`  
**AND** draft the `Clarification_Request` template asking for specifics.

### Ask Type D: Podcast Guest Pitch (Inbound to S2G)
**IF** the pitch invites the founder to appear on a podcast  
**AND** the podcast explicitly serves Christian women, caregivers, grieving families, or intentional living audiences  
**AND** the host provides episode length, format, and audience size  
**THEN** assign `STATUS: [APPROVE & SCHEDULE]`  
**AND** draft the `Podcast_Availability` template.

**IF** the podcast topic is generic business or "how to grow your brand" without faith or wellness angle  
**THEN** assign `STATUS: [DEAL-BREAKER ARCHIVE]`.

## Gate 5: Edge Cases & Exception Handling

### Exception 1: The "High-Aesthetic, Low-Budget" Community Partner
**IF** Aesthetic Score = 5 out of 5  
**AND** Brand Alignment Score = 5 out of 5  
**AND** (budget = $0 OR audience &lt; 5,000 OR no audience data provided)  
**AND** the sender is an independent creator, small print shop, local ministry, or solo blogger  
**THEN** assign `STATUS: [ESCALATE TO HUMAN]`  
**AND** draft the `Relational_Passion_Project` template.  
**DO NOT** archive. This is a potential brand ambassador.

### Exception 2: The "Direct Competitor" Conflict
**IF** the sender operates in the exact faith-based journal niche (e.g., Val Marie Paper, Cultivate What Matters, Prayerful Planner, Daily Grace Co.)  
**AND** the pitch is for cross-promotion or bundle  
**THEN** assign `STATUS: [ESCALATE TO HUMAN]`  
**AND** draft the `Competitor_Flag` internal note.  
**REASON:** Competitive intelligence requires founder discretion.

### Exception 3: Missing Data (Strict No-Guess Rule)
**IF** the pitch is fewer than 80 words  
**OR** the pitch contains no explicit mention of: budget, audience size, platform, timeline, or specific deliverables  
**THEN** the operator **must not** attempt to score Gates 2, 3, or 4.  
**Assign:** `STATUS: [COUNTER-OFFER]` immediately.  
**AND** draft the `Clarification_Request` template.  
**AND** output: `Insufficient data for scoring. Routing to clarification to prevent hallucination.`

**IF** the pitch is longer than 80 words but still omits budget AND audience AND timeline  
**AND** Brand Alignment Score from Gate 2 is &gt;= 3  
**THEN** assign `STATUS: [COUNTER-OFFER]` and request the missing metrics.  
**DO NOT** guess budget from industry norms.  
**DO NOT** infer audience size from vague phrases like `engaged community` or `growing following`.

## Execution Output Format

Every single evaluation must conclude with this exact markdown block:

***
**OPERATOR DECISION SUMMARY**
- **FINAL STATUS:** [Insert Status Here]
- **PRIMARY REASON:** [1-sentence deterministic logic match]
- **BRAND ALIGNMENT SCORE:** [X/5]
- **AESTHETIC SCORE:** [X/5]
- **FILE TARGET NAME:** [YYYY_MM_DD]_[BrandOrCreatorName]_Inbound_Triage.md
- **NEXT ACTION:** [Copy-paste response draft / Move to Archive / User Review Required]
- **TEMPLATE USED:** [TemplateName]
***
