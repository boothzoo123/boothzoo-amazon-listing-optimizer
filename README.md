# Amazon Listing Optimizer
**An open-source AI skill for generating conversion-optimized Amazon listings**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Compatible](https://img.shields.io/badge/Works%20with-Claude%20%7C%20ChatGPT%20%7C%20Gemini%20%7C%20Grok-blue)]()
[![Market](https://img.shields.io/badge/Market-US%20Amazon-orange)]()

---

## What It Does

Paste this skill into any AI's system prompt and it becomes a senior Amazon operator — generating full, ready-to-upload listings with the strategic logic of someone who has managed PPC, traffic structure, competitive positioning, and review velocity, not just copywriting.

**Every output includes:**
- ✅ Title (primary + A/B alternate)
- ✅ 5 Bullet Points (architected by conversion job, not random order)
- ✅ Product Description (Hook → Proof → CTA structure)
- ✅ Backend Search Terms (250-byte, bucketed by keyword type)
- ✅ 5 Q&As (written in real buyer voice, objection-first)
- ✅ Inline annotations explaining **why** every sentence was written that way
- ✅ Listing Health Score across 6 dimensions
- ✅ Compliance Scan (FTC / Amazon restricted claims)
- ✅ Operator Strategy: variant architecture, review velocity, refresh triggers
- ✅ Fine-tuning recommendations + 30-day post-launch checklist

---

## How To Use

### Option 1 — Claude Project (Recommended)
1. Open [Claude.ai](https://claude.ai) → Create a new **Project**
2. Go to **Project Instructions** → paste the full contents of `SKILL.md`
3. Start a new conversation in the project
4. The SOP guide will appear automatically on first use

### Option 2 — ChatGPT Custom GPT
1. Go to [ChatGPT](https://chat.openai.com) → **Explore GPTs** → **Create**
2. In the **Instructions** field → paste the full contents of `SKILL.md`
3. Save and start chatting

### Option 3 — Any AI with System Prompt Support
Paste `SKILL.md` contents into the system prompt field.
Works with: Claude, GPT-4o, Gemini, Grok, Mistral, DeepSeek, and others.

### Option 4 — API / Agent Integration (OpenClaw, Dify, n8n, Coze)
Use `SKILL.md` as the system prompt for a dedicated listing-generation agent node.
Connect to Feishu/Lark, WhatsApp, or any messaging platform for team workflow automation.

---

## Recommended Workflow (Best Results)

The skill works in two modes:

| Mode | What you provide | Output quality |
|---|---|---|
| **Inference mode** | Product basics only | ~55% — full structure, inferred keywords |
| **Data mode** | Keywords + competitor listings + reviews | ~85% — production-ready |

**For data mode, prepare these 3 inputs before starting:**

**Step 1 — Keyword data** (10 min)
Run your target ASIN or product category in Helium10 / DataDive / SellerSprite
Export Top 30–50 high-volume keywords → paste directly into the chat

**Step 2 — Competitor listings** (3 min)
Copy title + bullet points from 2–3 top competitors
The AI will identify positioning gaps they're all missing

**Step 3 — Review intelligence** (2 min)
Collect top 3 praise themes + top 3 complaint themes from your reviews (or competitor reviews)
This is the highest-ROI input — real buyer language goes directly into bullet points and Q&A

---

## Example Outputs

See the `/examples` folder for real generated listings with full annotations:
- 📱 [Wireless Charger](examples/wireless-charger.md) — Electronics, $25, new launch
- 🕶️ [Polarized Sunglasses](examples/sunglasses.md) — Sports & Outdoors, $28–35
- 🍳 [Cast Iron Wok](examples/cast-iron-wok.md) — Kitchen, $45, repositioning

---

## Algorithm Coverage

| Signal | Coverage |
|---|---|
| **A9 Search Ranking** | Keyword placement priority, CVR→rank feedback loop, exact-match weighting |
| **Rufus AI Shopping** | Use-case anchoring, conversational query structure, Q&A indexing |
| **Conversion Rate** | Pain-before-solution hooks, specificity over adjectives, objection pre-emption |
| **Compliance** | FTC claims, Amazon restricted terms, category-specific rules |

---

## Iteration Commands

Once a listing is generated, use these commands to refine:

| Command | Action |
|---|---|
| `rewrite [section]` | Rewrite one section with new direction |
| `more [tone]` | Adjust tone: technical / premium / casual / aggressive |
| `add keyword: [word]` | Weave new keyword in naturally |
| `a/b version` | Generate split-test variant (one variable only) |
| `localize: [UK/CA/DE/JP]` | Adapt for other Amazon markets |
| `translate: CN` | Chinese reference version for internal team |
| `gift version` | Reframe for gift-buyer persona |
| `defend: [complaint]` | Update listing to address new review pattern |
| `score only` | Run health score + compliance scan on existing listing |

---

## Skill Architecture

```
FIRST USE          → SOP guide (auto-triggers on first message)
PHASE 0            → Situation diagnosis (new / rewrite / optimize)
PHASE 1            → Context collection (required + optional inputs)
PHASE 2            → Competitive gap matrix (if ASINs provided)
PHASE 3            → Full listing generation with inline annotations
PHASE 4            → Listing health score (6 dimensions, /60)
PHASE 5            → Compliance scan (FTC / Amazon policy)
PHASE 6            → Operator strategy (variants / reviews / refresh)
PHASE 7            → Iteration menu
PHASE 8            → Fine-tuning recommendations + 30-day checklist
OPERATOR REFERENCE → A9, Rufus, copywriting, category intelligence
```

---

## Contributing

PRs welcome. High-value contributions:
- Category-specific rule additions (Beauty, Automotive, Grocery, etc.)
- Additional market localizations (UK, DE, JP, CA)
- Example listings for more product categories
- Translations of the SOP prompt (currently Chinese/English)

---

## License

MIT License — free to use, modify, and distribute.
See [LICENSE](LICENSE) for details.

---

*Built for cross-border Amazon sellers. Optimized for the US market.*
*Contributions from the seller community welcome.*
