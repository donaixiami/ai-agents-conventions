# 公共上下文登记表（REGISTRY）

> 工作区级索引：登记「有哪些项目、各自上下文与 skill 在哪、是否齐全」。  
> **不替代**各项目自己的 `docs/PROJECT_CONTEXT.md` 与 skill。  
> 恢复上下文时：先读本文 → 再读相关项目文档。  
> 最后全量核对：2026-07-19

## 使用规则

1. 管辖范围内独立项目 **≥ 3** 时，会话恢复/跨项目任务前必须先读本表并逐项对比。
2. 缺失 `PROJECT_CONTEXT` 或项目 skill → 先深度理解再创建，再改业务代码。
3. 新增/移除项目目录时同步更新本表。
4. 详细闸门见 `.grok/skills/project-context/SKILL.md`。

## 本仓库（ai-agents-conventions）自身

| 项目 | 路径 | PROJECT_CONTEXT | Skill | 状态 | 一句话 |
|------|------|-----------------|-------|------|--------|
| ai-agents-conventions（规则中枢） | `.` | `docs/PROJECT_CONTEXT.md` | `.grok/skills/*`（`uniapp-cross-platform` 为外部 submodule） | ok | 存放通用 Agents 规则与跨项目 skill，不承载业务实现 |

## 兄弟工作区示意（BackendManagementSystem）

> 下列为父目录 `BackendManagementSystem` 下常见项目索引，**以各仓库内实际文件为准**；在父目录或跨仓会话中恢复上下文时使用。  
> 状态：`ok` / `missing` / `stale` / `partial`（有 docs 无 skill 或反之）。

| 项目 | 相对父目录路径 | PROJECT_CONTEXT | Skill | 状态（2026-07-15） | 备注 |
|------|----------------|-----------------|-------|-------------------|------|
| soy-milk-project | `soy-milk-project/` | 见该仓 `docs/context/REGISTRY.md` | 根 `AGENTS.md` + `.grok/skills/*` | partial→见子仓登记 | monorepo，≥3 子项目时以子仓 REGISTRY 为准 |
| soyMilkProject | `soyMilkProject/` | 待核 | 待核 | missing | 历史工作区，只读参考倾向 |
| dn_ht_node | `dn_ht_node/` | `docs/PROJECT_CONTEXT.md` | `SKILL.md` | ok | Nest 后端 |
| chat-native-lab | `chat-native-lab/` | 子项待核 | 子项待核 | partial | 含 dn_ht_node / vben |
| vue-vben-admin | `vue-vben-admin/` | 常见于 `docs/` / memory | `vue-vben-admin-project/SKILL.md` 等 | partial | 以仓内为准 |
| nuxt3-demo2 | `nuxt3-demo2/` | `docs/PROJECT_CONTEXT.md` | 待核 | partial | |
| uniapp-demo | `uniapp-demo/` | `docs/PROJECT_CONTEXT.md` | 待核 | partial | |
| TechSpar | `TechSpar/` | `docs/` 多篇 | 待核 | partial | |
| ai-agents-conventions | `ai-agents-conventions/` | `docs/PROJECT_CONTEXT.md` | `.grok/skills/*` | ok | 本仓（原 ag-project 已删除） |

**说明**：父目录项目极多；跨仓任务只对**当次涉及**的行做深度补齐，并回写状态。全量补齐可按用户点名分批进行。

## 核对清单（会话用）

```
[ ] 项目数是否 ≥ 3
[ ] REGISTRY 是否覆盖目标项目
[ ] 每个目标项目 CONTEXT + skill 是否 ok
[ ] 缺失是否已深度理解并创建
```
