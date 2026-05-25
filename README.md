# Claude Plugin Guide

[![GitHub stars](https://img.shields.io/github/stars/hongsedaima/Claude-Plugin?style=social)](https://github.com/hongsedaima/Claude-Plugin/stargazers)
[![Claude Plugin Market](https://img.shields.io/badge/Claude-Plugin%20Market-orange)](https://claude.com/plugins)
[![中文指南](https://img.shields.io/badge/Guide-%E4%B8%AD%E6%96%87-blue)](#claude-plugin-guide)

一份面向新手的 **Claude 官方插件市场**速查表：每个插件做什么、什么时候开、哪些插件会互相覆盖。

> 更新时间：2026-05-25。本项目整理的是 [Claude 官方插件市场](https://claude.com/plugins) 中出现的插件，不表示这些插件都由 Anthropic 或 Claude 官方开发。插件市场里既有 Anthropic 维护的插件，也有第三方作者或公司发布的插件。若这份表帮你少踩坑，欢迎点 Star，方便以后回来看更新。

---

## 先复制这段提示词

新手不需要先手工读完整文档。把下面这段提示词发给 Claude Code、Codex 或其他项目内 Agent，让它先理解当前项目，再基于本指南给出插件安装和启停建议。

```text
请帮我为当前项目选择 Claude 官方插件市场中的插件，并把插件使用规则沉淀到项目记忆里。

请按下面流程执行：

1. 先阅读这个插件指南：https://github.com/hongsedaima/Claude-Plugin
2. 检查当前项目是否已经具备足够的基本信息。至少需要知道：项目目标、主要技术栈、语言/框架、包管理器、测试方式、部署方式、当前开发阶段、正在推进的任务、是否有 README/CLAUDE.md/AGENTS.md、是否使用 GitHub/Notion/浏览器自动化/外部网页抓取、是否涉及安全/财务/法律/敏感数据。
3. 如果这些基本信息不足，不要直接推荐插件。请先向我提出最少但必要的问题，补齐判断所需信息；能从项目文件中读取到的信息不要重复问我。
4. 基本信息足够后，结合项目类型、当前阶段、风险点和我的实际目标，给出插件建议，而不是照单全装。
5. 输出四类清单：
   - 必装且建议常驻：安装后默认开启，并说明原因。
   - 建议安装但按需开启：说明什么任务或场景下再开启。
   - 暂不建议安装：说明为什么现在不需要。
   - 需要谨慎授权的插件：涉及浏览器、网页抓取、GitHub、外部服务、财务/法律/敏感数据时单独列出。
6. 对每个推荐插件说明：插件名、官方插件页、解决的问题、常驻/按需、典型用法、可能重叠或冲突的插件。
7. 基于本指南的场景和用法，生成一段“项目记忆规则”。这段规则必须能让后续 Agent 做到：
   - 遇到新功能开发、前端页面、PR 审查、修 bug、上线前检查、长期记忆、项目规则维护、网页抓取、GitHub 操作、法律/财务/敏感数据等场景时，主动提醒我安装或开启对应插件。
   - 如果环境允许，并且我已授权，自动完成插件安装、基础设置和启停建议。
   - 安装插件后，提醒我设置哪些插件常驻、哪些插件按需开启、哪些插件任务结束后应关闭。
   - 遇到功能重叠的插件时，先说明取舍，不要默认全部开启。
   - 遇到高权限或敏感数据插件时，先提醒授权风险，再等待确认。
8. 如果当前项目有 CLAUDE.md、AGENTS.md、项目记忆文件或类似长期上下文，请把第 7 步生成的规则写入合适位置。写入前先展示目标文件路径和拟写入内容；如果我确认，帮我合并写入，不要覆盖已有团队约定。如果没有合适文件，先建议创建位置并等待我确认。
9. 如果当前环境支持插件安装或配置，请先给出将要执行的命令和影响范围；在我确认后再安装、启用或写配置。如果我已经明确授权你自动执行，则直接完成安装和基础设置，并在最后列出你改了什么。
10. 最后给我一份“日常使用规则”：哪些插件平时保持开启，哪些插件只在写前端、做 PR、修 bug、上线前检查、整理文档时开启，哪些插件任务结束后要关闭。

请用中文输出，结论优先，不要泛泛介绍插件。
```

如果你只想先得到推荐、不希望 Agent 自动安装，用这个更保守的版本：

```text
请阅读 https://github.com/hongsedaima/Claude-Plugin ，再检查当前项目是否已有足够基本信息，包括项目目标、技术栈、开发阶段、当前任务、测试/部署方式、长期记忆文件、外部服务和敏感数据边界。

如果信息不足，请先向我提出最少但必要的问题，补齐后再推荐插件。只输出插件推荐清单和项目记忆规则，不要安装插件，也不要修改任何配置或文件。

请按“必装常驻 / 安装但按需 / 暂不安装 / 需要谨慎授权”四类给出建议，并说明每个插件的典型用法、启停策略和可能重叠的插件。

最后额外给出一段“建议写入 CLAUDE.md/AGENTS.md/项目记忆的规则”：要求后续 Agent 在遇到对应场景时主动提醒安装、开启、关闭或谨慎授权插件，但不要实际写入。
```

推荐先用“只推荐版”跑一次；确认清单合理后，再让 Agent 执行安装和设置。'

如果你已经确定要让 Agent 长期记住这套策略，也可以单独复制下面这段：

```text
请根据当前项目实际情况，把 Claude 插件使用策略整理成一段适合写入项目记忆的规则。

要求：

1. 写入前先确认项目基本信息是否足够，包括项目目标、技术栈、当前阶段、测试/部署方式、团队协作方式、敏感数据边界和已有长期记忆文件。如果信息不足，先向我提问补齐。
2. 优先写入 CLAUDE.md、AGENTS.md 或本项目已经使用的长期记忆文件；如果没有合适文件，先建议创建位置，不要擅自新建。
3. 内容必须包括：常驻插件、按需插件、触发场景、谨慎授权插件、不要同时开启的插件组合、安装后启停检查清单。
4. 规则要面向后续 Agent 使用，写成可执行约束。例如：当开始新功能开发时提醒开启 Feature Dev；当进入 PR 审查时提醒开启 PR Review Toolkit 或 Code Review；当前端调试需要浏览器时提醒开启 Playwright 或 Chrome DevTools；当任务结束后提醒关闭高权限插件。
5. 如果环境允许且我已授权，后续 Agent 可以根据这些规则自动安装、启用、关闭或调整插件；未授权时只能提醒并等待确认。
6. 写入前先展示拟写入内容和目标文件路径，等我确认后再修改文件。
7. 如果项目已经有相关规则，请合并更新，不要覆盖已有团队约定。
```
'

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