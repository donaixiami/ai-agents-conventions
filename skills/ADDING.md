# 如何新增一个 Skill

给以后的人 / AI：按下列步骤添加，保证可被发现、可被加载。

## 1. 确认是否该进本仓

| 放本仓 `ai-agents-conventions` | 放业务仓 |
|--------------------------------|----------|
| 多个项目都会用到的工作方式 | 只服务某一个业务仓库 |
| 例如通用 UI 出稿、多项目上下文 | 例如某 Nest 模块约定、某 App 页面 |

## 2. 复制模板

```text
skills/_template/          →  参考骨架
.grok/skills/<name>/       →  实际落地目录
  SKILL.md
  references/              →  可选：checklist、长文参考
```

`<name>` 使用小写英文短横线，如 `api-contract`、`release-checklist`。

## 3. 写 SKILL.md

必备：

1. YAML frontmatter：`name`、`description`（description 写清**何时必须启用**，便于工具匹配）  
2. 正文：何时启用、硬性规则、禁止项、自检入口  
3. 用中文；不写某一业务页的屏幕清单（除非 skill 就是业务专用且放在业务仓）  

可参考：`skills/_template/SKILL.md`。

## 4. 登记索引

在 `skills/README.md` 的「已登记 Skills」表中**新增一行**（名称、何时使用、入口链接）。

未登记 = AI 默认不知道有这个 skill。

## 5. 可选：挂钩 Agents.md

若该 skill 应成为「总是/经常强制」的闸门，在 `Agents.md` 增加对应条款并指向  
`.grok/skills/<name>/SKILL.md`。

## 6. 提交

```text
docs(skills): 新增 <name> skill
```

推送到本仓库后，业务仓可按需拷贝该目录到自家 `.grok/skills/`。
