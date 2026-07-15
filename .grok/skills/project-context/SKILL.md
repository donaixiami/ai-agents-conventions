---
name: project-context
description: >
  多项目/ monorepo 上下文恢复与补齐闸门：当工作区有 3 个及以上独立项目时，
  先核对公共上下文登记表是否记录各项目自身 docs 与 skill；缺失则深度理解后创建。
  恢复上下文、跨项目任务、用户说「读上下文/记上下文/恢复记忆」时必须使用。
---

# 多项目上下文（公共登记 + 项目自身 docs/skill）

用中文沟通。本 skill 与根目录 `Agents.md` 第 12 条配套。

**定位**：保证「以后每次恢复上下文」都能按统一闸门盘点，而不是只靠会话记忆。  
**不要**把某一业务页的细节写进本 skill；业务细节写在各项目自己的 `PROJECT_CONTEXT` / skill 里。

---

## 何时启用

- 工作区/当前文件夹下有 **≥3 个独立项目**（见下方判定）
- 用户要求恢复上下文、读取要记忆的规则、跨项目协作
- 新会话接手 monorepo / 多仓工作区
- 用户说「补上下文」「登记项目」「有没有 PROJECT_CONTEXT」

**&lt;3 个项目**：仍建议每个项目自备 `docs/PROJECT_CONTEXT.md` + skill，但不强制走「全量盘点」；触及哪个项目就核对哪个。

---

## 什么叫「独立项目」

满足任一条即可计为 1 个项目：

- 含独立 `package.json` / 可独立构建的应用或库（排除纯 `node_modules`、构建产物目录）
- monorepo 下的正式子包（如 `apps/*`、业务命名子目录 `*-node` / `*-uniapp` / `*-admin`）
- 用户或登记表明确标为项目的目录

**不计入**：`node_modules`、`dist`、`public/upload`、仅资源目录 `ui-assets`、空壳/临时试验目录（除非用户点名）。

触发阈值：**当前管辖范围内独立项目数 ≥ 3**。

---

## 两层结构（必须理解）

| 层级 | 职责 | 默认路径 |
|------|------|----------|
| **公共上下文** | 登记「有哪些项目、各自上下文/skill 在哪、是否齐全、最后核对时间」 | 工作区根 `docs/context/REGISTRY.md` |
| **项目自身上下文** | 该项目定位、技术栈、目录、约定、风险、如何验证 | 项目内 `docs/PROJECT_CONTEXT.md` |
| **项目自身 skill** | 以后在该项目里怎么干活（启动步骤、禁区、命令、模块要点） | 项目根 `SKILL.md`，或 `.grok/skills/<name>/SKILL.md`，或项目内约定路径 |

公共层**不替代**项目层：登记表只做索引与齐全性状态；细节必须在各项目自己的 docs/skill。

若公共登记表不存在而项目数 ≥ 3：**先创建登记表骨架**，再逐项盘点。

---

## 恢复上下文固定顺序

```
1. 判定：管辖范围内独立项目是否 ≥ 3
2. 读公共 REGISTRY（无则创建骨架并列入已知项目）
3. 对比每个项目：PROJECT_CONTEXT 是否存在且非空壳；skill 是否存在且可执行
4. 缺失项：深度理解 → 创建/补齐 docs + skill → 更新 REGISTRY
5. 当次任务相关项目：完整阅读其 PROJECT_CONTEXT + skill
6. 再执行业务任务
```

**禁止**：跳过盘点直接改多个子项目；用过时会话摘要覆盖磁盘上的 `PROJECT_CONTEXT` 而不核对。

---

## 盘点标准（齐全 vs 缺失）

### 视为「有上下文 docs」

- 路径存在，且至少包含：项目定位、技术栈或主要目录、如何启动/验证中的两项以上
- 空文件、仅一行标题、纯复制无关项目内容 → **视为缺失**，需重写

### 视为「有 skill」

- 存在可被 agent 加载的 `SKILL.md`（frontmatter 建议含 `name` + `description`）
- 正文至少含：First Steps / 必读文档、项目形态、关键约定或命令
- 仅有通用 README、无操作闸门 → **不算**项目 skill（可保留 README，另建 skill）

### 登记表必须记录（每项目一行或一节）

- 项目名与相对路径
- `PROJECT_CONTEXT` 路径 + 状态（ok / missing / stale）
- skill 路径 + 状态
- 最后核对日期
- 一句话定位（可选）

---

## 缺失时如何「深度理解再创建」

1. **只读扫描**：`README*`、`package.json`、入口文件、主配置、现有 `docs/**`、测试与脚本  
2. **抓主干**：定位、技术栈、目录地图、请求/数据/鉴权约定、启动命令、已知风险  
3. **写 `docs/PROJECT_CONTEXT.md`**：面向「下次 AI/人快速接手」，不是changelog流水账；用模板 `references/TEMPLATE_PROJECT_CONTEXT.md`  
4. **写项目 `SKILL.md`**：面向「怎么安全改」；用模板 `references/TEMPLATE_PROJECT_SKILL.md`  
5. **回写 `docs/context/REGISTRY.md`**：状态改为 ok，注明日期  
6. **交付说明**：新建了哪些路径、仍不确定的假设写进 PROJECT_CONTEXT「待确认」

深度不足时：宁可在文档写「待确认」并标 `stale`，也不要编造接口与业务规则。

---

## 与记忆的关系

- **磁盘 docs/skill**：跨会话权威来源  
- **会话/内置记忆**：偏好与决策线索；与磁盘冲突时，以磁盘 + 代码事实为准，并更新磁盘  
- 用户说「记住」且属于项目级约定 → 写入对应项目 `PROJECT_CONTEXT` 或 skill，并更新 REGISTRY 日期  

---

## monorepo 特例

- monorepo **根**可有：公共 `docs/context/REGISTRY.md`、根级 `AGENTS.md` / 通用 skills（如 ui-standard）
- **每个可独立交付的子应用/服务**仍必须有自己的 `PROJECT_CONTEXT` + skill  
- 共享资源目录（如 `ui-assets`）在 REGISTRY 中可记为「共享资源」而非完整项目，但要写清唯一源路径  

---

## 禁止清单

- ≥3 项目时不读 REGISTRY 就开干  
- 只有公共登记、各项目无自身 docs  
- 用整仓一份超长 CONTEXT 代替各项目文档且从不拆分  
- 缺失时不扫描代码、凭「常见 Nest/Vue 项目」捏造  
- 创建 skill 却不指向 `PROJECT_CONTEXT`  
- 把用户可见产品文案写成上下文文档的主体（上下文是给协作者/AI 的）  

---

## 自检

完成盘点或补齐后执行 `references/checklist.md`。
