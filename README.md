# Claude Plugin Guide

[![GitHub stars](https://img.shields.io/github/stars/hongsedaima/Claude-Plugin-Management-Skill?style=social)](https://github.com/hongsedaima/Claude-Plugin-Management-Skill/stargazers)
[![Claude Plugin Market](https://img.shields.io/badge/Claude-Plugin%20Market-orange)](https://claude.com/plugins)
[![中文指南](https://img.shields.io/badge/Guide-%E4%B8%AD%E6%96%87-blue)](#claude-plugin-guide)

一份面向新手的 **Claude 官方插件市场**速查表：每个插件做什么、什么时候开、哪些插件会互相覆盖。

> 更新时间：2026-05-25。本项目整理的是 [Claude 官方插件市场](https://claude.com/plugins) 中出现的插件，不表示这些插件都由 Anthropic 或 Claude 官方开发。如本项目对你有用，记得点 Star，方便以后回来看更新。

---

## 为什么它重要

Claude 插件不是装得越多越好。对新手来说，真正的问题通常有两个：

1. 不知道当前项目到底该安装哪些插件。
2. 装了一大堆插件，但不知道什么时候开、什么时候关、哪些会互相覆盖。

第二种情况往往更糟。插件过多可能带来额外 token 消耗、输出变慢、重复劳动、权限面扩大、指令冲突，甚至让 Agent 在错误的场景调用错误的工具。插件装多了不一定是加分项，很多时候反而会降低协作质量。

所以这个项目不是鼓励你全量安装插件，而是提供一套 **项目插件管理 Skill**：让 Agent 基于真实项目需求，规划必要插件的安装、常驻、按需开启、关闭和授权边界。

---

## 核心概念：初始化项目插件管理规则

这个项目真正想解决的不是“列出所有插件”，而是帮你在任何项目开始时，先初始化一套 **项目插件管理规则**。

这套规则会写入 `CLAUDE.md`、`AGENTS.md` 或项目记忆。之后 Agent 不需要每次重新判断，也不需要用户记住每个插件的用法；当项目进入新功能开发、前端实现、PR 审查、Bug 修复、上线前检查、网页抓取、GitHub 操作、财务/法律/敏感数据处理等场景时，Agent 会主动提醒用户安装、开启、停止或谨慎授权对应插件。

它对 Agent 行为的正面影响是：

1. 从“凭感觉装插件”变成“按项目需求装插件”。
2. 从“用户记住什么时候开关插件”变成“Agent 根据规则主动提醒”。
3. 从“插件越多越混乱”变成“常驻、按需、谨慎授权分层管理”。
4. 从“一次性推荐清单”变成“可沉淀到项目记忆的长期协作规则”。

最终目标是把用户的认知压力和记忆压力降到最低：用户只负责说清楚项目需求，插件的选择、组合、启停和记忆沉淀交给 Agent 处理。

---

## 安装这个 Skill

新手不需要手工读完整插件列表，也不需要复制很长的提示词。直接让 Agent 安装并使用本仓库里的 Skill：

```text
请安装并使用这个 Skill：https://github.com/hongsedaima/Claude-Plugin-Management-Skill/tree/main/skills/project-plugin-management
然后根据当前项目需求，帮我初始化项目插件管理规则。
```

安装后，你可以这样调用：

```text
Use $project-plugin-management to initialize plugin management rules for this project.
```

这个 Skill 会让 Agent 自动完成这条工作流：读取项目上下文 -> 信息不足时提问 -> 推荐必要插件 -> 区分常驻/按需/暂不安装/谨慎授权 -> 生成项目插件管理规则 -> 经确认后写入项目记忆。

---

## 新手快速选择

| 目标 | 优先看这些插件 |
| -- | -- |
| 想让 Claude 记住项目规则 | [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management)、[`Remember`](https://claude.com/plugins/remember)、[`Productivity`](https://claude.com/plugins/productivity) |
| 想做新功能 | [`Feature Dev`](https://claude.com/plugins/feature-dev)、[`Superpowers`](https://claude.com/plugins/superpowers)、[`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) |
| 想做前端 | [`Frontend Design`](https://claude.com/plugins/frontend-design)、[`Design`](https://claude.com/plugins/design)、[`Playwright`](https://claude.com/plugins/playwright) |
| 想提高代码质量 | [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp)、[`Serena`](https://claude.com/plugins/serena)、[`Security Guidance`](https://claude.com/plugins/security-guidance)、[`Semgrep`](https://claude.com/plugins/semgrep) |
| 想做 PR 或上线前检查 | [`Code Review`](https://claude.com/plugins/code-review)、[`CodeRabbit`](https://claude.com/plugins/coderabbit)、[`Optibot Code Review`](https://claude.com/plugins/optibot)、[`sonarqube`](https://claude.com/plugins/sonarqube) |

---

## 常见组合

| 场景 | 推荐组合 |
| -- | -- |
| 长期代码项目 | [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management) + [`Hookify`](https://claude.com/plugins/hookify) + [`Security Guidance`](https://claude.com/plugins/security-guidance) + 对应语言 LSP |
| 新功能开发 | [`Feature Dev`](https://claude.com/plugins/feature-dev) + [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp) / [`Serena`](https://claude.com/plugins/serena) + [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) |
| 前端页面开发 | [`Frontend Design`](https://claude.com/plugins/frontend-design) + [`Playwright`](https://claude.com/plugins/playwright) + [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) |
| 上线前检查 | [`Semgrep`](https://claude.com/plugins/semgrep) + [`Sonatype Guide`](https://claude.com/plugins/sonatype-guide) + [`Code Review`](https://claude.com/plugins/code-review) 或 [`Optibot Code Review`](https://claude.com/plugins/optibot) |
| 大型仓库排障 | [`Serena`](https://claude.com/plugins/serena) + [`Sourcegraph`](https://claude.com/plugins/sourcegraph) 或 [`Greptile`](https://claude.com/plugins/greptile) + [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) |
| 需求到交付 | [`Product Management`](https://claude.com/plugins/product-management) + [`Feature Dev`](https://claude.com/plugins/feature-dev) + [`GitHub`](https://claude.com/plugins/github) + [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) |

---

## 怎么读这份表

- **常驻**：建议在匹配的项目、角色或团队流程中默认开启，持续收益大于上下文和权限成本。
- **按需**：只在具体任务中开启。通常因为权限更高、上下文更重、会明显改变 Claude 行为，或只适合某一类工作。
- **典型用法**：每个提示词都放在独立代码块里，在 GitHub 页面可直接点击复制。
- **影响关系**：每个分类下方都列出插件之间的包含、重叠、互补、冲突或权限影响。

插件明细不再用宽表格呈现。表格适合快速对比，但插件说明、推荐方式和典型用法都比较长，卡片式结构在移动端和 GitHub 页面上更容易阅读。

---

## 增强工作流

### [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management)

- 核心功能：维护 CLAUDE.md：审查质量、沉淀会话经验、让项目记忆保持更新。
- 使用场景：长期项目、团队约定频繁变化、希望 Claude 自动记住工程规则。
- 典型用法：

```text
检查并更新当前项目的 CLAUDE.md，把刚才约定的规则沉淀进去
```

- 推荐方式：**常驻**：代码项目内建议默认开启，用它维护项目级规则和踩坑记录；如果只是一次性问答或临时脚本，就不用引入项目记忆。

### [`Superpowers`](https://claude.com/plugins/superpowers)

- 核心功能：增强头脑风暴、子代理开发、代码审查、系统化调试、红绿 TDD 和技能编写能力。
- 使用场景：复杂需求拆解、TDD、调试卡住、想让 Claude 更主动地规划开发。
- 典型用法：

```text
用 Superpowers 帮我拆解这个需求，并按 TDD 的方式推进实现
```

- 推荐方式：**按需**：复杂功能、TDD 或系统化调试时开启；简单改文案、小修小补时会显得过重。

### [`Feature Dev`](https://claude.com/plugins/feature-dev)

- 核心功能：用探索、设计、实现、评审代理组织完整的新功能开发流程。
- 使用场景：从需求到代码落地的一整段功能开发，而不是零散小改动。
- 典型用法：

```text
用 Feature Dev 带我从探索、设计到实现这个新功能
```

- 推荐方式：**按需**：新功能启动到合并前开启，适合让 Claude 按流程推进；需求很小或已经有明确实现方案时不必开启。

### [`Claude Code Setup`](https://claude.com/plugins/claude-code-setup)

- 核心功能：分析代码库，推荐 hooks、skills、MCP servers、subagents 等 Claude Code 自动化配置。
- 使用场景：新项目接入 Claude Code，或想重整现有项目的自动化能力。
- 典型用法：

```text
帮我 setup 一下当前这个项目，推荐适合的 Claude Code 自动化配置
```

- 推荐方式：**按需**：项目初始化、换技术栈或季度巡检时运行一次；它是诊断工具，不需要每天常驻。

### [`Remember`](https://claude.com/plugins/remember)

- 核心功能：把对话抽取、总结、压缩为分层日志，形成 Claude Code 的持续记忆。
- 使用场景：跨天、跨周的长期协作，需要保留历史上下文。
- 典型用法：

```text
把这次会话的关键决策整理进长期记忆，方便下次继续
```

- 推荐方式：**常驻**：长期项目或长期协作建议开启，让 Claude 保留决策背景；短任务关闭，避免累积无价值记忆。

### [`Skill Creator`](https://claude.com/plugins/skill-creator)

- 核心功能：创建、改进、评估和基准测试 Claude 技能。
- 使用场景：想把公司流程、个人方法论或工具操作封装成可复用 skill。
- 典型用法：

```text
帮我把这套工作流程做成一个可复用的 Claude skill
```

- 推荐方式：**按需**：只有创建、评估或维护 skill 时开启；日常写代码不需要它参与上下文。

### [`Playwright`](https://claude.com/plugins/playwright)

- 核心功能：Microsoft Playwright MCP，支持浏览器自动化、截图、填表、点击和端到端测试。
- 使用场景：Web 应用测试、截图验收、复现用户路径、自动化表单操作。
- 典型用法：

```text
用 Playwright 打开本地页面，截图并验证主要交互是否正常
```

- 推荐方式：**按需**：需要真实浏览器交互、截图或 E2E 验证时开启；普通代码编辑阶段关闭，减少权限和执行成本。

### [`Firecrawl`](https://claude.com/plugins/firecrawl)

- 核心功能：把网页、站点或搜索结果转成适合 LLM 使用的 Markdown 或结构化数据。
- 使用场景：抓取竞品文档、网页资料整理、多来源信息抽取。
- 典型用法：

```text
用 Firecrawl 抓取这个网站并整理成适合 Claude 阅读的 Markdown
```

- 推荐方式：**按需**：外部网页采集和资料整理时开启；涉及版权、账号页或敏感网页时先确认边界。

### [`session-report`](https://claude.com/plugins/session-report)

- 核心功能：从本地 Claude transcript 生成可浏览 HTML 报告，分析 token、缓存、subagent、skill 和高成本 prompt。
- 使用场景：复盘一次 Claude Code 会话的消耗、效率和上下文结构。
- 典型用法：

```text
生成这次 Claude Code 会话的 session report，分析 token 和缓存使用
```

- 推荐方式：**按需**：会话结束、成本异常或想优化工作流时开启；它不改善实时开发体验，不必常驻。

影响关系：

1. [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management)、[`Remember`](https://claude.com/plugins/remember)、[`Productivity`](https://claude.com/plugins/productivity) 都和“记忆”有关：前者管项目规则，第二个管会话历史，第三个偏个人任务和工作上下文，避免同一事实重复写入三处。
2. [`Feature Dev`](https://claude.com/plugins/feature-dev) 包含探索、设计、实现、评审流程；[`Superpowers`](https://claude.com/plugins/superpowers) 更强调 TDD、调试和子代理开发。新功能优先用 [`Feature Dev`](https://claude.com/plugins/feature-dev)，卡在技术策略或测试节奏时再加 [`Superpowers`](https://claude.com/plugins/superpowers)。
3. [`Claude Code Setup`](https://claude.com/plugins/claude-code-setup) 是诊断和推荐工具，不直接替代其他插件；适合先跑它，再决定是否安装 [`Playwright`](https://claude.com/plugins/playwright)、[`Firecrawl`](https://claude.com/plugins/firecrawl)、[`Hookify`](https://claude.com/plugins/hookify) 等插件。
4. [`Playwright`](https://claude.com/plugins/playwright) 和 [`Firecrawl`](https://claude.com/plugins/firecrawl) 都会访问外部网页或浏览器环境，适合按需开启，避免在普通代码任务中扩大权限面。
5. [`Skill Creator`](https://claude.com/plugins/skill-creator) 和 [`Superpowers`](https://claude.com/plugins/superpowers) 都能帮助技能编写；正式创建、评估 skill 时优先用 [`Skill Creator`](https://claude.com/plugins/skill-creator)。
6. [`session-report`](https://claude.com/plugins/session-report) 不改变 Claude 行为，适合最后做复盘，不需要常驻。

---

## 约束 Agent

### [`Hookify`](https://claude.com/plugins/hookify)

- 核心功能：用 Markdown 规则创建 hooks，阻止 Claude 出现不符合项目约定的行为。
- 使用场景：强制代码风格、限制危险命令、禁止错误库或过时 API。
- 典型用法：

```text
根据这些项目规则创建 Hookify 约束，防止 Claude 以后违反
```

- 推荐方式：**常驻**：规则稳定后建议默认开启，把团队约定变成执行护栏；规则还在探索时先小范围启用，避免误拦截。

### [`Ralph Loop`](https://claude.com/plugins/ralph-loop)

- 核心功能：让 Claude 以自我参照循环反复处理同一任务，看到上轮结果后继续迭代直到完成。
- 使用场景：需要多轮自动尝试、修复、再验证的开发任务。
- 典型用法：

```text
用 Ralph Loop 反复修复这个问题，直到测试通过或遇到明确阻塞
```

- 推荐方式：**按需**：只给边界清晰、验收标准明确的任务开启；涉及远程写入、资金、账号或大规模改动时不要放任循环。

影响关系：

1. [`Hookify`](https://claude.com/plugins/hookify) 是约束，[`Ralph Loop`](https://claude.com/plugins/ralph-loop) 是加速；同时使用时必须写清楚停止条件、允许命令和验收标准。
2. [`Hookify`](https://claude.com/plugins/hookify) 可把 CLAUDE.md 中的规则变成执行前后的约束，适合补强 [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management)。
3. [`Ralph Loop`](https://claude.com/plugins/ralph-loop) 不建议和 [`GitHub`](https://claude.com/plugins/github)、[`Playwright`](https://claude.com/plugins/playwright)、[`Firecrawl`](https://claude.com/plugins/firecrawl) 等高权限插件长期同时开启，避免自动循环影响远程仓库或外部系统。

---

## 设计前端

### [`Frontend Design`](https://claude.com/plugins/frontend-design)

- 核心功能：生成有设计质量的生产级前端界面，避免通用 AI 风格。
- 使用场景：从文字需求生成页面、组件、交互或视觉更完整的前端代码。
- 典型用法：

```text
用 Frontend Design 设计并实现这个页面，避免通用 AI 风格
```

- 推荐方式：**按需**：写 UI、组件、落地页或交互原型时开启；后端、脚本、安全扫描任务关闭，避免审美指令污染技术判断。

### [`Design`](https://claude.com/plugins/design)

- 核心功能：加速设计 critique、UX 文案、可访问性审查、研究综合和开发交接。
- 使用场景：评审视觉稿、整理设计系统、检查无障碍、把调研转成设计决策。
- 典型用法：

```text
用 Design 审查这个界面，重点看 UX 文案、可访问性和交接问题
```

- 推荐方式：**按需**：设计评审、无障碍审查、UX 文案或交接阶段开启；进入纯实现阶段后只保留必要上下文。

影响关系：

1. [`Design`](https://claude.com/plugins/design) 更像设计评审和交接专家，[`Frontend Design`](https://claude.com/plugins/frontend-design) 更像前端界面生成专家；推荐先用 [`Design`](https://claude.com/plugins/design) 明确标准，再用 [`Frontend Design`](https://claude.com/plugins/frontend-design) 写代码。
2. [`Frontend Design`](https://claude.com/plugins/frontend-design) 生成代码后，可以接 [`Playwright`](https://claude.com/plugins/playwright) 做截图和端到端验证，也可以接 [`Playground`](https://claude.com/plugins/playground) 做可交互预览。
3. 两者都会影响 Claude 的审美和表达方式，不建议在纯后端、数据处理或安全扫描任务中常驻。

---

## 写代码

### [`Playground`](https://claude.com/plugins/playground)

- 核心功能：生成带控件、实时预览和复制输出的自包含 HTML playground。
- 使用场景：快速做设计探索、数据探索、概念图或文档 critique 工具。
- 典型用法：

```text
做一个可交互的 HTML playground，让我能调整参数并预览结果
```

- 推荐方式：**按需**：需要可视化交互原型、一次性分析面板或演示工具时开启；正式产品代码应另行工程化。

### [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp)

- 核心功能：为 TypeScript 和 JavaScript 提供语言服务器级代码智能。
- 使用场景：TS/JS 项目的类型、引用、诊断和重构辅助。
- 典型用法：

```text
用 TypeScript LSP 检查这次修改的类型错误和引用问题
```

- 推荐方式：**常驻**：TS/JS 项目默认开启，能持续提升定位和修改精度；非 TS/JS 项目关闭，避免无效上下文。

### [`sonarqube`](https://claude.com/plugins/sonarqube)

- 核心功能：在 agent coding loop 中执行 SonarQube 质量与安全规则、secret 扫描和质量门禁。
- 使用场景：企业级质量门禁、合并前检查、多语言代码质量治理。
- 典型用法：

```text
用 sonarqube 检查当前改动的代码质量、安全风险和质量门禁
```

- 推荐方式：**按需**：合并前、发布前或高标准企业项目开启；快速原型阶段不建议常驻，因为 hooks 可能拖慢迭代。

### [`Code Simplifier`](https://claude.com/plugins/code-simplifier)

- 核心功能：在保持功能不变的前提下，简化最近修改过的代码，提升清晰度和一致性。
- 使用场景：功能写完后做收尾重构、降低复杂度、统一风格。
- 典型用法：

```text
在不改变功能的前提下，简化最近修改过的代码
```

- 推荐方式：**按需**：测试通过、功能边界稳定后开启；需求还在变化时先别简化，减少返工。

### [`Serena`](https://claude.com/plugins/serena)

- 核心功能：基于语言服务器协议提供语义代码理解、重构建议和代码库导航。
- 使用场景：大型代码库理解、跨文件重构、定位复杂调用链。
- 典型用法：

```text
用 Serena 分析这个函数的调用链，并给出安全的重构方案
```

- 推荐方式：**常驻**：大型或长期代码库推荐开启，持续提供语义导航；小脚本或单文件任务按需即可。

### [`Security Guidance`](https://claude.com/plugins/security-guidance)

- 核心功能：编辑文件时提醒命令注入、XSS 和不安全代码模式。
- 使用场景：Web、API、鉴权、输入处理、脚本执行相关开发。
- 典型用法：

```text
检查这段代码是否有命令注入、XSS 或不安全模式
```

- 推荐方式：**常驻**：多数代码项目都适合默认开启，作为轻量安全护栏；非代码写作任务可以关闭。

### [`Semgrep`](https://claude.com/plugins/semgrep)

- 核心功能：实时捕获安全漏洞，并引导 Claude 从一开始写更安全的代码。
- 使用场景：安全敏感代码、Web/API、合并前安全检查。
- 典型用法：

```text
用 Semgrep 扫描当前改动里的安全漏洞，并给出修复建议
```

- 推荐方式：**常驻**：安全敏感项目建议默认开启，尽早发现漏洞模式；与更重的安全平台同时开时注意重复报警。

### [`Aikido Security`](https://claude.com/plugins/aikido)

- 核心功能：通过 Aikido MCP 做 SAST、secret 和 IaC 漏洞检测。
- 使用场景：上线前安全扫描、密钥泄露检查、基础设施配置审查。
- 典型用法：

```text
用 Aikido Security 扫描 SAST、密钥泄露和 IaC 风险
```

- 推荐方式：**按需**：发布前、安全审计或 IaC 变更时开启；日常小改动可先依赖轻量安全提醒。

### [`Sonatype Guide`](https://claude.com/plugins/sonatype-guide)

- 核心功能：做软件供应链和依赖安全分析，给出漏洞检测与安全版本建议。
- 使用场景：新增依赖、升级依赖、审查 npm/pip/Maven 等第三方包。
- 典型用法：

```text
用 Sonatype Guide 检查这些依赖是否有漏洞，并推荐安全版本
```

- 推荐方式：**按需**：新增、升级或审查依赖时开启；它解决供应链问题，不替代源码扫描。

影响关系：

1. [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp)、[`Serena`](https://claude.com/plugins/serena)、[`Sourcegraph`](https://claude.com/plugins/sourcegraph)、[`Greptile`](https://claude.com/plugins/greptile) 都能帮助理解代码：[`TypeScript LSP`](https://claude.com/plugins/typescript-lsp) 专注 TS/JS 类型和引用，[`Serena`](https://claude.com/plugins/serena) 偏本地语义导航，[`Sourcegraph`](https://claude.com/plugins/sourcegraph) / [`Greptile`](https://claude.com/plugins/greptile) 偏跨仓库或自然语言搜索。
2. [`Security Guidance`](https://claude.com/plugins/security-guidance) 是轻量实时提醒；[`Semgrep`](https://claude.com/plugins/semgrep) 更偏规则化漏洞扫描；[`Aikido Security`](https://claude.com/plugins/aikido) 覆盖 SAST、secret、IaC；[`sonarqube`](https://claude.com/plugins/sonarqube) 同时管质量和安全。不要无脑全开，先按项目风险选择。
3. [`Sonatype Guide`](https://claude.com/plugins/sonatype-guide) 只解决依赖和供应链问题，不能替代 [`Semgrep`](https://claude.com/plugins/semgrep)、[`Aikido Security`](https://claude.com/plugins/aikido) 或 [`sonarqube`](https://claude.com/plugins/sonarqube) 的源码安全检查。
4. [`Code Simplifier`](https://claude.com/plugins/code-simplifier) 应放在功能完成和测试通过之后；过早简化会增加返工。
5. [`sonarqube`](https://claude.com/plugins/sonarqube) hooks 可能在每次编辑后运行，更适合高质量门禁项目，不适合快速原型阶段长期常驻。

---

## 管理代码

### [`GitHub`](https://claude.com/plugins/github)

- 核心功能：GitHub MCP，可创建 issue、管理 PR、审查代码、搜索仓库并访问 GitHub API。
- 使用场景：在 Claude Code 中处理 issue、PR、repo 搜索和仓库自动化。
- 典型用法：

```text
用 GitHub 帮我查看这个仓库的 open PR，并总结需要处理的事项
```

- 推荐方式：**常驻**：GitHub 是主要协作平台时建议默认开启；注意 token 权限，敏感仓库只在需要时授权。

### [`Commit Commands`](https://claude.com/plugins/commit-commands)

- 核心功能：提供 commit、push、创建 PR 等 Git 工作流命令。
- 使用场景：写完代码后规范提交、推送、开 PR。
- 典型用法：

```text
检查 diff 后帮我生成合适的 commit，并准备 push 和 PR
```

- 推荐方式：**常驻**：频繁提交代码的项目可以开启，减少重复命令；自动提交前仍要先完成测试和 diff 审查。

### [`Greptile`](https://claude.com/plugins/greptile)

- 核心功能：用自然语言查询仓库，查找代码、依赖关系和架构上下文。
- 使用场景：问“这个功能在哪”“谁调用了这个模块”“这段逻辑依赖什么”。
- 典型用法：

```text
用 Greptile 找出用户登录逻辑在哪里实现，以及依赖哪些模块
```

- 推荐方式：**按需**：大型仓库或不熟悉代码库时开启；小仓库优先用本地搜索和 LSP，减少外部依赖。

### [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit)

- 核心功能：针对 PR 评论、测试、错误处理、类型设计、代码质量和简化的评审代理集合。
- 使用场景：合并前做系统化 PR 检查。
- 典型用法：

```text
用 PR Review Toolkit 审查这个 PR，重点看测试、错误处理和类型设计
```

- 推荐方式：**按需**：开 PR、准备合并或改动影响面较大时开启；日常编辑阶段不用持续占用上下文。

影响关系：

1. [`GitHub`](https://claude.com/plugins/github) 已覆盖 issue、PR 和仓库 API；[`Commit Commands`](https://claude.com/plugins/commit-commands) 更偏本地 Git 提交命令，两者可以共存，但创建 PR 的能力有重叠。
2. [`Greptile`](https://claude.com/plugins/greptile) 和 [`Sourcegraph`](https://claude.com/plugins/sourcegraph) 都能做代码搜索；如果只是当前仓库问题，先用 [`Greptile`](https://claude.com/plugins/greptile) 或 [`Serena`](https://claude.com/plugins/serena)，跨仓库再用 [`Sourcegraph`](https://claude.com/plugins/sourcegraph)。
3. [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit)、[`Code Review`](https://claude.com/plugins/code-review)、[`CodeRabbit`](https://claude.com/plugins/coderabbit)、[`Optibot Code Review`](https://claude.com/plugins/optibot) 都能参与评审。普通 PR 用 [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) 或 [`Code Review`](https://claude.com/plugins/code-review)，高风险改动再加 [`CodeRabbit`](https://claude.com/plugins/coderabbit) 或 [`Optibot Code Review`](https://claude.com/plugins/optibot)。
4. [`Commit Commands`](https://claude.com/plugins/commit-commands) 最好放在测试、静态检查和 PR 评审之后使用，不要让提交命令跑在质量检查前面。

---

## 修 BUG

### [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp)

- 核心功能：控制和检查实时 Chrome：性能 trace、网络请求、console、source map 栈和浏览器动作。
- 使用场景：调试页面性能、接口请求、控制台错误、真实浏览器状态。
- 典型用法：

```text
用 Chrome DevTools 连接当前页面，检查 console、network 和性能问题
```

- 推荐方式：**按需**：需要连接正在运行的浏览器、分析性能或查网络请求时开启；不调试前端时关闭。

### [`Code Review`](https://claude.com/plugins/code-review)

- 核心功能：使用专门代理和置信度过滤做 PR 代码审查。
- 使用场景：代码合并前检查明显 bug、回归风险和可维护性问题。
- 典型用法：

```text
用 Code Review 审查这个 PR，列出高置信度问题和修复建议
```

- 推荐方式：**按需**：PR 阶段或重要改动完成后开启；不要在每次小改动后都运行，避免审查噪音。

### [`CodeRabbit`](https://claude.com/plugins/coderabbit)

- 核心功能：结合 40+ 分析器、AST、代码图和项目规则做 AI 代码评审。
- 使用场景：复杂、安全敏感或影响面大的代码改动，需要外部视角。
- 典型用法：

```text
用 CodeRabbit 对当前改动做深度代码审查，重点看安全和边界情况
```

- 推荐方式：**按需**：高风险合并前开启，适合当第二审查视角；它不能替代测试、类型检查和人工判断。

### [`Optibot Code Review`](https://claude.com/plugins/optibot)

- 核心功能：审查本地改动、分支差异或 patch，关注生产 bug、业务逻辑问题和安全漏洞。
- 使用场景：未提交改动、分支对比、patch 文件审查、CI 中自动评审。
- 典型用法：

```text
用 Optibot review my changes，重点找生产 bug、业务逻辑问题和安全漏洞
```

- 推荐方式：**按需**：发布前、本地 diff 审查或 CI 自动审查时开启；与 [`CodeRabbit`](https://claude.com/plugins/coderabbit) 部分重叠，二选一或分层使用。

### [`Sourcegraph`](https://claude.com/plugins/sourcegraph)

- 核心功能：跨代码库搜索、追踪引用、分析重构影响、排查事故和做定向安全扫查。
- 使用场景：跨仓库定位 bug、理解历史提交和引用链路。
- 典型用法：

```text
用 Sourcegraph 跨仓库搜索这个 API 的调用方和历史修改
```

- 推荐方式：**按需**：多仓库、大型代码库或事故排查时开启；单仓库小问题先用 [`Serena`](https://claude.com/plugins/serena) 或本地搜索。

影响关系：

1. [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) 和 [`Playwright`](https://claude.com/plugins/playwright) 都能操控浏览器：前者适合现场调试和性能分析，后者适合把复现路径固化成自动化测试。
2. [`Code Review`](https://claude.com/plugins/code-review)、[`CodeRabbit`](https://claude.com/plugins/coderabbit)、[`Optibot Code Review`](https://claude.com/plugins/optibot) 都是评审类插件，但重点不同：[`Code Review`](https://claude.com/plugins/code-review) 偏 PR，[`CodeRabbit`](https://claude.com/plugins/coderabbit) 偏深度静态分析，[`Optibot Code Review`](https://claude.com/plugins/optibot) 偏本地差异和生产风险。
3. [`Sourcegraph`](https://claude.com/plugins/sourcegraph)、[`Greptile`](https://claude.com/plugins/greptile)、[`Serena`](https://claude.com/plugins/serena) 都能找代码；[`Sourcegraph`](https://claude.com/plugins/sourcegraph) 更适合跨仓库和事故排查，[`Serena`](https://claude.com/plugins/serena) 更适合本地语义重构。
4. 推荐修 bug 流程：[`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) 复现问题，[`Serena`](https://claude.com/plugins/serena) / [`Sourcegraph`](https://claude.com/plugins/sourcegraph) 定位代码，修复后用 [`Code Review`](https://claude.com/plugins/code-review) 或 [`Optibot Code Review`](https://claude.com/plugins/optibot) 复核。

---

## 其他日常事务

### [`LegalZoom`](https://claude.com/plugins/legalzoom)

- 核心功能：AI 审查法律文件风险，并在需要时建议咨询律师或连接 LegalZoom 专业网络。
- 使用场景：合同、合规文档、条款审查、识别需要律师介入的风险。
- 典型用法：

```text
用 LegalZoom 审查这份合同，标出关键风险和需要律师确认的条款
```

- 推荐方式：**按需**：只有处理法律文件、合同条款或合规风险时开启；它不能替代律师意见，敏感文件要注意授权范围。

影响关系：

1. [`LegalZoom`](https://claude.com/plugins/legalzoom) 只应处理法律文件相关任务，不适合常驻到代码开发上下文中。
2. 处理合同或合规文件时，避免同时开启不必要的代码仓库、浏览器或网页采集插件，减少敏感信息暴露面。
3. 如果文件内容涉及财务、运营或产品策略，可先用对应业务插件整理事实，再用 [`LegalZoom`](https://claude.com/plugins/legalzoom) 做法律风险视角审查。

---

## 通用办公与业务插件

### [`Productivity`](https://claude.com/plugins/productivity)

- 核心功能：管理任务、规划一天，并建立关于工作上下文的持久记忆。
- 使用场景：个人工作流、日程任务同步、上下文整理。
- 典型用法：

```text
帮我整理今天的任务和上下文，给出接下来最该做的三件事
```

- 推荐方式：**常驻**：把 Claude 当日常工作助理时建议开启；如果只做纯代码任务，注意和 [`Remember`](https://claude.com/plugins/remember)、[`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management) 的记忆边界。

### [`Engineering`](https://claude.com/plugins/engineering)

- 核心功能：支持站会、代码审查、架构决策、事故响应和技术文档。
- 使用场景：技术负责人、研发团队协作、工程流程管理。
- 典型用法：

```text
用 Engineering 帮我整理这次架构决策，输出 ADR 草稿
```

- 推荐方式：**常驻**：工程管理、团队协作和技术文档场景建议开启；单纯写代码时可按需打开，避免覆盖更专门的开发插件。

### [`Data`](https://claude.com/plugins/data)

- 核心功能：写 SQL、探索数据集、生成洞察、构建可视化和仪表盘。
- 使用场景：数据分析、报表、指标解释、面向干系人的数据故事。
- 典型用法：

```text
用 Data 帮我写 SQL 分析这个指标，并生成面向业务的结论
```

- 推荐方式：**按需**：数据查询、分析和可视化任务开启；普通代码或文档任务关闭，避免把非数据问题误导成分析任务。

### [`Operations`](https://claude.com/plugins/operations)

- 核心功能：优化供应商管理、流程文档、变更管理和合规跟踪。
- 使用场景：运营流程梳理、SOP、容量规划、合规记录。
- 典型用法：

```text
用 Operations 把这个流程整理成 SOP，并标出风险和负责人
```

- 推荐方式：**按需**：流程、SOP、供应商或合规跟踪任务开启；不处理运营材料时关闭，减少业务上下文干扰。

### [`Finance`](https://claude.com/plugins/finance)

- 核心功能：支持分录、对账、财务报表和差异分析等财务流程。
- 使用场景：月结、审计准备、报表解释、预算与实际差异分析。
- 典型用法：

```text
用 Finance 分析这份报表的预算与实际差异，并解释主要原因
```

- 推荐方式：**按需**：财务资料处理时开启，并严格控制数据权限；一般业务分析先用 [`Data`](https://claude.com/plugins/data)，涉及会计口径再切到它。

### [`Product Management`](https://claude.com/plugins/product-management)

- 核心功能：写功能规格、规划路线图、综合用户研究并同步干系人。
- 使用场景：PRD、路线图、用户研究总结、竞品和干系人沟通。
- 典型用法：

```text
用 Product Management 把这个想法整理成 PRD 和路线图建议
```

- 推荐方式：**常驻**：产品经理、需求 owner 或长期规划工作建议开启；进入工程实现阶段可与 [`Feature Dev`](https://claude.com/plugins/feature-dev) 分工使用。

### [`Notion`](https://claude.com/plugins/notion)

- 核心功能：集成 Notion 工作区，可搜索页面、创建或更新文档、管理数据库和访问团队知识库。
- 使用场景：团队知识库、项目文档、需求文档、会议记录都在 Notion 的场景。
- 典型用法：

```text
用 Notion 搜索相关项目文档，并更新这份需求说明
```

- 推荐方式：**常驻**：团队核心文档在 Notion 时建议开启；如果只是偶尔查一篇文档，按需授权更稳妥。

影响关系：

1. [`Productivity`](https://claude.com/plugins/productivity)、[`Remember`](https://claude.com/plugins/remember)、[`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management) 都会处理记忆：个人任务用 [`Productivity`](https://claude.com/plugins/productivity)，会话历史用 [`Remember`](https://claude.com/plugins/remember)，项目规则用 [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management)。
2. [`Engineering`](https://claude.com/plugins/engineering) 覆盖站会、代码审查、架构决策和事故响应，可能与 [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit)、[`Code Review`](https://claude.com/plugins/code-review)、[`session-report`](https://claude.com/plugins/session-report) 的部分流程重叠。
3. [`Product Management`](https://claude.com/plugins/product-management) 适合需求和路线图阶段，[`Feature Dev`](https://claude.com/plugins/feature-dev) 适合工程落地阶段；先用前者明确需求，再用后者执行。
4. [`Data`](https://claude.com/plugins/data)、[`Finance`](https://claude.com/plugins/finance)、[`Operations`](https://claude.com/plugins/operations) 都可能处理敏感业务数据，默认按需开启，并在任务结束后关闭。
5. [`Notion`](https://claude.com/plugins/notion) 是知识库入口，不等于记忆插件；它负责读写团队文档，[`Productivity`](https://claude.com/plugins/productivity) / [`Remember`](https://claude.com/plugins/remember) 负责组织个人或会话上下文。

---

## 纠错与贡献

Claude 官方插件市场会更新，欢迎提交 issue 或 PR：

1. 插件链接失效或 slug 变化。
2. 插件市场页面描述变化。
3. 推荐方式需要调整。
4. 插件之间出现新的包含、冲突、互补或替代关系。
5. 插件作者或来源标注变化。

---

## 数据来源

- [Claude Plugin Directory](https://claude.com/plugins)
- [Anthropic official Claude plugins marketplace manifest](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json)
- [Anthropic public Claude plugins](https://github.com/anthropics/claude-plugins-public)

本项目不是 Anthropic 官方仓库，也不是“Claude 官方出品插件”清单；它只是基于 Claude 官方插件市场页面整理的中文导航。
---

# English Version

[![GitHub stars](https://img.shields.io/github/stars/hongsedaima/Claude-Plugin-Management-Skill?style=social)](https://github.com/hongsedaima/Claude-Plugin-Management-Skill/stargazers)
[![Claude Plugin Market](https://img.shields.io/badge/Claude-Plugin%20Market-orange)](https://claude.com/plugins)
[![涓枃鎸囧崡](https://img.shields.io/badge/Guide-%E4%B8%AD%E6%96%87-blue)](#claude-plugin-guide)
[![English](https://img.shields.io/badge/Guide-English-green)](#english-version)

A beginner-friendly guide to the **Claude official plugin marketplace**: what each plugin does, when to use it, and which plugins overlap.

> Updated: 2026-05-25. This project organizes plugins that appear in the [Claude official plugin marketplace](https://claude.com/plugins). It does not mean every plugin is developed by Anthropic or Claude officially. If this project is useful to you, please star it so you can find future updates easily.

---

## Why This Matters

Claude plugins are not better just because you install more of them. Beginners usually face two problems:

1. They do not know which plugins their current project actually needs.
2. They install too many plugins but do not know when to enable, disable, or avoid overlapping ones.

The second problem is often worse. Too many plugins can increase token usage, slow down responses, duplicate work, expand permission scope, create instruction conflicts, and cause the agent to call the wrong tool in the wrong context. More plugins can reduce quality instead of improving it.

This project is not about encouraging full installation. It provides a **project plugin management Skill**: let the agent plan necessary plugin installation, always-on usage, on-demand usage, shutdown timing, and authorization boundaries based on real project needs.

---

## Core Concept: Initialize Project Plugin Management Rules

The real goal is not to list every plugin. The goal is to initialize a set of **project plugin management rules** when starting or onboarding any project.

These rules should be written into `CLAUDE.md`, `AGENTS.md`, or project memory. After that, the agent does not need to re-decide everything every time, and the user does not need to remember each plugin manually. When the project enters scenarios such as feature development, frontend implementation, PR review, bug fixing, pre-release checks, web crawling, GitHub operations, finance/legal/sensitive-data handling, the agent can proactively remind the user to install, enable, disable, or cautiously authorize the right plugin.

Positive impact on agent behavior:

1. From 鈥渋nstall plugins by intuition鈥?to 鈥渋nstall plugins based on project needs.鈥?2. From 鈥渢he user remembers when to toggle plugins鈥?to 鈥渢he agent reminds based on rules.鈥?3. From 鈥渕ore plugins create more confusion鈥?to 鈥渁lways-on, on-demand, and cautious-authorization plugins are managed separately.鈥?4. From 鈥渙ne-time recommendation list鈥?to 鈥渓ong-term collaboration rules saved in project memory.鈥?
The final goal is to minimize the user's cognitive and memory load: the user only explains the project needs; plugin choice, combinations, enable/disable timing, and memory persistence are handled by the agent.

---

## Install This Skill

Beginners do not need to read the whole plugin list manually or copy a long prompt. Ask your agent to install and use the Skill in this repository:

```text
Please install and use this Skill: https://github.com/hongsedaima/Claude-Plugin-Management-Skill/tree/main/skills/project-plugin-management
Then initialize project plugin management rules for the current project based on its needs.
```

After installation, invoke it like this:

```text
Use $project-plugin-management to initialize plugin management rules for this project.
```

The Skill follows this workflow: read project context -> ask for missing information -> recommend necessary plugins -> separate always-on / on-demand / not-needed / cautious-authorization plugins -> generate project plugin management rules -> write them into project memory after confirmation.

---

## Beginner Quick Picks

| Goal | Start With These Plugins |
| -- | -- |
| Make Claude remember project rules | [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management), [`Remember`](https://claude.com/plugins/remember), [`Productivity`](https://claude.com/plugins/productivity) |
| Build a new feature | [`Feature Dev`](https://claude.com/plugins/feature-dev), [`Superpowers`](https://claude.com/plugins/superpowers), [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) |
| Build frontend UI | [`Frontend Design`](https://claude.com/plugins/frontend-design), [`Design`](https://claude.com/plugins/design), [`Playwright`](https://claude.com/plugins/playwright) |
| Improve code quality | [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp), [`Serena`](https://claude.com/plugins/serena), [`Security Guidance`](https://claude.com/plugins/security-guidance), [`Semgrep`](https://claude.com/plugins/semgrep) |
| Review PRs or prepare for release | [`Code Review`](https://claude.com/plugins/code-review), [`CodeRabbit`](https://claude.com/plugins/coderabbit), [`Optibot Code Review`](https://claude.com/plugins/optibot), [`sonarqube`](https://claude.com/plugins/sonarqube) |

---

## Common Combinations

| Scenario | Recommended Combination |
| -- | -- |
| Long-running code project | [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management) + [`Hookify`](https://claude.com/plugins/hookify) + [`Security Guidance`](https://claude.com/plugins/security-guidance) + the relevant language LSP |
| New feature development | [`Feature Dev`](https://claude.com/plugins/feature-dev) + [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp) / [`Serena`](https://claude.com/plugins/serena) + [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) |
| Frontend page development | [`Frontend Design`](https://claude.com/plugins/frontend-design) + [`Playwright`](https://claude.com/plugins/playwright) + [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) |
| Pre-release checks | [`Semgrep`](https://claude.com/plugins/semgrep) + [`Sonatype Guide`](https://claude.com/plugins/sonatype-guide) + [`Code Review`](https://claude.com/plugins/code-review) or [`Optibot Code Review`](https://claude.com/plugins/optibot) |
| Large codebase debugging | [`Serena`](https://claude.com/plugins/serena) + [`Sourcegraph`](https://claude.com/plugins/sourcegraph) or [`Greptile`](https://claude.com/plugins/greptile) + [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) |
| Requirement to delivery | [`Product Management`](https://claude.com/plugins/product-management) + [`Feature Dev`](https://claude.com/plugins/feature-dev) + [`GitHub`](https://claude.com/plugins/github) + [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit) |

---

## How To Read This Guide

- **Always-on**: Keep enabled by default for matching projects, roles, or team workflows when the ongoing benefit is greater than context and permission cost.
- **On-demand**: Enable only for specific tasks. These plugins often have higher permissions, heavier context, stronger behavior changes, or narrow use cases.
- **Typical usage**: Each prompt is placed in a separate code block so it can be copied directly on GitHub.
- **Impact relationships**: Each category lists plugin overlaps, substitutions, conflicts, and permission implications.

Plugin details use a card-style layout instead of wide tables. Tables are good for quick comparison, but plugin descriptions, recommendations, and usage prompts are long; cards are easier to read on GitHub and mobile screens.

---

## Workflow Enhancement

### [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management)

- Core function: Maintain `CLAUDE.md`: audit quality, capture session learnings, and keep project memory current.
- Use when: Long-running projects, frequently changing team conventions, or when Claude should remember engineering rules.
- Typical usage:

```text
Check and update this project's CLAUDE.md, and save the rules we just agreed on.
```

- Recommendation: **Always-on** for code projects. Use it to maintain project-level rules and lessons learned. Do not introduce project memory for one-off Q&A or temporary scripts.

### [`Superpowers`](https://claude.com/plugins/superpowers)

- Core function: Adds brainstorming, subagent-driven development, code review, systematic debugging, red/green TDD, and skill authoring.
- Use when: Complex requirement breakdown, TDD, debugging roadblocks, or when Claude should plan development more actively.
- Typical usage:

```text
Use Superpowers to break down this requirement and implement it with a TDD workflow.
```

- Recommendation: **On-demand** for complex features, TDD, or systematic debugging. It is too heavy for small copy edits or minor fixes.

### [`Feature Dev`](https://claude.com/plugins/feature-dev)

- Core function: Organizes complete feature development with exploration, design, implementation, and review agents.
- Use when: A full feature needs to move from requirement to code, not just a small isolated change.
- Typical usage:

```text
Use Feature Dev to guide this new feature from exploration and design to implementation.
```

- Recommendation: **On-demand** from feature kickoff to merge readiness. Skip it when the requirement is tiny or the implementation path is already clear.

### [`Claude Code Setup`](https://claude.com/plugins/claude-code-setup)

- Core function: Analyze a codebase and recommend Claude Code automation such as hooks, skills, MCP servers, and subagents.
- Use when: Onboarding Claude Code to a new project or reorganizing automation for an existing one.
- Typical usage:

```text
Set up this project and recommend suitable Claude Code automations.
```

- Recommendation: **On-demand** during project initialization, stack changes, or periodic workflow audits. It is a diagnostic tool, not a daily always-on plugin.

### [`Remember`](https://claude.com/plugins/remember)

- Core function: Extracts, summarizes, and compresses conversations into layered logs for persistent Claude Code memory.
- Use when: Long-term collaboration across days or weeks needs historical context.
- Typical usage:

```text
Save the key decisions from this session into long-term memory so we can continue next time.
```

- Recommendation: **Always-on** for long-running projects or collaborations. Disable for short tasks to avoid accumulating low-value memory.

### [`Skill Creator`](https://claude.com/plugins/skill-creator)

- Core function: Create, improve, evaluate, and benchmark Claude skills.
- Use when: You want to package a company workflow, personal method, or tool procedure as a reusable skill.
- Typical usage:

```text
Turn this workflow into a reusable Claude skill.
```

- Recommendation: **On-demand** only when creating, evaluating, or maintaining skills. It is not needed for normal coding.

### [`Playwright`](https://claude.com/plugins/playwright)

- Core function: Microsoft Playwright MCP for browser automation, screenshots, forms, clicks, and end-to-end tests.
- Use when: Web app testing, screenshot review, user-path reproduction, or automated form interaction.
- Typical usage:

```text
Use Playwright to open the local page, take screenshots, and verify the main interactions.
```

- Recommendation: **On-demand** when real browser interaction, screenshots, or E2E validation are needed. Disable during ordinary code editing to reduce permission and execution cost.

### [`Firecrawl`](https://claude.com/plugins/firecrawl)

- Core function: Convert web pages, sites, or search results into LLM-ready Markdown or structured data.
- Use when: Collecting competitor docs, organizing web materials, or extracting information from multiple sources.
- Typical usage:

```text
Use Firecrawl to crawl this website and organize it into Markdown suitable for Claude.
```

- Recommendation: **On-demand** for external web collection and material organization. Confirm copyright, account-page, and privacy boundaries first.

### [`session-report`](https://claude.com/plugins/session-report)

- Core function: Generate an explorable HTML report from local Claude transcripts, including tokens, cache, subagents, skills, and expensive prompts.
- Use when: Reviewing the cost, efficiency, and context structure of a Claude Code session.
- Typical usage:

```text
Generate a session report for this Claude Code session and analyze token and cache usage.
```

- Recommendation: **On-demand** after a session, when cost looks abnormal, or when optimizing workflow. It does not improve real-time development.

Impact relationships:

1. [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management), [`Remember`](https://claude.com/plugins/remember), and [`Productivity`](https://claude.com/plugins/productivity) all relate to memory. Use the first for project rules, the second for session history, and the third for personal tasks and work context.
2. [`Feature Dev`](https://claude.com/plugins/feature-dev) covers exploration, design, implementation, and review. [`Superpowers`](https://claude.com/plugins/superpowers) is stronger for TDD, debugging, and subagent development.
3. [`Claude Code Setup`](https://claude.com/plugins/claude-code-setup) is a diagnostic and recommendation tool, not a replacement for other plugins.
4. [`Playwright`](https://claude.com/plugins/playwright) and [`Firecrawl`](https://claude.com/plugins/firecrawl) access external web or browser environments, so use them on demand.
5. [`Skill Creator`](https://claude.com/plugins/skill-creator) and [`Superpowers`](https://claude.com/plugins/superpowers) can both help with skill authoring; prefer [`Skill Creator`](https://claude.com/plugins/skill-creator) for formal skill creation and evaluation.
6. [`session-report`](https://claude.com/plugins/session-report) is for retrospective analysis and does not need to stay enabled.

---

## Agent Constraints

### [`Hookify`](https://claude.com/plugins/hookify)

- Core function: Create hooks from Markdown rules to prevent Claude from violating project conventions.
- Use when: Enforcing code style, limiting dangerous commands, or banning wrong libraries or outdated APIs.
- Typical usage:

```text
Create Hookify constraints from these project rules so Claude will not violate them later.
```

- Recommendation: **Always-on** once rules are stable. Start with a smaller scope while rules are still being explored.

### [`Ralph Loop`](https://claude.com/plugins/ralph-loop)

- Core function: Let Claude repeatedly work on the same task, see prior results, and iterate until completion.
- Use when: A task needs repeated attempts, fixes, and validation.
- Typical usage:

```text
Use Ralph Loop to keep fixing this issue until tests pass or a clear blocker appears.
```

- Recommendation: **On-demand** only for tasks with clear boundaries and acceptance criteria. Do not let it loop freely around remote writes, money, accounts, or large-scale changes.

Impact relationships:

1. [`Hookify`](https://claude.com/plugins/hookify) constrains behavior; [`Ralph Loop`](https://claude.com/plugins/ralph-loop) accelerates iteration. When used together, define stop conditions, allowed commands, and acceptance criteria.
2. [`Hookify`](https://claude.com/plugins/hookify) can turn `CLAUDE.md` rules into executable guardrails.
3. Avoid long-running [`Ralph Loop`](https://claude.com/plugins/ralph-loop) with high-permission plugins such as [`GitHub`](https://claude.com/plugins/github), [`Playwright`](https://claude.com/plugins/playwright), or [`Firecrawl`](https://claude.com/plugins/firecrawl).

---

## Frontend Design

### [`Frontend Design`](https://claude.com/plugins/frontend-design)

- Core function: Generate production-grade frontend interfaces with higher design quality and less generic AI style.
- Use when: Creating pages, components, interactions, or visually complete frontend code from text requirements.
- Typical usage:

```text
Use Frontend Design to design and implement this page while avoiding generic AI style.
```

- Recommendation: **On-demand** for UI, components, landing pages, or interaction prototypes. Disable for backend, scripting, or security scanning tasks.

### [`Design`](https://claude.com/plugins/design)

- Core function: Accelerate design critique, UX writing, accessibility audits, research synthesis, and developer handoff.
- Use when: Reviewing visuals, organizing design systems, checking accessibility, or turning research into design decisions.
- Typical usage:

```text
Use Design to review this interface, focusing on UX copy, accessibility, and handoff issues.
```

- Recommendation: **On-demand** during design review, accessibility audit, UX writing, or handoff. Keep only necessary context once implementation begins.

Impact relationships:

1. [`Design`](https://claude.com/plugins/design) is closer to design review and handoff; [`Frontend Design`](https://claude.com/plugins/frontend-design) is closer to frontend UI generation.
2. After [`Frontend Design`](https://claude.com/plugins/frontend-design) generates code, pair it with [`Playwright`](https://claude.com/plugins/playwright) for screenshots/E2E verification or [`Playground`](https://claude.com/plugins/playground) for interactive previews.
3. Both influence Claude's taste and expression style, so do not keep them always-on for backend, data, or security tasks.

---

## Coding

### [`Playground`](https://claude.com/plugins/playground)

- Core function: Generate self-contained HTML playgrounds with controls, live preview, and copyable output.
- Use when: Creating quick interactive prototypes, data explorers, concept maps, or document critique tools.
- Typical usage:

```text
Create an interactive HTML playground so I can adjust parameters and preview results.
```

- Recommendation: **On-demand** for visual prototypes or one-off analysis panels. Production code still needs normal engineering.

### [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp)

- Core function: Language-server code intelligence for TypeScript and JavaScript.
- Use when: Type, reference, diagnostic, and refactoring support is needed in TS/JS projects.
- Typical usage:

```text
Use TypeScript LSP to check type errors and reference issues in this change.
```

- Recommendation: **Always-on** for TS/JS projects. Disable for non-TS/JS projects.

### [`sonarqube`](https://claude.com/plugins/sonarqube)

- Core function: Run SonarQube quality/security rules, secret scanning, and quality gates in the agent coding loop.
- Use when: Enterprise quality gates, merge checks, or multi-language quality governance are needed.
- Typical usage:

```text
Use sonarqube to check code quality, security risks, and quality gates for this change.
```

- Recommendation: **On-demand** before merge/release or in high-standard enterprise projects. Avoid always-on use during rapid prototyping.

### [`Code Simplifier`](https://claude.com/plugins/code-simplifier)

- Core function: Simplify recently modified code while preserving behavior, clarity, and consistency.
- Use when: Cleaning up after a feature is complete and tests pass.
- Typical usage:

```text
Simplify the recently modified code without changing behavior.
```

- Recommendation: **On-demand** after tests pass and feature boundaries are stable. Avoid premature simplification while requirements are still changing.

### [`Serena`](https://claude.com/plugins/serena)

- Core function: Semantic code understanding, refactoring advice, and codebase navigation through language server protocol.
- Use when: Understanding large codebases, cross-file refactoring, or locating complex call chains.
- Typical usage:

```text
Use Serena to analyze this function's call chain and propose a safe refactor.
```

- Recommendation: **Always-on** for large or long-running codebases. Use on demand for small scripts or single-file tasks.

### [`Security Guidance`](https://claude.com/plugins/security-guidance)

- Core function: Warn about command injection, XSS, and unsafe code patterns while editing files.
- Use when: Developing Web, API, auth, input handling, or script-execution code.
- Typical usage:

```text
Check whether this code has command injection, XSS, or unsafe patterns.
```

- Recommendation: **Always-on** for most code projects as a lightweight security guardrail. Disable for non-code writing tasks.

### [`Semgrep`](https://claude.com/plugins/semgrep)

- Core function: Detect security vulnerabilities in real time and guide Claude toward safer code.
- Use when: Security-sensitive code, Web/API work, or pre-merge security checks.
- Typical usage:

```text
Use Semgrep to scan this change for security vulnerabilities and suggest fixes.
```

- Recommendation: **Always-on** for security-sensitive projects. Watch for duplicate alerts if used with heavier security platforms.

### [`Aikido Security`](https://claude.com/plugins/aikido)

- Core function: SAST, secret, and IaC vulnerability detection through Aikido MCP.
- Use when: Pre-release security scanning, secret leak checks, or infrastructure configuration review.
- Typical usage:

```text
Use Aikido Security to scan SAST, secret leaks, and IaC risks.
```

- Recommendation: **On-demand** before release, during security audits, or for IaC changes. Daily small edits can rely on lighter security reminders first.

### [`Sonatype Guide`](https://claude.com/plugins/sonatype-guide)

- Core function: Software supply-chain and dependency security analysis with vulnerability detection and safe version recommendations.
- Use when: Adding, upgrading, or reviewing npm/pip/Maven and other dependencies.
- Typical usage:

```text
Use Sonatype Guide to check these dependencies for vulnerabilities and recommend safe versions.
```

- Recommendation: **On-demand** when changing or reviewing dependencies. It does not replace source-code scanning.

Impact relationships:

1. [`TypeScript LSP`](https://claude.com/plugins/typescript-lsp), [`Serena`](https://claude.com/plugins/serena), [`Sourcegraph`](https://claude.com/plugins/sourcegraph), and [`Greptile`](https://claude.com/plugins/greptile) all help understand code. Use them by scope: language intelligence, local semantic navigation, cross-repo search, or natural-language repo search.
2. [`Security Guidance`](https://claude.com/plugins/security-guidance) is lightweight; [`Semgrep`](https://claude.com/plugins/semgrep) is rule-based scanning; [`Aikido Security`](https://claude.com/plugins/aikido) covers SAST/secrets/IaC; [`sonarqube`](https://claude.com/plugins/sonarqube) covers quality and security.
3. [`Sonatype Guide`](https://claude.com/plugins/sonatype-guide) handles dependencies and supply chain only.
4. Use [`Code Simplifier`](https://claude.com/plugins/code-simplifier) after functionality and tests stabilize.
5. [`sonarqube`](https://claude.com/plugins/sonarqube) hooks may run after edits, so it is better for quality-gated projects than rapid prototypes.

---

## Code Management

### [`GitHub`](https://claude.com/plugins/github)

- Core function: GitHub MCP for issues, PRs, code review, repo search, and GitHub API access.
- Use when: Managing issues, PRs, repo search, and repository automation inside Claude Code.
- Typical usage:

```text
Use GitHub to check open PRs in this repository and summarize what needs attention.
```

- Recommendation: **Always-on** if GitHub is the primary collaboration platform. Be careful with token permissions and sensitive repositories.

### [`Commit Commands`](https://claude.com/plugins/commit-commands)

- Core function: Commands for commit, push, and PR workflows.
- Use when: Standardizing commits, pushing changes, and opening PRs after code is done.
- Typical usage:

```text
Review the diff, generate a suitable commit, and prepare push and PR steps.
```

- Recommendation: **Always-on** for projects with frequent commits. Still run tests and review diffs before automated commits.

### [`Greptile`](https://claude.com/plugins/greptile)

- Core function: Natural-language repository search for code, dependencies, and architecture context.
- Use when: Asking where a feature is implemented, who calls a module, or what a logic path depends on.
- Typical usage:

```text
Use Greptile to find where user login is implemented and which modules it depends on.
```

- Recommendation: **On-demand** for large or unfamiliar repositories. For small repos, local search and LSP may be enough.

### [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit)

- Core function: PR review agents for comments, tests, error handling, type design, code quality, and simplification.
- Use when: Systematic PR checks before merge.
- Typical usage:

```text
Use PR Review Toolkit to review this PR, focusing on tests, error handling, and type design.
```

- Recommendation: **On-demand** when opening or preparing to merge a PR, especially when the change has broad impact.

Impact relationships:

1. [`GitHub`](https://claude.com/plugins/github) covers issues, PRs, and repo APIs; [`Commit Commands`](https://claude.com/plugins/commit-commands) focuses on local Git workflow.
2. [`Greptile`](https://claude.com/plugins/greptile) and [`Sourcegraph`](https://claude.com/plugins/sourcegraph) both support code search. Use local tools or [`Serena`](https://claude.com/plugins/serena) for current-repo questions, and [`Sourcegraph`](https://claude.com/plugins/sourcegraph) for cross-repo work.
3. [`PR Review Toolkit`](https://claude.com/plugins/pr-review-toolkit), [`Code Review`](https://claude.com/plugins/code-review), [`CodeRabbit`](https://claude.com/plugins/coderabbit), and [`Optibot Code Review`](https://claude.com/plugins/optibot) all participate in review. Use one or layer them by risk.
4. Use [`Commit Commands`](https://claude.com/plugins/commit-commands) after tests, static checks, and review.

---

## Bug Fixing

### [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp)

- Core function: Control and inspect live Chrome: performance traces, network requests, console logs, source maps, and browser actions.
- Use when: Debugging page performance, API calls, console errors, or real browser state.
- Typical usage:

```text
Use Chrome DevTools to connect to the current page and inspect console, network, and performance issues.
```

- Recommendation: **On-demand** when connecting to a live browser, analyzing performance, or inspecting network requests.

### [`Code Review`](https://claude.com/plugins/code-review)

- Core function: PR code review with specialized agents and confidence filtering.
- Use when: Checking obvious bugs, regression risk, and maintainability before merge.
- Typical usage:

```text
Use Code Review to review this PR and list high-confidence issues with fixes.
```

- Recommendation: **On-demand** during PR review or after important changes. Avoid running it after every tiny edit.

### [`CodeRabbit`](https://claude.com/plugins/coderabbit)

- Core function: AI code review with 40+ analyzers, AST, code graph, and project rules.
- Use when: Complex, security-sensitive, or high-impact code needs an external review perspective.
- Typical usage:

```text
Use CodeRabbit to perform a deep code review of this change, focusing on security and edge cases.
```

- Recommendation: **On-demand** before high-risk merges. It does not replace tests, type checks, or human judgment.

### [`Optibot Code Review`](https://claude.com/plugins/optibot)

- Core function: Review local changes, branch diffs, or patches for production bugs, business-logic issues, and security vulnerabilities.
- Use when: Reviewing uncommitted changes, branch comparisons, patch files, or CI review.
- Typical usage:

```text
Use Optibot to review my changes, focusing on production bugs, business logic issues, and security vulnerabilities.
```

- Recommendation: **On-demand** before release, for local diff review, or CI automation. It overlaps with [`CodeRabbit`](https://claude.com/plugins/coderabbit); choose one or layer by risk.

### [`Sourcegraph`](https://claude.com/plugins/sourcegraph)

- Core function: Cross-codebase search, reference tracing, refactor impact analysis, incident investigation, and targeted security sweeps.
- Use when: Locating bugs across repositories, understanding history, or tracing references.
- Typical usage:

```text
Use Sourcegraph to search cross-repository callers and historical changes for this API.
```

- Recommendation: **On-demand** for multi-repo, large-codebase, or incident investigation work.

Impact relationships:

1. [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp) and [`Playwright`](https://claude.com/plugins/playwright) both operate browsers: DevTools for live debugging/performance, Playwright for repeatable tests.
2. [`Code Review`](https://claude.com/plugins/code-review), [`CodeRabbit`](https://claude.com/plugins/coderabbit), and [`Optibot Code Review`](https://claude.com/plugins/optibot) are all review tools with different focuses.
3. [`Sourcegraph`](https://claude.com/plugins/sourcegraph), [`Greptile`](https://claude.com/plugins/greptile), and [`Serena`](https://claude.com/plugins/serena) all find code. Use [`Sourcegraph`](https://claude.com/plugins/sourcegraph) for cross-repo and incident investigation, [`Serena`](https://claude.com/plugins/serena) for local semantic refactoring.
4. Recommended bug-fix flow: reproduce with [`Chrome DevTools`](https://claude.com/plugins/chrome-devtools-mcp), locate with [`Serena`](https://claude.com/plugins/serena) / [`Sourcegraph`](https://claude.com/plugins/sourcegraph), then review with [`Code Review`](https://claude.com/plugins/code-review) or [`Optibot Code Review`](https://claude.com/plugins/optibot).

---

## General Office and Business Plugins

### [`Productivity`](https://claude.com/plugins/productivity)

- Core function: Manage tasks, plan the day, and build persistent work-context memory.
- Use when: Personal workflows, calendar/task sync, and context organization.
- Typical usage:

```text
Organize today's tasks and context, then tell me the top three things to do next.
```

- Recommendation: **Always-on** if you use Claude as a daily work assistant. Keep memory boundaries clear with [`Remember`](https://claude.com/plugins/remember) and [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management).

### [`Engineering`](https://claude.com/plugins/engineering)

- Core function: Support standups, code review, architecture decisions, incident response, and technical documentation.
- Use when: Engineering leads, team collaboration, and engineering process management.
- Typical usage:

```text
Use Engineering to summarize this architecture decision and draft an ADR.
```

- Recommendation: **Always-on** for engineering management, team collaboration, and technical documentation. Use on demand for pure coding tasks.

### [`Data`](https://claude.com/plugins/data)

- Core function: Write SQL, explore datasets, generate insights, and build visualizations/dashboards.
- Use when: Data analysis, reporting, metric interpretation, and stakeholder data stories.
- Typical usage:

```text
Use Data to write SQL for this metric and generate a business-facing conclusion.
```

- Recommendation: **On-demand** for data tasks. Disable for ordinary coding or writing to avoid forcing non-data problems into analysis mode.

### [`Operations`](https://claude.com/plugins/operations)

- Core function: Optimize vendor management, process documentation, change management, and compliance tracking.
- Use when: Process mapping, SOPs, capacity planning, and compliance records.
- Typical usage:

```text
Use Operations to turn this process into an SOP and mark risks and owners.
```

- Recommendation: **On-demand** for operations or process-management tasks.

### [`Finance`](https://claude.com/plugins/finance)

- Core function: Support journal entries, reconciliation, financial statements, and variance analysis.
- Use when: Month-end close, audit prep, statement explanation, and budget-vs-actual analysis.
- Typical usage:

```text
Use Finance to analyze budget versus actuals in this report and explain the main causes.
```

- Recommendation: **On-demand** for financial materials, with strict data permission boundaries. Use [`Data`](https://claude.com/plugins/data) first for general business analytics, then switch to this when accounting concepts matter.

### [`Product Management`](https://claude.com/plugins/product-management)

- Core function: Write feature specs, plan roadmaps, synthesize user research, and update stakeholders.
- Use when: PRDs, roadmaps, user research summaries, competitive analysis, and stakeholder communication.
- Typical usage:

```text
Use Product Management to turn this idea into a PRD and roadmap suggestion.
```

- Recommendation: **Always-on** for product managers, requirement owners, or long-term planning. Pair with [`Feature Dev`](https://claude.com/plugins/feature-dev) during engineering implementation.

### [`Notion`](https://claude.com/plugins/notion)

- Core function: Integrate a Notion workspace, search pages, create/update documents, manage databases, and access team knowledge.
- Use when: Team knowledge bases, project docs, requirement docs, and meeting notes live in Notion.
- Typical usage:

```text
Use Notion to search related project docs and update this requirement document.
```

- Recommendation: **Always-on** if core team documentation lives in Notion. If you only need one document occasionally, authorize it on demand.

Impact relationships:

1. [`Productivity`](https://claude.com/plugins/productivity), [`Remember`](https://claude.com/plugins/remember), and [`CLAUDE.md Management`](https://claude.com/plugins/claude-md-management) all handle memory: personal tasks, session history, and project rules respectively.
2. [`Engineering`](https://claude.com/plugins/engineering) overlaps with PR review, code review, and session reporting workflows.
3. [`Product Management`](https://claude.com/plugins/product-management) fits requirement and roadmap stages; [`Feature Dev`](https://claude.com/plugins/feature-dev) fits engineering delivery.
4. [`Data`](https://claude.com/plugins/data), [`Finance`](https://claude.com/plugins/finance), and [`Operations`](https://claude.com/plugins/operations) may process sensitive business data, so enable them only when needed and disable them after the task.
5. [`Notion`](https://claude.com/plugins/notion) is a knowledge-base entry point, not a memory plugin.

---

## Corrections and Contributions

The Claude plugin marketplace changes over time. Issues and PRs are welcome for:

1. Broken plugin links or slug changes.
2. Updated marketplace descriptions.
3. Recommendation changes.
4. New overlaps, conflicts, complements, or substitutions between plugins.
5. Plugin author or source changes.

---

## Sources

- [Claude Plugin Directory](https://claude.com/plugins)
- [Anthropic official Claude plugins marketplace manifest](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json)
- [Anthropic public Claude plugins](https://github.com/anthropics/claude-plugins-public)

This project is not an official Anthropic repository and is not a list of 鈥減lugins officially made by Claude.鈥?It is an independent guide based on Claude official plugin marketplace pages.
