# 项目知识库

## 概述

oh-my-opencode（OMO）系统的 omo-* 治理技能仓库：执行路由、Atlas 编排约束、计划结构标准与计划审查协议。纯文档项目，无构建/测试/CI。

本仓整体位于 OMO 技能加载路径 `~/.config/opencode/skills/`（与同级 `prompts/`、`commands/` 子仓库并列），修改后重启会话自动生效。

2026-10-08 自 `E:\Work\publicSkills`（workskills）迁出建仓；迁移前的行为裁决与决策史（SK-xxx）记录在原仓 `DECISIONS.md`，本仓后续决策建议新建 `DECISIONS.md` 续接记录。

## 结构

```
（仓库根，扁平结构：每个 skill 是根下独立目录，各含单个 SKILL.md）
├── README.md                        # 总览 + 技能列表 + 依赖关系
├── AGENTS.md                        # 项目知识库
├── omo-adaptive-execution/          # Core: OMO 执行与路由单一入口（滚动波次/路由/发现委托/委托契约/质量门）
├── omo-atlas-execution-constraints/ # Execution: Atlas 角色边界与治理（须在 adaptive 之后加载）
├── omo-plan-structure/              # Plan: 计划结构单一标准（Prometheus 编写 / Momus 审查共用）
└── omo-plan-review/                 # Plan: 计划审查协议单一来源（Oracle→Momus 两阶段循环）
```

## 依赖与加载顺序

- `omo-atlas-execution-constraints` 必须在 `omo-adaptive-execution` 成功加载后才加载（会话记录需有顺序证据）。
- `omo-plan-structure` 与 `omo-plan-review` 互不复制：结构标准与判定附件格式在前者，审查循环协议与 reviewer 注入模板在后者。
- 外部消费方（如 workskills 仓的 `review-work`）按名字加载 `omo-adaptive-execution`，不复制其内容。

## 约定

- SKILL.md 结构与渐进式披露分层（L0 触发 / L1 规范 / L2 详情 / L3 执行）、frontmatter 约束、长度红线与反模式清单：设计参照维护在 workskills 仓 `docs/skill-design-guide.md`，修改本仓 skill 前先读。
- Frontmatter 仅 `name` + `description` 两个字段；`description` 中文、「当……时使用」触发格式，不写工作流/能力清单。
- 目录与文件命名 kebab-case；skill 内容中文、系统标识符英文（`name`、命令、路径、术语）。
- 提交信息格式：`类型(模块): 中文描述`。
