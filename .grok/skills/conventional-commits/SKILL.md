---
name: conventional-commits
description: >
  用户要求提交、commit、推送 GitHub、写提交说明时使用。
  约定式提交（Conventional Commits）+ 中文说明；暂存范围与禁止事项。
---

# 中文约定式提交（Conventional Commits）

用户要求 **提交 / commit / 推 GitHub** 时必须遵循本 skill。  
与根目录 `Agents.md` 一致：用中文沟通；提交说明**标题与正文默认中文**。

---

## 何时启用

- 用户说：提交、commit、push、上传到 GitHub、写提交信息  
- AI 主动建议提交且用户已同意  
- 审查或改写他人/历史提交说明（若任务要求）  

未要求提交时：**不要**擅自 commit / push。

---

## 格式（强制）

```text
<type>(<scope>): <中文摘要>

[可选正文：说明动机、影响范围、破坏性变更]
```

| 部分 | 规则 |
|------|------|
| `type` | 小写英文，见下方类型表 |
| `scope` | 可选；小写英文或短横线，表示模块/包/端，如 `skills`、`uniapp`、`api` |
| 摘要 | **中文**；陈述做了什么；不加句号；建议 ≤50 字 |
| 正文 | 可选；中文完整句；动机、影响、迁移说明 |
| 标题与正文之间 | 空一行（有正文时） |

### 正确示例

```text
feat(uniapp): 增加分账首页空态与重试

docs: 完善项目介绍与 README 导航

fix(api): 修复菜单列表空字符串过滤导致的误查

docs(skills): 引入 test-driven-development 与中文提交规范

refactor(auth): 抽取 token 刷新逻辑，行为不变
```

### 错误示例

```text
update code                    # 无 type、非中文、无信息
Fix bug.                       # type 应小写；摘要宜中文
feat: Add new feature          # 摘要应中文（除非用户明确要求英文仓）
feat: 完成了，还有别的          # 空洞、不可检索
```

---

## 类型表（type）

| type | 何时用 | 中文理解 |
|------|--------|----------|
| `feat` | 新功能、用户可感知能力 | 新功能 |
| `fix` | 修复缺陷 | 修复 |
| `docs` | 只改文档、注释性说明、skill/规则文案 | 文档 |
| `style` | 格式化、分号、空格等**不影响逻辑** | 格式 |
| `refactor` | 重构，不改变对外行为 | 重构 |
| `perf` | 性能优化 | 性能 |
| `test` | 加测/改测，无生产逻辑（或仅测试） | 测试 |
| `build` | 构建系统、打包、依赖版本（构建相关） | 构建 |
| `ci` | CI 配置与脚本 | 持续集成 |
| `chore` | 杂项工具、不影响 src/test 的维护 | 杂务 |
| `revert` | 回滚某次提交 | 回滚 |

**选型优先**：能归 `feat`/`fix`/`docs` 的不要用 `chore`。  
只改 skill/Agents/说明 → 优先 `docs` 或 `docs(skills)`。

---

## 暂存与提交操作

1. 先看 `git status` / `git diff`，确认改动范围。  
2. **只 stage 与本次意图相关的文件**；禁止无脑 `git add -A` / `git add .`（易带入密钥、本地垃圾）。  
3. 有敏感文件（`.env`、密钥、证书）→ **不加入提交**，并提醒用户。  
4. 提交信息用 HEREDOC / 多行字符串，避免 shell 转义弄坏中文。  
5. 用户明确要求 push 再 push；默认不 force push。  
6. 不改 git config；不回滚用户已有未提交改动。  

PowerShell 示例：

```powershell
git add path/to/file1 path/to/file2
git commit -m @"
docs(skills): 增加中文约定式提交规范

- 类型表与中文摘要示例
- 暂存范围与禁止事项
"@
git push origin main
```

---

## 摘要怎么写（中文）

- 用「动词 + 对象 + 必要限定」，像在说明变更事实，不是日记。  
- 好：`修复登录验证码过期未提示`、`增加公共上下文登记表`  
- 差：`改了一下`、`更新`、`处理问题`、`各种修复`  
- 多个无关改动 → **拆成多次提交**，或摘要写清主变更并在正文列要点。  
- 破坏性变更：标题可加 `!`，或正文写 `BREAKING CHANGE: ...`（说明用中文）。

```text
feat(api)!: 登录响应改为仅返回 accessToken

BREAKING CHANGE: 客户端须停止读取 refreshToken 字段，改走刷新接口。
```

---

## 与本仓其它规则的关系

- 测试实现：先 `test-driven-development` + `bdd-gherkin-gate`，**测通后再提交**。  
- 只改文档/skill：可直接 `docs`，不必强行挂 test 提交。  
- 业务仓若有更细的 scope 表（如 monorepo 包名），以业务 `PROJECT_CONTEXT` 为准，**type + 中文摘要规则不变**。  

---

## 禁止清单

- 英文空洞标题（`update` / `fix stuff`）且无中文说明  
- 伪造作者、或用错误身份提交（除非用户要求）  
- `git add -A` 带入无关/敏感文件  
- 未获用户同意就 push / `--force`  
- 用 `refactor` 掩盖 `feat`/`fix`  
- 一次提交混入完全无关的多主题大杂烩（可拆则拆）  

---

## 自检

完成前执行 [references/checklist.md](./references/checklist.md)。
