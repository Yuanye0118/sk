# 短线交易纪律重构 Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 以统一的“预案—试错—确认—持有/加仓—失效”模型替换旧短线纪律。

**Architecture:** `portfolio.md` 保存面向用户的完整纪律；`AGENTS.md` 保存与其一致的盯盘和分析执行规范。两份文件使用相同的状态定义、触发条件和输出口径。

**Tech Stack:** Markdown 文档；公开行情与人工分析流程。

---

## Chunk 1: 统一纪律正文

### Task 1: 替换 portfolio 的纪律章节

**Files:**
- Modify: `D:\stock\portfolio.md` 的“持仓管理框架”章节

- [ ] 删除旧的编号纪律与重复例外。
- [ ] 同时删除前段“持仓管理纪律”，确保不会保留第二套当前触发条件。
- [ ] 写入统一的五状态短线纪律、明确的攻击信号与成交量标准、试错/加仓仓位上限、入场/加仓/失效条件和复盘模板。
- [ ] 人工检查标题、编号和相邻章节连接，确认不再出现已废弃规则。

### Task 2: 对齐 AGENTS 的执行规范

**Files:**
- Modify: `D:\stock\AGENTS.md` 的分析框架、技术优先和超短线章节

- [ ] 删除旧规则并以统一纪律替代，包括旧警戒/买点提示、当前持仓/预备池表里的旧回本/补仓/止损/确认价指令，以及工作流程中的“开盘买点”表述。
- [ ] 将需要保留的个股执行信息统一改写为“预案/攻击/确认/失效”四字段卡片；没有最新预案的个股不保留旧触发价。
- [ ] 保留自动盯盘仅报告状态、不得自动给出买卖指令的限制。
- [ ] 让收盘预案、盘中试错判断和复盘问题使用同一套术语。

### Task 3: 验证

**Files:**
- Verify: `D:\stock\portfolio.md`
- Verify: `D:\stock\AGENTS.md`

- [ ] 搜索旧的“仅收盘确认”“平本离场优先”“前瞻进场”“天赐买点提醒”等规则，确认不再作为独立纪律存在。
- [ ] 搜索“预案”“试错”“确认”“加仓”“失效”，确认两份文件都覆盖五状态模型。
- [ ] 用永鼎股份的盘中反抽场景人工验证：分别写出“是否达到小仓试错”“是否达到确认加仓”“当前状态和失效证据”，并确认两份文件的结论一致。

### Task 3A: 清理池子文件的遗留纪律

**Files:**
- Modify: `D:\stock\ready-pool.md`
- Modify: `D:\stock\ultra-short-pool.md`
- Modify: `D:\stock\candidate-pool.md`
- Modify: `D:\stock\watchlist.md`
- Modify: `D:\stock\portfolio.md`

- [ ] 删除或标注历史化所有旧触发价、进出场、即时退出和旧体系指令。
- [ ] 为继续跟踪的标的使用统一预案卡字段；候选与推荐观察文件不生成操作触发。
- [ ] 将 portfolio 的市场观察和环境备忘明确标为历史参考。
- [ ] 搜索“触发价”“止损”“加仓”“立即退出”“回踩买入”，确认仅保留在历史记录或统一纪律的非个股示例中。
