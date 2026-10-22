# WORKFLOW.md — 八阶段科研流程

默认流程。**不是硬性流水线，简单科研项目允许合并阶段。**

| Phase | 名称 | 主要工作 | 主要执行者 |
|---|---|---|---|
| 1 | Research Scope | RQ / 范围 / 检索方向 | CC 可前置设计，Hermes 确认 |
| 2 | Literature Discovery | 检索策略 + 代表性策展 | Hermes（判断）；批量收集委派 |
| 3 | Corpus Construction | 元数据 / PDF / 去重 / 入库 | Pi 优先 |
| 4 | Evidence Matrix | 矩阵构建 + 高层判断 | Pi 构建，Hermes 判断 |
| 5 | Framework Review | 分类体系 / 证据强度 / 过度外推 | CC 重点参与 |
| 6 | Drafting | 核心整合与成文 | Hermes 主写，可按章节复杂度委派 |
| 7 | Citation Audit | 批量审计 + 语义异常判断 | Pi/脚本做机械，Hermes 判语义异常 |
| 8 | Final Review | 重要复核 + 独立验收 | CC 复核，Hermes 最终验收 |

## 阶段闸门与上下文管理

重要阶段结束后：
1. 保存 checkpoint（检索进度 / 已完成不重复 / 待办）。
2. 更新项目状态文件。
3. 固化重要输出。

**不规定"每阶段必须新会话"。** 但出现以下任一情况时：
- 上下文显著膨胀
- 阶段目标已变化
- 大部分事实已落盘
- 旧对话开始造成成本或干扰

则：checkpoint → 压缩阶段状态 → 必要时开新 Hermes session → 从项目文件继续。

**原则：项目文件是 Source of Truth，Hermes 长上下文不是项目数据库。**

阶段拆分粒度参考 `AGENT_ROUTING.md` 的「任务批量与粒度」与 Dispatch Check：满足稳定接口 / 高度相关时优先合并 Batch；接口未稳 / 高风险 / 强依赖前步结果时保留细粒度验收。
