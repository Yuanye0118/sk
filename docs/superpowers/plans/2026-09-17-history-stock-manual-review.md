# 历史股票人工复查机制 Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 让用户手动点名的历史已退出股票重新进入受控的收盘后候选研究流程，而不产生盘中追入或自动预案。

**Architecture:** 新增独立的 `manual-review.md` 作为人工复查名单；`AGENTS.md` 定义其唯一入口、收盘初筛和升级路径；`candidate-pool.md` 只接收通过初筛的记录。实时交易判断继续只依赖 `ready-pool.md` 的当前有效执行卡。

**Tech Stack:** Markdown 工作流文档、长桥行情与行业趋势数据。

---

## Chunk 1: 复查名单与纪律入口

### Task 1: 建立人工复查名单

**Files:**
- Create: `D:\stock\manual-review.md`

- [ ] **Step 1: 创建名单文件与状态声明**

写入“仅用户点名后加入、不是持仓/观察池/预案卡、不得盘中生成操作结论”的声明。

- [ ] **Step 2: 创建固定字段表格**

字段为：标的、代码、点名日期、复查原因、当日客观状态、收盘初筛结果、下一步归类。

- [ ] **Step 3: 验证文件边界**

Run: `Get-Content D:\stock\manual-review.md -Encoding UTF8`

Expected: 文件不包含攻击位、确认位、失效位或任何交易指令。

### Task 2: 将人工复查机制写入总规则

**Files:**
- Modify: `D:\stock\AGENTS.md` 的“池子结构与盯盘分工”“工作流程”“每日复盘”

- [ ] **Step 1: 在池子结构中定义人工复查名单**

声明其仅由用户手动点名进入、盘中只报告客观状态、不得替代当前预案卡。

- [ ] **Step 2: 增加收盘后升级门槛**

要求行业进入当日趋势前列、个股相对指数走强、既有四项机会初筛至少通过三项，才可移入候选池。

- [ ] **Step 3: 增加禁止项与复盘字段**

明确旧成本、错过上涨、涨停、连续加速和盘中异动都不能直接产生预案；复盘需记录未通过原因。

- [ ] **Step 4: 验证规则一致性**

Run: `rg -n "人工复查|当前预案卡|收盘后|至少三项" D:\stock\AGENTS.md`

Expected: 新机制没有改变“无当前预案卡不推导交易行动”的总规则。

## Chunk 2: 候选池衔接与验证

### Task 3: 预留候选池承接位置

**Files:**
- Modify: `D:\stock\candidate-pool.md` 的短线/波段研究记录前

- [ ] **Step 1: 添加“人工复查候选”小节**

声明只接收已经完成收盘初筛的手动复查标的，初始为空。

- [ ] **Step 2: 固定候选记录字段**

字段为：标的、代码、通过日期、板块证据、个股量价证据、初筛结果、后续处理。

- [ ] **Step 3: 验证候选池不含执行关键位**

Run: `Get-Content D:\stock\candidate-pool.md -Encoding UTF8 -TotalCount 35`

Expected: 该小节仅记录研究证据，未提供交易触发价。

### Task 4: 场景验收

**Files:**
- Verify: `D:\stock\manual-review.md`
- Verify: `D:\stock\AGENTS.md`
- Verify: `D:\stock\candidate-pool.md`

- [ ] **Step 1: 模拟用户点名烽火通信**

预期：仅加入人工复查名单；不进入当前预案卡，不产生买卖结论。

- [ ] **Step 2: 模拟收盘初筛未通过**

预期：保留客观记录与未通过原因，不进入候选池。

- [ ] **Step 3: 模拟收盘初筛通过**

预期：仅转入“人工复查候选”；仍须在后续收盘后补齐五项预案字段，才可进入 `ready-pool.md`。

- [ ] **Step 4: 人工核对全部边界**

Run: `rg -n "人工复查|盘中|候选|预案卡|创业板" D:\stock\AGENTS.md D:\stock\manual-review.md D:\stock\candidate-pool.md`

Expected: 全链路保留创业板排除、盘中不追入、收盘后建卡三条边界。
