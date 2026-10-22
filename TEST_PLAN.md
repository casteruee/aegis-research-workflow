# TEST_PLAN.md — v0.2 验证基线

把今天第二轮「缩小版综述调度测试」记录为 v0.2 的初始验证样本。

## 测试结果基线（2026-09-11）

| 维度 | 结果 |
|---|---|
| CC 参与 | ✅ 前置设计 + 框架设计 + Review（3 次调用） |
| Pi 参与 | ✅ 文献库构建 + 证据矩阵组装（2 次，产物均经 Hermes 亲验正确） |
| Hermes 角色 | 路由判断 / 检索策展 / 证据综合 / 草稿写作 / 验收 |
| Codex | NOT_NEEDED（无本机操作任务，合理缺席） |
| 反模式 | 未重现"顺手链"（机械 CSV 构建交 Pi，设计审查交 CC） |
| 新发现① | CC 也会错配执行者 → 确认 Route Review 必要性 |
| 新发现② | Pi Bridge status=ERROR 但产物正确 → 确认"验收 artifact 不信 status" |

## 待后续优化（记录，不在本轮解决）
1. Evidence Package 不足导致 CC 误判数字 → EVIDENCE_POLICY 已加规则，待下次 Review 验证。
2. Pi Bridge ERROR 假阳性 → 已记验收规则，是否改 Bridge 代码待观察。
3. 阶段闸门的实际执行成本（checkpoint + 压缩）→ 待更大项目验证。

## 下一轮测试建议
在下一个真实科研项目里验证：八阶段闸门制是否真的能抑制"顺手链"、Pi 承接脚本工程是否真的降本。
