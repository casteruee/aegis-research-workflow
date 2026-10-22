# COST_QUOTA_CONTEXT.md — 成本 / 配额 / 上下文

## 外部数据源纪律（来自 v0.1 OpenAlex 429 教训）

科研外部数据源必须支持：
- quota awareness（开始前查剩余额度）
- checkpoint（进度落盘，可恢复）
- retry budget（有限重试，不无脑重试）
- source fallback（切换备用源）
- duplicate prevention（不重复已完成的工作）
- next-day resume（额度恢复后补缺口）

**不写死某个数据库必须启用/禁用。**

遇到 429 / quota exhausted / 权限失败 / 持续网络异常：
1. 先判断错误类型（quota？权限？网络？）。
2. 明确是 quota exhausted → **不要无意义持续重试**（v0.1 曾 40 次盲重试白耗 1 小时）。
3. 保存 checkpoint → 切换备用源 → 额度恢复后再补缺口。

## 成本原则

目标不是"尽量少用 Hermes"，而是**"把高价值 Token 用在高价值判断上"**。

Hermes 可以消耗 Token 做：判断、综合、写作、验收、跨来源分析。

应尽量减少 Hermes Token 用于：大规模重复解析、机械格式转换、批量文件操作、重复脚本编写、可确定性处理的数据工作。

## 上下文原则

长上下文是成本二次增长的根源（轮数 × 上下文大小）。
项目文件是 Source of Truth；Hermes 长上下文不是项目数据库。
阶段结束后 checkpoint + 压缩，必要时新 session 从项目文件继续。
