# PROJECT_CONTEXT — ai-agents-conventions

> 规则与 skill 中枢仓库，不承载具体业务产品实现。  
> 最后更新：2026-07-19（补充测试服务复用与清理闸门）
> 原目录名 `ag-project` 已废弃，统一使用本仓库名。

## 1. 项目定位

`BackendManagementSystem/ai-agents-conventions` 用于沉淀**跨项目通用协作规则**与 **Grok skills**，供同级业务仓（如 `soy-milk-project`）或新会话恢复时复用。

- 通用规则：`Agents.md`
- 通用 UI 出稿：`.grok/skills/ui-standard/`
- 多项目上下文闸门：`.grok/skills/project-context/`
- uni-app App/微信小程序/H5 三端兼容：外部 Git 仓库 `donaixiami/uniapp-cross-platform-skill`，本仓以 submodule 挂载到 `.grok/skills/uniapp-cross-platform/`
- 公共登记表：`docs/context/REGISTRY.md`
- 测试服务复用与清理：`Agents.md` 第 18 条

## 2. 目录结构

```
ai-agents-conventions/
├── Agents.md
├── README.md
├── skills/                     # Skill 索引（AI 先读 skills/README.md）
│   ├── README.md
│   ├── ADDING.md
│   └── _template/
├── docs/
│   ├── PROJECT_CONTEXT.md      # 本文
│   ├── 项目介绍.md
│   └── context/
│       └── REGISTRY.md         # 公共上下文登记表
└── .grok/skills/               # Skill 实现正文
    ├── ui-standard/
    ├── project-context/
    ├── uniapp-cross-platform/     # 外部 submodule：App/微信小程序/H5 兼容矩阵与验收
    ├── test-driven-development/  # 来自 obra/superpowers + 本仓 BDD 闸门
    └── conventional-commits/     # 中文约定式提交
```

## 3. 使用方式

1. 在本仓或拷贝规则到目标仓后，AI 会话遵循 `Agents.md`。
2. 查 skill：先 `skills/README.md`，再读 `.grok/skills/<name>/SKILL.md`。
3. 多项目（≥3）恢复上下文：先 `docs/context/REGISTRY.md`，再各项目自身 CONTEXT + skill（见 project-context skill）。
4. UI 出稿：先 `ui-standard` skill。
5. uni-app 三端开发/审查：先初始化并读取 `uniapp-cross-platform` submodule。
6. 更新该 Skill：在独立仓库发布版本，再在本仓更新 submodule 指针。
7. 新增 skill：见 `skills/ADDING.md`，并登记到 `skills/README.md`。

## 4. 非目标

- 不在此仓实现业务 API、页面或数据库。
- 不把某一业务的屏幕清单写进通用 skill。
