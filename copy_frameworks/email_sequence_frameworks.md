# Cold Email Copy Frameworks

These frameworks guide Claude when writing personalized cold email sequences in Step 4. Customize or add your own proven templates. The goal is not generic emails — it is hyper-personalized messages that feel 1:1.

---

## ✍️ Core Principles

1. **One idea per email.** Don't cram multiple value props into one message.
2. **Lead with them, not you.** The first sentence should be about the prospect, not your product.
3. **Merge tags are mandatory.** Every email must use `{{first_name}}`, `{{company_name}}`, and at least one custom `{{personalization_line}}`.
4. **Short > Long.** Aim for 50–100 words per email. Busy decision makers don't read essays.
5. **One CTA.** Ask for one thing (a reply, a meeting, a yes/no).

---

## 📧 4-Step Sequence Structure

| Step | Day | Goal | Tone |
|------|-----|------|------|
| Email 1 | Day 1 | Spark curiosity, make it about them | Warm, direct |
| Email 2 | Day 3 | Add value (case study, stat, insight) | Helpful |
| Email 3 | Day 7 | Different angle or objection handle | Honest |
| Email 4 | Day 12 | Break-up email (last attempt) | Light, brief |

---

## 🧩 Framework 1 — Observation + Problem + Solution

**Best for:** Specific pain points you've identified from research

```
Subject: {{personalization_line}} — quick thought

Hi {{first_name}},

[OBSERVATION about their company or work — specific, shows you did research]

[PROBLEM that observation implies — one sentence]

[HOW YOUR PRODUCT SOLVES IT — one sentence, no fluff]

Worth a quick chat?

[YOUR FIRST NAME]
```

**Example personalization_line:** `saw {{company_name}} is hiring 3 editors`

---

## 🧩 Framework 2 — Result-Led (Social Proof)

**Best for:** Follow-up email (Day 3) or when you have strong proof

```
Subject: How [SIMILAR COMPANY TYPE] saved [X hours/dollars]

Hi {{first_name}},

Following up — wanted to share a quick win:

[SIMILAR CUSTOMER TYPE] used [YOUR PRODUCT] to [SPECIFIC RESULT] in [TIMEFRAME].

Given {{company_name}} [does what they do], I thought this might resonate.

Happy to show you how it works in 15 minutes — would that be useful?

[YOUR FIRST NAME]
```

---

## 🧩 Framework 3 — Contrarian / Reframe

**Best for:** Day 7, when they've gone quiet

```
Subject: Not another "just checking in"

Hi {{first_name}},

Most [THEIR ROLE]s I talk to think [COMMON BELIEF]. 
The ones seeing the best results think the opposite.

[YOUR PRODUCT] is built around that second mindset.

If that's interesting, I'll send over a 2-min demo — if not, totally fine.

[YOUR FIRST NAME]
```

---

## 🧩 Framework 4 — Break-Up

**Best for:** Day 12, final email

```
Subject: Closing the loop, {{first_name}}

Hi {{first_name}},

I've reached out a few times — I'll take the silence as a "not right now" and won't bother you again.

If things change and [THE PROBLEM YOUR PRODUCT SOLVES] becomes a priority, I'm here.

Best,
[YOUR FIRST NAME]
```

---

## 🛠 Merge Tag Reference

| Tag | Description | Source |
|-----|-------------|--------|
| `{{first_name}}` | Prospect's first name | contacts.csv |
| `{{company_name}}` | Their company | contacts.csv |
| `{{title}}` | Their job title | contacts.csv |
| `{{personalization_line}}` | Custom research line | Claude generates from web research |
| `{{product_name}}` | Your product name | CLAUDE.md |
| `{{pain_point}}` | Specific pain point identified | scoring/icp_rubric.md |

---

## ✅ Copy Checklist (Claude should verify before saving)

- [ ] First sentence mentions the prospect or their company specifically
- [ ] No jargon, buzzwords, or filler phrases ("synergy", "leverage", "circle back")
- [ ] Under 100 words per email
- [ ] All merge tags from the Merge Tag Reference are used at least once across the sequence
- [ ] Subject lines are 6 words or fewer
- [ ] 2 subject line variants per step
- [ ] CTA is a simple yes/no or reply request
