# ai-agents-conventions

跨项目 **AI 协作规则** 与 **Grok Skills** 中枢仓库。

让多仓库 / monorepo 在换会话、换人之后，仍按同一套方式思考、改代码、出 UI、恢复上下文。  
**不包含**业务产品实现代码。

完整介绍见：**[docs/项目介绍.md](./docs/项目介绍.md)**

---

## 快速导航

| 文档 | 说明 |
|------|------|
| [docs/项目介绍.md](./docs/项目介绍.md) | 项目是什么、解决什么、怎么用 |
| [Agents.md](./Agents.md) | 通用协作规则（会话总闸门） |
| [**skills/README.md**](./skills/README.md) | **Skill 总目录（AI 先读）** |
| [skills/ADDING.md](./skills/ADDING.md) | 如何新增 skill |
| [.grok/skills/ui-standard/](./.grok/skills/ui-standard/SKILL.md) | 通用 UI 出稿规范 |
| [.grok/skills/project-context/](./.grok/skills/project-context/SKILL.md) | 多项目上下文恢复闸门 |
| [docs/context/REGISTRY.md](./docs/context/REGISTRY.md) | 公共上下文登记表示例 |
| [docs/PROJECT_CONTEXT.md](./docs/PROJECT_CONTEXT.md) | 本仓自身上下文 |

---

## 仓库结构

```
ai-agents-conventions/
├── Agents.md
├── skills/                         # Skill 索引与新增指南（给人/AI 浏览）
│   ├── README.md                   # 总目录：有哪些 skill、何时用
│   ├── ADDING.md
│   └── _template/
├── docs/
│   ├── 项目介绍.md
│   ├── PROJECT_CONTEXT.md
│   └── context/REGISTRY.md
└── .grok/skills/                   # Skill 实现（Grok 加载）
    ├── ui-standard/
    └── project-context/
```

---

## 三分钟上手

1. **读规则**：打开 `Agents.md`  
2. **看有哪些 skill**：打开 [`skills/README.md`](./skills/README.md)，再读命中的 `.grok/skills/...`  
3. **接业务仓**：拷贝 `Agents.md` + 需要的 skill 到业务项目，或在会话中引用本仓路径  
4. **多项目（≥3）**：在业务仓维护 `docs/context/REGISTRY.md`，保证每个子项目有 `docs/PROJECT_CONTEXT.md` 与项目 skill  
5. **做 UI**：按 `ui-standard` 出稿（**PC / H5 / 小程序同等要求**）；不规则切图必须先问用户  
6. **新增 skill**：按 [`skills/ADDING.md`](./skills/ADDING.md)  

---

## 设计原则（摘要）

- **规则可复用，业务不混写**：通用闸门在本仓，产品细节在业务仓  
- **磁盘优先于会话记忆**：约定落在 md / skill 里，而不是只靠聊天  
- **先上下文后改代码**：缺 `PROJECT_CONTEXT` / skill 时先深度理解再补文档  
- **交付面向最终读者**：用户可见页面不写制作过程与评审话术  

---

## License

未单独声明时，默认仅供本组织/作者关联项目内部使用；对外开源请自行补充许可证文件。
