# Skills 目录索引（AI 先读这里）

本文件是本仓库 **skill 总目录**。  
AI 在判断「有没有相关 skill、该读哪份」时：**先读本文**，再按路径打开对应 `SKILL.md`。

---

## 存放约定

| 角色 | 路径 | 说明 |
|------|------|------|
| **本索引（给人/AI 浏览）** | `skills/README.md` | 登记表：有哪些 skill、何时用、入口文件 |
| **skill 实现（Grok 加载）** | `.grok/skills/<name>/SKILL.md` | 实际规范正文；可含 `references/` |
| **新增模板** | `skills/_template/` | 复制后改名，再落到 `.grok/skills/` |

新增 skill 时：实现写入 `.grok/skills/<name>/`，**并在本 README 登记一行**，否则 AI 容易漏读。

详细步骤见 [ADDING.md](./ADDING.md)。

---

## 已登记 Skills

| 名称 | 何时使用 | 入口 | 参考/清单 |
|------|----------|------|-----------|
| **ui-standard** | 任意 UI / 原型 / 视觉稿 / 切图 / Inspect / Figma；**PC、H5、小程序**同等闸门 | [`.grok/skills/ui-standard/SKILL.md`](../.grok/skills/ui-standard/SKILL.md) | [checklist](../.grok/skills/ui-standard/references/checklist.md) |
| **project-context** | 多项目（≥3）恢复上下文；核对公共 REGISTRY 与各项目 docs/skill；缺失则深挖补齐 | [`.grok/skills/project-context/SKILL.md`](../.grok/skills/project-context/SKILL.md) | [checklist](../.grok/skills/project-context/references/checklist.md)、[CONTEXT 模板](../.grok/skills/project-context/references/TEMPLATE_PROJECT_CONTEXT.md)、[项目 skill 模板](../.grok/skills/project-context/references/TEMPLATE_PROJECT_SKILL.md) |
| **test-driven-development** | 实现功能、修 bug、重构、改行为之前；先 TDD；正式测试体前先 BDD/Gherkin 骨架并请用户确认 | [`.grok/skills/test-driven-development/SKILL.md`](../.grok/skills/test-driven-development/SKILL.md) | [bdd-gherkin-gate](../.grok/skills/test-driven-development/bdd-gherkin-gate.md)、[testing-anti-patterns](../.grok/skills/test-driven-development/testing-anti-patterns.md)、[来源](../.grok/skills/test-driven-development/SOURCE.md) |
| **conventional-commits** | 提交 / commit / 推 GitHub；**约定式 type + 中文摘要**；暂存范围与禁止 force | [`.grok/skills/conventional-commits/SKILL.md`](../.grok/skills/conventional-commits/SKILL.md) | [checklist](../.grok/skills/conventional-commits/references/checklist.md) |

> 上表未出现的目录，不视为本仓正式 skill，AI 不应默认启用。

---

## AI 读取顺序

```
1. 读 skills/README.md（本文）→ 匹配任务相关 skill
2. 读对应 .grok/skills/<name>/SKILL.md
3. 需要验收时读 references/checklist.md
4. 再执行任务
```

与 `Agents.md` 的关系：

- `Agents.md`：总协作规则（总是适用）  
- 本目录 skill：按任务类型启用；匹配到则**必须**遵循  

---

## 快速匹配提示

| 用户意图关键词（示例） | 优先 skill |
|------------------------|------------|
| 画 UI、原型、mockup、切图、Inspect、Figma、后台页、H5、小程序 | ui-standard |
| 恢复上下文、多项目、REGISTRY、PROJECT_CONTEXT、补 skill | project-context |
| 写功能、修 bug、重构、TDD、先写测试、单元测试、BDD、Gherkin、Given-When-Then | test-driven-development |
| 提交、commit、push、GitHub、提交说明、约定式提交 | conventional-commits |
| 通用怎么协作、中文、根因、读者视角 | 仅 `Agents.md`（不必进 skill） |

---

## 维护

- 增删 skill → 同步改本表  
- 改 skill 行为 → 改 `.grok/skills/<name>/` 内文件，必要时更新本表「何时使用」  
- 业务项目专用 skill 放在**业务仓**，不要塞进本中枢仓，除非确认为跨项目通用  
