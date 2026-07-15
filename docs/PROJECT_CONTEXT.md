# PROJECT_CONTEXT — ai-agents-conventions

> 规则与 skill 中枢仓库，不承载具体业务产品实现。  
> 最后更新：2026-07-15  
> 原目录名 `ag-project` 已废弃，统一使用本仓库名。

## 1. 项目定位

`BackendManagementSystem/ai-agents-conventions` 用于沉淀**跨项目通用协作规则**与 **Grok skills**，供同级业务仓（如 `soy-milk-project`）或新会话恢复时复用。

- 通用规则：`Agents.md`
- 通用 UI 出稿：`.grok/skills/ui-standard/`
- 多项目上下文闸门：`.grok/skills/project-context/`
- 公共登记表：`docs/context/REGISTRY.md`

## 2. 目录结构

```
ai-agents-conventions/
├── Agents.md
├── README.md
├── docs/
│   ├── PROJECT_CONTEXT.md      # 本文
│   └── context/
│       └── REGISTRY.md         # 公共上下文登记表
└── .grok/skills/
    ├── ui-standard/
    └── project-context/
```

## 3. 使用方式

1. 在本仓或拷贝规则到目标仓后，AI 会话遵循 `Agents.md`。
2. 多项目（≥3）恢复上下文：先 `docs/context/REGISTRY.md`，再各项目自身 CONTEXT + skill（见 project-context skill）。
3. UI 出稿：先 `ui-standard` skill。

## 4. 非目标

- 不在此仓实现业务 API、页面或数据库。
- 不把某一业务的屏幕清单写进通用 skill。
