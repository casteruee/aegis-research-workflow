# FUTURE_OBSERVATIONS.md

阅读 v0.2 全套文档时识别到的小型可优化项。
**未在本轮（v0.2.1）处理**，记录于此，等下一次真实项目验证后再决定是否升级为规则。

不要把单次观察直接升级为全局规则。v0.3 仍待更多真实项目验证。

---

1. **Bridge / transport 层 status 假阳性不限于 Pi**  
   v0.2 已固化的"Pi Bridge ERROR ≠ 任务失败"经验，可能同样适用于 CC / Codex 与外部服务（API、Shell）的传输层。  
   Independent Acceptance 三层 PASS 已覆盖原则，但未明示"任意 Agent 的 transport 错误都应优先验 artifact"。  
   待 v0.3 验证是否需要把这条从 Pi 显式扩展为通用规则。

2. **"任意 Agent 允许 NOT_NEEDED"是否需要显式成文**  
   v0.2 已说明"Codex 不需要为了'多 Agent'而强行出场"。  
   CC 在某些阶段（如纯脚本批处理）也可能并非必需。是否需要把"凡本阶段不需要的 Agent 一律不派"独立成文，避免后续误读为"四角色必须每次全员出席"。

3. **"合并"一词在 WORKFLOW 与 AGENT_ROUTING 之间的歧义**  
   WORKFLOW.md："简单科研项目允许合并阶段"（= Phase 合并）。  
   AGENT_ROUTING.md 的 Task Batching："合并多个 Worker 任务"（= 派工合并）。  
   两者并不等价，但都用了"合并"一词，未来可能造成歧义。是否需要在 v0.3 引入区分术语（如 Phase merge vs Task batching）。