# QUALITY_GATES.md — 阶段验收

## 验收原则

**Hermes 不能仅相信 Agent 的 status。** 对重要任务必须检查真实 artifact / 输出 / 测试结果后再验收。

## Pi Bridge 验收规则（v0.1 实测教训）

Pi Bridge 返回 ERROR / TIMEOUT 时，**任务可能已经正确完成**。
（实测：Pi 因瞬时 curl 失败被 Bridge 判 ERROR，但产物完全正确。）

因此：
1. 先检查 artifact（文件是否存在、内容是否正确）。
2. 再检查 exit code、文件完整性。
3. 最后才结合 status 判定 PASS / FAIL。

**Agent status ≠ 最终事实。**

## 阶段闸门 checklist

每阶段验收至少确认：
- 产出物存在且非空
- 内容与阶段目标一致
- 无明显的"已完成但内容错误"（抽查关键字段/数字）
- 该阶段的决策已记录

## Independent Acceptance（v0.2.1）

**Agent PASS ≠ Project PASS**

明确区分三层验收：

- **AGENT_PASS**：某个 Agent 完成自己负责的任务，并认为结果符合其验收标准。
- **STAGE_PASS**：当前阶段的全部必要交付物完成，阶段接口验证通过。
- **PROJECT_PASS**：只有 Hermes 作为最终 Orchestrator，基于真实产物完成独立验收后，才允许宣布。

Hermes 最终验收（在每阶段闸门之上叠加全局判断）至少关注：

- 真实产物是否存在
- 关键功能是否实际可运行
- 关键数据是否真实
- Agent 间接口是否正确
- 是否存在阻塞级缺陷

Hermes 不需要重新执行所有子 Agent 工作；但**不能仅因 `CC PASS`、`Pi PASS`、`Codex PASS`、`Tests PASS` 就自动宣布 `PROJECT PASS`**。

## 科研项目特有的三道核验（来自 v0.1，属于 EVIDENCE_POLICY 的强制门）

1. DOI 核验（以注册机构为准）
2. PDF 同一性体检（首页题名 ↔ 元数据题名逐字比对）
3. 引文审计（正文引文逐条回原文比对）

这三道门适用于"进入正式参考文献"的文献，是科研项目的**强制质量门**。
