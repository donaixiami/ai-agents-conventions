# ai-agents-conventions

跨项目 **AI 协作规则** 与 **Grok skills** 中枢仓库。不承载业务产品代码。

## 内容

| 路径 | 说明 |
|------|------|
| `Agents.md` | 通用协作规则（中文、第一性原理、读者视角、多项目上下文闸门等） |
| `.grok/skills/ui-standard/` | 通用 UI 出稿规范（原型 / Inspect / Figma / 切图先问） |
| `.grok/skills/project-context/` | 多项目（≥3）上下文恢复：公共 REGISTRY + 各项目 docs/skill |
| `docs/PROJECT_CONTEXT.md` | 本仓自身上下文 |
| `docs/context/REGISTRY.md` | 公共上下文登记表（可作工作区索引模板） |

## 使用

1. 业务仓可拷贝 `Agents.md` 与所需 skill，或在会话中直接引用本仓路径。
2. monorepo / 多项目工作区：恢复上下文时先读 `docs/context/REGISTRY.md`（或目标仓内同等文件），再读各项目 `PROJECT_CONTEXT` + skill。
3. UI 相关任务：先读 `ui-standard` skill 与 checklist。

## 首次提交建议

```text
docs: 初始化 AI 协作规则与 ui-standard、project-context skill
```
