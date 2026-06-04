# 🚀 AI Cold Email Pipeline with Claude Code

A fully automated outbound pipeline powered by [Claude Code](https://docs.anthropic.com/claude/claude-code). This repo gives you the exact folder structure, `CLAUDE.md` brain template, ICP scoring rubric, API documentation setup, and cold email frameworks to go from zero → personalized sequences loaded into your sequencer — using plain English prompts.

> Based on the workflow from [Manthan | Lead Gen Man](https://www.youtube.com/@LeadGenMan)

---

## 📁 Folder Structure

```
ai-cold-email-pipeline/
├── CLAUDE.md                      # Campaign brain — Claude reads this at every session
├── .env.example                   # API key template
├── README.md
│
├── scoring/
│   └── icp_rubric.md              # ICP scoring rubric (customize for your offer)
│
├── api_docs/
│   ├── apollo_api_docs.md         # Apollo.io API reference snippets
│   └── sequencer_api_docs.md      # Your cold email tool (Saleshandy / Smartlead / Instantly)
│
├── copy_frameworks/
│   └── email_sequence_frameworks.md  # Cold email copy frameworks & templates
│
├── output_examples/
│   └── example_campaign.md        # Example of a successful campaign for Claude to reference
│
└── output/                        # Claude writes all CSVs here (git-ignored)
    └── .gitkeep
```

---

## ⚡ Quick Start

### Step 1 — Clone and open in Claude Code
```bash
git clone https://github.com/HDG1023/ai-cold-email-pipeline.git
cd ai-cold-email-pipeline
```

Then in Claude Code:
```
Clone this repo at [path] and fill in my business details, offer, and ICP inside CLAUDE.md
```

### Step 2 — Add your API keys
Copy `.env.example` to `.env` and fill in your keys:
```bash
cp .env.example .env
```
Then tell Claude Code:
```
Read my .env file and store the API keys for Apollo and [your sequencer]
```

### Step 3 — Run the pipeline with prompts
Paste these prompts into Claude Code in order:

**1. Build lead list**
```
Build a company lead list using Apollo for [YOUR ICP, e.g. video editing agencies] in [LOCATION] with [X]+ employees. Save to output/companies.csv
```

**2. Score companies**
```
Apply the ICP scoring rubric from scoring/icp_rubric.md to output/companies.csv. Research each company online and score them. Save results with tier labels to output/scored_companies.csv
```

**3. Find decision makers**
```
For all Tier 1 companies in output/scored_companies.csv, find decision makers and their verified emails using Apollo. Save to output/contacts.csv
```

**4. Write personalized sequences**
```
Using the frameworks in copy_frameworks/email_sequence_frameworks.md and data in output/contacts.csv, write a 4-step personalized cold email sequence for each contact. Day 1, Day 3, Day 7, Day 12. Include merge tags. Save to output/sequences.csv
```

**5. Deploy to sequencer**
```
Create a new sequence named "[CAMPAIGN NAME]" in [your tool] and add all prospects from output/contacts.csv with their email copies from output/sequences.csv
```

---

## 🛠 Tools Stack

| Tool | Purpose | Link |
|------|---------|------|
| **Apollo.io** | Lead enrichment & decision maker data | [apollo.io](https://apollo.io) |
| **Saleshandy** | Cold email sequencer | [saleshandy.com](https://saleshandy.com) |
| **Smartlead** | Alternative sequencer | [smartlead.ai](https://smartlead.ai) |
| **Instantly** | Alternative sequencer | [instantly.ai](https://instantly.ai) |
| **Maildoso** | Email infrastructure (domains, mailboxes, warm-up) | [maildoso.com](https://maildoso.com) |
| **Claude Code** | The AI brain running everything | [claude.ai](https://claude.ai) |

---

## 💡 Why This Beats Clay

| | This Pipeline | Clay |
|---|---|---|
| ICP Scoring | Free Python script (any size) | Costs credits per row |
| Copy Generation | Uses your existing Claude plan | External API cost per row |
| Learning curve | Plain English prompts | Must learn Clay tables & filters |
| Sequencer | Works with any tool via API | Limited integrations |
| Monthly cost | ~$79–$249 total | $395+/month for webhooks & API |

---

## 📊 Pricing Reference

- **Apollo**: $59–$149/month
- **Saleshandy**: ~$70/month (150k emails)
- **Claude**: $20–$200/month

---

## 📄 License

MIT — use freely, customize for your business.
