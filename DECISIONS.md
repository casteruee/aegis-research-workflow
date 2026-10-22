# DECISIONS.md — v0.2 / v0.2.1 核心决定与原因

## v0.2（沿用）

| # | 决定 | 原因 |
|---|---|---|
| 1 | Hermes 采用 Player-Coach，而非纯管理者 | 纯转发器会丢失跨 Agent 整合与写作这类 Hermes 的真实价值；但必须设防"顺手链" |
| 2 | CC 设计但不拥有最终派工权 | v0.1 实测 CC 曾错配执行者（精读派 Pi、建库派 Codex）；路由判断权必须在 Hermes |
| 3 | Pi 负责批量与脚本工程 | v0.1 的 6,174 行脚本全由 Hermes 写，是本应外派的最大一块 |
| 4 | Codex 按本机操作需求介入 | 不强行为"多 Agent"出场；无本机任务时 NOT_NEEDED 是正确结果 |
| 5 | 不追求 Agent 使用率平均 | 平均化会制造伪任务；缺位不等于错 |
| 6 | 不采用绝对 FIRST 规则 | 路由是判断不是查表；绝对规则会在边缘情况出错 |
| 7 | 项目文件而非长上下文作为事实源 | 长上下文造成成本二次增长 + 压缩丢细节 + 加剧"顺手链"锁定 |
| 8 | 重要任务验收真实产物而不是只看 status | v0.1 实测 Pi Bridge status=ERROR 但产物正确；status≠事实 |

## v0.2.1（maintenance patch）

| 决定 | 原因 |
|---|---|
| 引入 **Independent Acceptance**（AGENT_PASS / STAGE_PASS / PROJECT_PASS）+ **Task Batching / Dispatch Check** | 最新一次真实项目验证显示：CC Architect / Reviewer 定位基本正确；Pi Worker 定位正确；Hermes Route Review + Final Acceptance 有效；Codex 没有适合任务时不强制参与。但多 Agent 均 PASS 后，Hermes 真实产物验收仍发现阻塞级问题。当前主要效率瓶颈从「角色分工错误」转为「任务拆分过细 + 多轮串行交接」。故本轮不调整角色与八阶段，仅补两项轻量规则。 |

## 未在本轮固化的（保持观察）
- Pi Bridge 的 ERROR 假阳性 → 只记验收规则，不改 Bridge 代码（本轮不改，观察后再定）。
- 具体引文审计算法（6-gram 等）→ 不固化算法，只固化"必须审计"。
- 数据库启用/禁用清单 → 不写死，写"预检 + 熔断 + 切换"。
- Bridge / transport 假阳性是否泛化到其他 Agent → 见 FUTURE_OBSERVATIONS，等下次真实项目验证。
- "任意 Agent 都允许 NOT_NEEDED" 是否需显式成文 → 见 FUTURE_OBSERVATIONS。
