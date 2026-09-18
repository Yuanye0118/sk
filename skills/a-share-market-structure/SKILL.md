---
name: a-share-market-structure
description: Analyze the current A-share market structure before the open or after the close, including leading themes, capital rotation, leader hierarchy, sentiment stage, and next-session observations. Use for requests such as 盘面、市场主线、题材周期、资金去了哪里、盘前总结 or 收盘复盘.
---

# A-share Market Structure

Identify the tradable market structure, not a news list. Use current public market data for indices, breadth, turnover, sector performance and sector capital flows. Use reputable current news only to verify catalysts; state data gaps rather than inferring unavailable breadth, limit-up ladders, or fund flows.

## Operating modes

- **Pre-open:** Review the prior close, overnight catalysts and the prior session's strongest/weakest directions. Produce observation conditions for the coming session, not entry instructions.
- **Intraday / close:** Start from index trend, breadth, turnover and high-to-low performance. Then identify sectors with both relative strength and capital/leader confirmation. Treat a one-off surge without follow-through as a pulse, not a main theme.

## Structure test

For each possible theme, distinguish:

- **Main theme:** sector breadth, identifiable leader, capital participation and a continuing catalyst or trend all align.
- **Secondary theme:** has strength but lacks one of those confirmations.
- **Pulse / follower:** isolated leaders, thin breadth, or a move that is already weakening.

Name the emotional leader, capacity or trend anchor, potential catch-up names, and followers separately. Do not describe every advancing theme as an opportunity.

Classify the market as strong, range-bound, weak, or retreating; then assess the emotion stage as ice point, repair, advance, high-level consolidation, or retreat. Give observable evidence for the classification, including whether leaders hold, broaden, or fade.

Assess each main theme's persistence as weak, average, relatively strong, or strong from: industrial logic, catalyst continuity, and capital consensus. State the invalidation signal.

## Output

Use this exact structure, with concise evidence under every heading:

【1.市场环境】
【2.当前主线】
【3.次级热点】
【4.核心锚点个股】
【5.情绪周期】
【6.主线持续性评估】
【7.明日观察重点】
【8.一句话交易结论】

## Local constraints

- In automatic reports, report structure and observation points only; do not give buy or sell instructions.
- Existing execution decisions remain governed solely by `D:\stock\ready-pool.md` and its current plan cards.
- Do not move or recommend ChiNext / 创业板 stocks (`300`/`301`) into the candidate pool, ultra-short simulation pool, or current plan cards. They may be noted only as market anchors, clearly marked as excluded from execution.
