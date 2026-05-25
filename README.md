# Claude Official Plugin Guide

[![GitHub stars](https://img.shields.io/github/stars/hongsedaima/Claude-Offical-Plugin?style=social)](https://github.com/hongsedaima/Claude-Offical-Plugin/stargazers)
[![Claude Plugins](https://img.shields.io/badge/Claude-Plugins-orange)](https://claude.com/plugins)
[![中文指南](https://img.shields.io/badge/Guide-%E4%B8%AD%E6%96%87-blue)](#claude-official-plugin-guide)

一份面向新手的 Claude 官方插件速查表：每个插件做什么、什么时候开、哪些插件会互相覆盖。

> 更新时间：2026-05-25。插件信息以 [Claude 插件目录](https://claude.com/plugins) 与 Anthropic 官方插件仓库为主要来源；第三方插件只要出现在 Claude 官方插件页，也纳入本表。若本项目帮你少踩坑，欢迎点 Star，方便以后回来看更新。

## 怎么读这份表

- **常驻**：建议在匹配的项目或角色中默认开启，持续收益大于干扰。
- **按需**：只在具体任务中开启。通常因为权限更高、上下文更重、会改变 Claude 行为，或只适合某类工作。
- **影响关系**：每个分类表格下方都列出插件之间的包含、重叠、冲突或组合方式。

## 新手快速选择

| 目标 | 优先看这些插件 |
| -- | -- |
| 想让 Claude 记住项目规则 | [CLAUDE.md Management](https://claude.com/plugins/claude-md-management)、[Remember](https://claude.com/plugins/remember)、[Productivity](https://claude.com/plugins/productivity) |
| 想做新功能 | [Feature Dev](https://claude.com/plugins/feature-dev)、[Superpowers](https://claude.com/plugins/superpowers)、[PR Review Toolkit](https://claude.com/plugins/pr-review-toolkit) |
| 想做前端 | [Frontend Design](https://claude.com/plugins/frontend-design)、[Design](https://claude.com/plugins/design)、[Playwright](https://claude.com/plugins/playwright) |
| 想提高代码质量 | [TypeScript LSP](https://claude.com/plugins/typescript-lsp)、[Serena](https://claude.com/plugins/serena)、[Security Guidance](https://claude.com/plugins/security-guidance)、[Semgrep](https://claude.com/plugins/semgrep) |
| 想做 PR 或上线前检查 | [Code Review](https://claude.com/plugins/code-review)、[CodeRabbit](https://claude.com/plugins/coderabbit)、[Optibot Code Review](https://claude.com/plugins/optibot)、[sonarqube](https://claude.com/plugins/sonarqube) |

## 增强工作流

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [CLAUDE.md Management](https://claude.com/plugins/claude-md-management) | 维护 CLAUDE.md：审查质量、沉淀会话经验、让项目记忆保持更新。 | 长期项目、团队约定频繁变化、希望 Claude 自动记住工程规则。 | 常驻：项目内默认开启，作为项目级记忆的主入口。 |
| [Superpowers](https://claude.com/plugins/superpowers) | 增强头脑风暴、子代理开发、代码审查、系统化调试、红绿 TDD 和技能编写能力。 | 复杂需求拆解、TDD、调试卡住、想让 Claude 更主动地规划开发。 | 按需：做复杂功能或 TDD 时开启；与 Feature Dev 部分重叠。 |
| [Feature Dev](https://claude.com/plugins/feature-dev) | 用探索、设计、实现、评审代理组织完整的新功能开发流程。 | 从需求到代码落地的一整段功能开发，而不是零散小改动。 | 按需：新功能启动时开启，流程完成后关闭。 |
| [Claude Code Setup](https://claude.com/plugins/claude-code-setup) | 分析代码库，推荐 hooks、skills、MCP servers、subagents 等 Claude Code 自动化配置。 | 新项目接入 Claude Code，或想重整现有项目的自动化能力。 | 按需：项目初始化或季度巡检时运行。 |
| [Remember](https://claude.com/plugins/remember) | 把对话抽取、总结、压缩为分层日志，形成 Claude Code 的持续记忆。 | 跨天、跨周的长期协作，需要保留历史上下文。 | 常驻：长期项目开启；一次性任务不建议开。 |
| [Skill Creator](https://claude.com/plugins/skill-creator) | 创建、改进、评估和基准测试 Claude 技能。 | 想把公司流程、个人方法论或工具操作封装成可复用 skill。 | 按需：只有创建或维护 skill 时开启。 |
| [Playwright](https://claude.com/plugins/playwright) | Microsoft Playwright MCP，支持浏览器自动化、截图、填表、点击和端到端测试。 | Web 应用测试、截图验收、复现用户路径、自动化表单操作。 | 按需：需要真实浏览器交互时开启；权限较高。 |
| [Firecrawl](https://claude.com/plugins/firecrawl) | 把网页、站点或搜索结果转成适合 LLM 使用的 Markdown 或结构化数据。 | 抓取竞品文档、网页资料整理、多来源信息抽取。 | 按需：外部网页采集时开启；注意版权与隐私。 |
| [session-report](https://claude.com/plugins/session-report) | 从本地 Claude transcript 生成可浏览 HTML 报告，分析 token、缓存、subagent、skill 和高成本 prompt。 | 复盘一次 Claude Code 会话的消耗、效率和上下文结构。 | 按需：会话结束后复盘成本时开启。 |

影响关系：

1. CLAUDE.md Management、Remember、Productivity 都和“记忆”有关：CLAUDE.md Management 更适合项目规则，Remember 更适合会话历史，Productivity 更偏任务和日程上下文，避免同一事实重复写入三处。
2. Feature Dev 已包含探索、设计、评审流程；Superpowers 更强调 TDD、调试和子代理开发。新功能用 Feature Dev，卡在技术策略或测试节奏时再加 Superpowers。
3. Claude Code Setup 是诊断和推荐工具，不直接替代其他插件；建议先跑它，再决定是否安装 Playwright、Firecrawl、Hookify 等插件。
4. Playwright 和 Firecrawl 都会访问外部网页或浏览器环境，适合按需开启，避免在普通代码任务中扩大权限面。
5. Skill Creator 和 Superpowers 都能帮助技能编写；正式创建、评估 skill 时优先用 Skill Creator。
6. session-report 不改变 Claude 行为，适合最后做复盘，不需要常驻。

## 约束 Agent

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [Hookify](https://claude.com/plugins/hookify) | 用 Markdown 规则创建 hooks，阻止 Claude 出现不符合项目约定的行为。 | 强制代码风格、限制危险命令、禁止错误库或过时 API。 | 常驻：规则稳定后默认开启；和 CLAUDE.md Management 配合效果最好。 |
| [Ralph Loop](https://claude.com/plugins/ralph-loop) | 让 Claude 以自我参照循环反复处理同一任务，看到上轮结果后继续迭代直到完成。 | 需要多轮自动尝试、修复、再验证的开发任务。 | 按需：只给边界清晰的任务开启；可能放大成本和错误。 |

影响关系：

1. Hookify 是刹车，Ralph Loop 是油门；同时使用时必须写清楚停止条件、允许命令和验收标准。
2. Hookify 可把 CLAUDE.md 中的规则变成执行前后的约束，适合补强 CLAUDE.md Management。
3. Ralph Loop 不建议和 GitHub、Playwright、Firecrawl 等高权限插件长期同时开启，避免自动循环影响远程仓库或外部系统。

## 设计前端

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [Frontend Design](https://claude.com/plugins/frontend-design) | 生成有设计质量的生产级前端界面，避免通用 AI 风格。 | 从文字需求生成页面、组件、交互或视觉更完整的前端代码。 | 按需：写 UI 时开启；后端或脚本任务关闭。 |
| [Design](https://claude.com/plugins/design) | 加速设计 critique、UX 文案、可访问性审查、研究综合和开发交接。 | 评审视觉稿、整理设计系统、检查无障碍、把调研转成设计决策。 | 按需：设计评审或交接阶段开启；与 Frontend Design 配合使用。 |

影响关系：

1. Design 更像设计评审和交接专家，Frontend Design 更像前端界面生成专家；推荐先用 Design 明确标准，再用 Frontend Design 写代码。
2. Frontend Design 生成代码后，可以接 Playwright 做截图和端到端验证，也可以接 Playground 做可交互预览。
3. 两者都会影响 Claude 的审美和表达方式，不建议在纯后端、数据处理或安全扫描任务中常驻。

## 写代码

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [Playground](https://claude.com/plugins/playground) | 生成带控件、实时预览和复制输出的自包含 HTML playground。 | 快速做设计探索、数据探索、概念图或文档 critique 工具。 | 按需：需要可视化交互原型时开启。 |
| [TypeScript LSP](https://claude.com/plugins/typescript-lsp) | 为 TypeScript 和 JavaScript 提供语言服务器级代码智能。 | TS/JS 项目的类型、引用、诊断和重构辅助。 | 常驻：TS/JS 项目默认开启；非 TS/JS 项目不用开。 |
| [sonarqube](https://claude.com/plugins/sonarqube) | 在 agent coding loop 中执行 SonarQube 质量与安全规则、secret 扫描和质量门禁。 | 企业级质量门禁、合并前检查、多语言代码质量治理。 | 按需：合并前或高标准项目开启；常驻可能拖慢快速试验。 |
| [Code Simplifier](https://claude.com/plugins/code-simplifier) | 在保持功能不变的前提下，简化最近修改过的代码，提升清晰度和一致性。 | 功能写完后做收尾重构、降低复杂度、统一风格。 | 按需：测试通过后再开启；不要在需求未稳定时过早使用。 |
| [Serena](https://claude.com/plugins/serena) | 基于语言服务器协议提供语义代码理解、重构建议和代码库导航。 | 大型代码库理解、跨文件重构、定位复杂调用链。 | 常驻：大型或长期代码库推荐开启；小脚本按需即可。 |
| [Security Guidance](https://claude.com/plugins/security-guidance) | 编辑文件时提醒命令注入、XSS 和不安全代码模式。 | Web、API、鉴权、输入处理、脚本执行相关开发。 | 常驻：轻量安全护栏，适合大多数代码项目。 |
| [Semgrep](https://claude.com/plugins/semgrep) | 实时捕获安全漏洞，并引导 Claude 从一开始写更安全的代码。 | 安全敏感代码、Web/API、合并前安全检查。 | 常驻：安全敏感项目默认开启；与 SonarQube/Aikido 有重叠。 |
| [Aikido Security](https://claude.com/plugins/aikido) | 通过 Aikido MCP 做 SAST、secret 和 IaC 漏洞检测。 | 上线前安全扫描、密钥泄露检查、基础设施配置审查。 | 按需：发布前或安全审计时开启；与 Semgrep/SonarQube 部分重叠。 |
| [Sonatype Guide](https://claude.com/plugins/sonatype-guide) | 做软件供应链和依赖安全分析，给出漏洞检测与安全版本建议。 | 新增依赖、升级依赖、审查 npm/pip/Maven 等第三方包。 | 按需：改依赖或发布前开启；不替代源码扫描。 |

影响关系：

1. TypeScript LSP、Serena、Sourcegraph、Greptile 都能帮助理解代码：TypeScript LSP 专注 TS/JS 类型和引用，Serena 偏本地语义导航，Sourcegraph/Greptile 偏跨仓库或自然语言搜索。
2. Security Guidance 是轻量实时提醒；Semgrep 更偏规则化漏洞扫描；Aikido 覆盖 SAST、secret、IaC；SonarQube 同时管质量和安全。不要无脑全开，先按项目风险选择。
3. Sonatype Guide 只解决依赖和供应链问题，不能替代 Semgrep、Aikido 或 SonarQube 的源码安全检查。
4. Code Simplifier 应放在功能完成和测试通过之后；过早简化会增加返工。
5. SonarQube hooks 可能在每次编辑后运行，更适合高质量门禁项目，不适合快速原型阶段长期常驻。

## 管理代码

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [GitHub](https://claude.com/plugins/github) | 官方 GitHub MCP，可创建 issue、管理 PR、审查代码、搜索仓库并访问 GitHub API。 | 在 Claude Code 中处理 issue、PR、repo 搜索和仓库自动化。 | 常驻：GitHub 项目默认开启；注意授权范围。 |
| [Commit Commands](https://claude.com/plugins/commit-commands) | 提供 commit、push、创建 PR 等 Git 工作流命令。 | 写完代码后规范提交、推送、开 PR。 | 常驻：频繁提交代码时开启；与 GitHub 的 PR 能力重叠。 |
| [Greptile](https://claude.com/plugins/greptile) | 用自然语言查询仓库，查找代码、依赖关系和架构上下文。 | 问“这个功能在哪”“谁调用了这个模块”“这段逻辑依赖什么”。 | 按需：大型仓库搜索时开启；与 Sourcegraph/Serena 重叠。 |
| [PR Review Toolkit](https://claude.com/plugins/pr-review-toolkit) | 针对 PR 评论、测试、错误处理、类型设计、代码质量和简化的评审代理集合。 | 合并前做系统化 PR 检查。 | 按需：开 PR 或准备合并时开启；与 Code Review/CodeRabbit 重叠。 |

影响关系：

1. GitHub 已覆盖 issue、PR 和仓库 API；Commit Commands 更偏本地 Git 提交命令，两者可以共存，但创建 PR 的功能有重叠。
2. Greptile 和 Sourcegraph 都能做代码搜索；如果只是当前仓库问题，先用 Greptile 或 Serena，跨仓库再用 Sourcegraph。
3. PR Review Toolkit、Code Review、CodeRabbit、Optibot 都能参与评审。建议普通 PR 用 PR Review Toolkit 或 Code Review，高风险改动再加 CodeRabbit 或 Optibot。
4. Commit Commands 最好放在测试、静态检查和 PR 评审之后使用，不要让提交命令跑在质量检查前面。

## 修 BUG

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [Chrome DevTools](https://claude.com/plugins/chrome-devtools-mcp) | 控制和检查实时 Chrome：性能 trace、网络请求、console、source map 栈和浏览器动作。 | 调试页面性能、接口请求、控制台错误、真实浏览器状态。 | 按需：需要连接运行中的浏览器时开启。 |
| [Code Review](https://claude.com/plugins/code-review) | 使用专门代理和置信度过滤做 PR 代码审查。 | 代码合并前检查明显 bug、回归风险和可维护性问题。 | 按需：PR 阶段开启；与 PR Review Toolkit/CodeRabbit 重叠。 |
| [CodeRabbit](https://claude.com/plugins/coderabbit) | 结合 40+ 分析器、AST、代码图和项目规则做 AI 代码评审。 | 复杂、安全敏感或影响面大的代码改动，需要外部视角。 | 按需：高风险合并前开启；不要替代测试。 |
| [Optibot Code Review](https://claude.com/plugins/optibot) | 审查本地改动、分支差异或 patch，关注生产 bug、业务逻辑问题和安全漏洞。 | 未提交改动、分支对比、patch 文件审查、CI 中自动评审。 | 按需：发布前或本地差异审查时开启；与 CodeRabbit 部分重叠。 |
| [Sourcegraph](https://claude.com/plugins/sourcegraph) | 跨代码库搜索、追踪引用、分析重构影响、排查事故和做定向安全扫查。 | 跨仓库定位 bug、理解历史提交和引用链路。 | 按需：多仓库或大型代码库排障时开启。 |

影响关系：

1. Chrome DevTools 和 Playwright 都能操控浏览器：DevTools 适合现场调试和性能分析，Playwright 适合把复现路径固化成自动化测试。
2. Code Review、CodeRabbit、Optibot 都是评审类插件；不要把它们当成同一种工具。Code Review 偏 PR，CodeRabbit 偏深度静态分析，Optibot 偏本地差异和生产风险。
3. Sourcegraph、Greptile、Serena 都能找代码；Sourcegraph 更适合跨仓库和事故排查，Serena 更适合本地语义重构。
4. 推荐修 bug 流程：Chrome DevTools 复现问题，Serena/Sourcegraph 定位代码，修复后用 Code Review 或 Optibot 复核。

## 其他日常事务

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [LegalZoom](https://claude.com/plugins/legalzoom) | AI 审查法律文件风险，并在需要时建议咨询律师或连接 LegalZoom 专业网络。 | 合同、合规文档、条款审查、识别需要律师介入的风险。 | 按需：处理法律文件时开启；不能替代律师意见。 |

影响关系：

1. LegalZoom 只应处理法律文件相关任务，不适合常驻到代码开发上下文中。
2. 处理合同或合规文件时，避免同时开启不必要的代码仓库、浏览器或网页采集插件，减少敏感信息暴露面。
3. 如果文件内容涉及财务、运营或产品策略，可先用对应业务插件整理事实，再用 LegalZoom 做法律风险视角审查。

## 通用办公与业务插件

| 插件 | 核心功能 | 使用场景 | 推荐方式 |
| -- | -- | -- | -- |
| [Productivity](https://claude.com/plugins/productivity) | 管理任务、规划一天，并建立关于工作上下文的持久记忆。 | 个人工作流、日程任务同步、上下文整理。 | 常驻：日常工作中默认开启；与 Remember/CLAUDE.md Management 有记忆重叠。 |
| [Engineering](https://claude.com/plugins/engineering) | 支持站会、代码审查、架构决策、事故响应和技术文档。 | 技术负责人、研发团队协作、工程流程管理。 | 常驻：工程管理或团队协作场景开启；纯写代码任务可按需。 |
| [Data](https://claude.com/plugins/data) | 写 SQL、探索数据集、生成洞察、构建可视化和仪表盘。 | 数据分析、报表、指标解释、面向干系人的数据故事。 | 按需：数据任务开启；普通代码任务关闭。 |
| [Operations](https://claude.com/plugins/operations) | 优化供应商管理、流程文档、变更管理和合规跟踪。 | 运营流程梳理、SOP、容量规划、合规记录。 | 按需：业务运营或流程管理任务开启。 |
| [Finance](https://claude.com/plugins/finance) | 支持分录、对账、财务报表和差异分析等财务流程。 | 月结、审计准备、报表解释、预算与实际差异分析。 | 按需：财务资料处理时开启；注意数据权限。 |
| [Product Management](https://claude.com/plugins/product-management) | 写功能规格、规划路线图、综合用户研究并同步干系人。 | PRD、路线图、用户研究总结、竞品和干系人沟通。 | 常驻：产品经理或需求 owner 可默认开启；工程实现阶段按需。 |
| [Notion](https://claude.com/plugins/notion) | 集成 Notion 工作区，可搜索页面、创建或更新文档、管理数据库和访问团队知识库。 | 团队知识库、项目文档、需求文档、会议记录都在 Notion 的场景。 | 常驻：团队核心文档在 Notion 时开启；否则按需。 |

影响关系：

1. Productivity、Remember、CLAUDE.md Management 都会处理记忆：个人任务用 Productivity，会话历史用 Remember，项目规则用 CLAUDE.md Management。
2. Engineering 覆盖站会、代码审查、架构决策和事故响应，可能与 PR Review Toolkit、Code Review、session-report 的部分流程重叠。
3. Product Management 适合需求和路线图阶段，Feature Dev 适合工程落地阶段；先 PM 明确需求，再 Feature Dev 执行。
4. Data、Finance、Operations 都可能处理敏感业务数据，默认按需开启，并在任务结束后关闭。
5. Notion 是知识库入口，不等于记忆插件；它负责读写团队文档，Productivity/Remember 负责组织个人或会话上下文。

## 常见组合

| 场景 | 推荐组合 |
| -- | -- |
| 长期代码项目 | CLAUDE.md Management + Hookify + Security Guidance + 对应语言 LSP |
| 新功能开发 | Feature Dev + TypeScript LSP/Serena + PR Review Toolkit |
| 前端页面开发 | Frontend Design + Playwright + Chrome DevTools |
| 上线前检查 | Semgrep + Sonatype Guide + Code Review 或 Optibot |
| 大型仓库排障 | Serena + Sourcegraph 或 Greptile + Chrome DevTools |
| 需求到交付 | Product Management + Feature Dev + GitHub + PR Review Toolkit |

## 纠错与贡献

Claude 插件目录会更新，欢迎提交 issue 或 PR：

1. 插件链接失效或 slug 变化。
2. 官方描述变化。
3. 推荐方式需要调整。
4. 插件之间出现新的包含、冲突或替代关系。

## 数据来源

- [Claude Plugin Directory](https://claude.com/plugins)
- [Anthropic official Claude plugins marketplace manifest](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json)
- [Anthropic public Claude plugins](https://github.com/anthropics/claude-plugins-public)

本项目不是 Anthropic 官方仓库，只是基于公开官方页面整理的中文导航。