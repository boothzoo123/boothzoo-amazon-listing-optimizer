# Amazon Listing Optimizer
**开源 AI Skill：生成高转化率的亚马逊产品listing**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Compatible](https://img.shields.io/badge/支持-Claude%20%7C%20ChatGPT%20%7C%20Gemini%20%7C%20Grok-blue)]()
[![Market](https://img.shields.io/badge/市场-美国亚马逊-orange)]()

---

## 这是什么

把这个Skill粘进任何AI的系统提示词，它就变成一个资深亚马逊运营——不只是写文案，而是用懂流量结构、竞品定位、合规风险、Review策略的运营思维来生成listing。

**每次生成包含：**
- ✅ 标题（主版本 + A/B测试备选版本）
- ✅ 五点描述（每条按转化职能排序，不是随机排列）
- ✅ 产品描述（Hook → 证明 → CTA结构）
- ✅ 后台关键词（250字节，按关键词类型分桶）
- ✅ 5条Q&A（真实买家语气，以顾虑为切入点）
- ✅ 每段内容的**编注**：解释为什么这样写、埋了哪些词、逻辑是什么
- ✅ Listing健康度评分（6个维度，满分60）
- ✅ 合规扫描（FTC / 亚马逊违禁词）
- ✅ 运营策略建议：变体架构 / Review加速 / 刷新触发条件
- ✅ 上架前Top 3修复项 + 上架后30天行动清单

---

## 怎么用

### 方式一 — Claude Project（推荐）
1. 打开 [claude.ai](https://claude.ai) → 新建 **Project**
2. 进入 **Project Instructions** → 粘贴 `SKILL.md` 的全部内容
3. 在Project里开始新对话
4. 第一条消息发任何内容，SOP准备指南会自动弹出

### 方式二 — ChatGPT Custom GPT
1. 打开 [ChatGPT](https://chat.openai.com) → **探索GPT** → **创建**
2. 在 **Instructions** 栏 → 粘贴 `SKILL.md` 的全部内容
3. 保存后开始对话

### 方式三 — 任何支持系统提示词的AI
把 `SKILL.md` 内容粘进系统提示词输入框即可。
支持：Claude、GPT-4o、Gemini、Grok、Mistral、DeepSeek 等。

### 方式四 — API / Agent集成（OpenClaw、Dify、n8n、Coze）
把 `SKILL.md` 作为独立Listing生成Agent节点的系统提示词。
可接入飞书、WhatsApp等即时通讯工具，实现团队工作流自动化。

---

## 推荐准备流程（效果差距显著）

Skill支持两种模式运行：

| 模式 | 你需要提供 | 输出质量 |
|---|---|---|
| **推断模式** | 仅产品基本信息 | ~55% — 框架完整，关键词为推断 |
| **数据模式** | 关键词 + 竞品listing + Review | ~85% — 接近可直接上架质量 |

**数据模式需要提前准备3样东西：**

**Step 1 — 关键词数据**（约10分钟）
用 Helium10 / DataDive / SellerSprite 跑目标ASIN或产品词
导出 Top 30–50 高流量词，直接粘进对话

**Step 2 — 竞品listing**（约3分钟）
复制2–3个竞品的标题 + 五点描述
AI会找出竞品都没说的差异化空间

**Step 3 — Review情报**（约2分钟）
整理自己产品（或竞品）的高频好评词 + 高频差评/顾虑
这是ROI最高的输入——真实买家语言会直接进入Bullet和Q&A

---

## 效果示例

查看 `/examples` 文件夹中的完整生成案例（含编注）：
- 📱 [无线充电器](examples/wireless-charger.md) — 3C配件，$25，新品上架
- 🕶️ [偏光墨镜](examples/sunglasses.md) — 运动户外，$28–35
- 🍳 [铸铁炒锅](examples/cast-iron-wok.md) — 厨房用品，$45，重新定位

---

## 算法覆盖范围

| 算法/机制 | 覆盖内容 |
|---|---|
| **A9搜索排名** | 关键词放置优先级、CVR→排名反馈机制、精确匹配权重 |
| **Rufus AI购物助手** | 使用场景锚定、对话式查询结构、Q&A索引权重 |
| **转化率优化** | 痛点前置Hook、具体数字替代形容词、顾虑预防性处理 |
| **合规审查** | FTC声明规范、亚马逊违禁词、品类专项规则 |

---

## 迭代指令

listing生成后，可用以下指令继续优化：

| 指令 | 操作 |
|---|---|
| `rewrite [模块名]` | 重写某一个模块 |
| `more [风格]` | 调整整体语气：技术感 / 高端 / 亲切 / 强势 |
| `add keyword: [词]` | 自然地嵌入新关键词 |
| `a/b version` | 生成A/B测试备选版本（只改一个变量） |
| `localize: [UK/CA/DE/JP]` | 适配其他亚马逊站点 |
| `translate: CN` | 输出中文内部参考版本 |
| `gift version` | 以礼品买家为主要人群重新生成 |
| `defend: [差评内容]` | 针对新出现的差评模式更新listing |
| `score only` | 对现有listing跑健康度评分+合规扫描 |

---

## Skill结构

```
首次使用          → SOP准备指南（第一条消息自动触发）
PHASE 0          → 情境判断（新建 / 改写 / 优化在跑的listing）
PHASE 1          → 信息收集（必填项 + 高价值选填项）
PHASE 2          → 竞品差异化矩阵（提供ASIN时触发）
PHASE 3          → 完整listing生成，每段附编注
PHASE 4          → Listing健康度评分（6维度，满分60）
PHASE 5          → 合规扫描（FTC / 亚马逊政策）
PHASE 6          → 运营策略（变体 / Review / 刷新时机）
PHASE 7          → 迭代指令菜单
PHASE 8          → 微调建议 + 30天上架行动清单
运营参考          → A9、Rufus、文案原则、品类专项规则
```

---

## 参与贡献

欢迎PR，优先需要的贡献方向：
- 更多品类的专项规则（美妆、汽车配件、食品、宠物等）
- 其他站点适配（英国、德国、日本、加拿大）
- 更多产品品类的示例输出
- SOP提示的多语言版本

---

## 开源协议

MIT License — 可自由使用、修改、商用，保留原作者信息即可。
详见 [LICENSE](LICENSE)。

---

*为跨境亚马逊卖家构建，针对美国市场优化。*
*欢迎卖家社区贡献和改进。*# Amazon Listing Optimizer
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
