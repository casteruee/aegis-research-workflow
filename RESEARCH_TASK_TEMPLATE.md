# RESEARCH_TASK_TEMPLATE.md — 给 Pi 的施工单模板

**简单任务用简单模板。不要写超长施工单。**

## 最小核心（简单任务必填 4 项）

```markdown
# Task: <一句话目标>

## Goal
（要达成什么）

## Input
（输入文件/数据在哪）

## Output
（产出什么文件、什么格式）

## Acceptance
（怎么算验收通过）
```

## 可选补充（复杂任务才加）

- Background（为什么做、相关上下文）
- Steps（编号步骤）
- Do Not Change（禁止改动的文件/逻辑）
- Commands（应运行的命令）
- Final Report Format（简短报告格式）

## 注意
- 任务越具体，MiniMax-M3 执行越可靠；模糊任务会漂移或停住。
- 明确"验收条件"，Pi 才能自检。
- Hermes 拿到结果后**必须亲自核验 artifact**（见 QUALITY_GATES.md）。
