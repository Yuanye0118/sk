# 双窗口超短预案体系 Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将A股预案体系升级为四卡位、双交易窗口且量能条件可验证的超短框架。

**Architecture:** `AGENTS.md`保存纪律与固定流程，`ready-pool.md`保存每日期卡位和完整预案，自动盯盘任务按相同窗口核验并在收盘后更新下一交易日卡位。

**Tech Stack:** Markdown规则文件、长桥CLI行情与资金数据、Codex heartbeat自动盯盘。

---

## Chunk 1: 纪律与预案模板

### Task 1: 更新统一交易纪律

**Files:**
- Modify: `D:\stock\AGENTS.md`

- [ ] 将每日有效执行卡上限改为4张，并定义2主线、1备选、1次日预布局的卡位。
- [ ] 将上午试错窗口改为09:30至10:30，量能门槛改为此前3分钟均量的1.2倍。
- [ ] 新增13:30至14:30的预布局规则：仅限有效卡、最多计划仓位1/3、须满足主基准、量能和2分钟站稳。
- [ ] 保留无前一日卡不交易、涨停/连续加速不进卡、两阶段失败检查等底线。

### Task 2: 更新预案池模板

**Files:**
- Modify: `D:\stock\ready-pool.md`

- [ ] 增加每日四卡位的收盘筛选模板和强弱锚点说明。
- [ ] 标注下午预布局的适用范围，避免旧卡位或盘中涨幅榜被误用。

## Chunk 2: 自动监控与核验

### Task 3: 更新自动盯盘任务

**Files:**
- Modify: Codex automation `a-2`

- [ ] 将10:30和14:30检查改为同时报告四卡位的上午试错、下午预布局状态。
- [ ] 要求每周五收盘后以四卡位结构建立周一预案，未通过则记录原因。

### Task 4: 核验

**Files:**
- Verify: `D:\stock\AGENTS.md`
- Verify: `D:\stock\ready-pool.md`
- Verify: Codex automation `a-2`

- [ ] 搜索并确认1.2倍、09:30–10:30、13:30–14:30、1/3、4张卡位均存在。
- [ ] 确认无前一日预案不交易、涨停/连续加速排除和创业板排除仍存在。
- [ ] 读取自动化配置，确认周五收盘生成周一预案规则仍有效。
