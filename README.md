# OMO 治理 skills

oh-my-opencode 多智能体系统的 omo-* 治理技能集：执行路由、Atlas 编排约束、计划结构标准与计划审查协议。

2026-10-08 自 `E:\Work\publicSkills`（workskills.git）迁出建立本仓库；迁移前的行为裁决与决策史（SK-xxx）仍记录在原仓 `DECISIONS.md`，本仓 skill 后续决策在本仓记录。

## 安装

本仓库整体位于 oh-my-opencode 技能配置路径 `~/.config/opencode/skills/`，重启会话后自动加载。

## 技能列表

| 技能 | 说明 |
|------|------|
| [omo-adaptive-execution](omo-adaptive-execution/) | OMO 统一执行入口：普通任务前台成批，后台仅限明确滑动策略；计划波次、路由与发现委托均在 `SKILL.md`，Sisyphus 日常预算按 overlay，显式滑动不豁免硬边界 |
| [omo-atlas-execution-constraints](omo-atlas-execution-constraints/) | OMO Atlas 中大型目标编排的角色边界、执行门控和质量要求 |
| [omo-plan-structure](omo-plan-structure/) | OMO 计划结构单一标准：五区块 schema、矩阵结构约束、任务原子性契约、并行准入标准、Task 契约字段、路由档位判据、审查判定附件格式与计划/账本分离；Prometheus 编写与 Momus 审查前必须加载 |
| [omo-plan-review](omo-plan-review/) | OMO 计划审查协议单一来源：单审/双审两阶段循环（先 Oracle 循环→再 Momus 循环）、reviewer 委托注入模板、温链收敛与成本门槛；用户选送审时由 Prometheus 加载 |

## 依赖关系

```
omo-adaptive-execution ──→ OMO 执行状态机 + 路由 + 发现委托（单文件，单一规则源）

omo-atlas-execution-constraints ──→ omo-adaptive-execution（必须在 adaptive 成功加载后加载）

omo-plan-structure / omo-plan-review ──→ 计划路径配套（结构标准与审查协议，互不复制）

review-work（仍在 publicSkills 仓）──→ omo-adaptive-execution（启动审查 lane 前加载）
```

## 执行模式裁决

2026-10-08 用户将后台默认改为前台批次优先：普通独立 task 同一响应成组发出，直接收取返回；只有明确滑动需求才按需后台。执行方式及理由要求由 `omo-adaptive-execution/SKILL.md` 单一维护，角色 prompt 和计划格式只承接它；本次用户裁决及被替代历史记录见同级 prompts 仓 `DECISIONS.md` 的 D-049。此变更不修改插件源码、hook、模型、DCP 或清理时长。
