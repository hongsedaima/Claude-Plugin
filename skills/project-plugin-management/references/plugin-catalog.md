# Plugin Catalog Reference

Use this reference to choose Claude plugin marketplace plugins by project need. The catalog is intentionally selective: recommend only what the current project and task justify.

## Workflow and Memory

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `CLAUDE.md Management` | https://claude.com/plugins/claude-md-management | 常驻 for code projects | Project rules, team conventions, lessons learned | `检查并更新当前项目的 CLAUDE.md，把刚才约定的规则沉淀进去` | Overlaps with `Remember` and `Productivity`; use it for project rules. |
| `Superpowers` | https://claude.com/plugins/superpowers | 按需 | Complex feature planning, TDD, debugging | `用 Superpowers 帮我拆解这个需求，并按 TDD 的方式推进实现` | Overlaps with `Feature Dev`; use when TDD/debugging depth matters. |
| `Feature Dev` | https://claude.com/plugins/feature-dev | 按需 | New feature from exploration to implementation | `用 Feature Dev 带我从探索、设计到实现这个新功能` | Preferred for end-to-end feature workflow. |
| `Claude Code Setup` | https://claude.com/plugins/claude-code-setup | 按需 | Project onboarding or automation audit | `帮我 setup 一下当前这个项目，推荐适合的 Claude Code 自动化配置` | Diagnostic tool; not a daily plugin. |
| `Remember` | https://claude.com/plugins/remember | 常驻 for long projects | Long-running work across days/weeks | `把这次会话的关键决策整理进长期记忆，方便下次继续` | Conversation memory, not project-rule memory. |
| `Skill Creator` | https://claude.com/plugins/skill-creator | 按需 | Create or maintain skills | `帮我把这套工作流程做成一个可复用的 Claude skill` | Use for skill authoring/evals only. |
| `Playwright` | https://claude.com/plugins/playwright | 按需, cautious | Browser automation, screenshots, E2E | `用 Playwright 打开本地页面，截图并验证主要交互是否正常` | Overlaps with `Chrome DevTools`; disable after browser task. |
| `Firecrawl` | https://claude.com/plugins/firecrawl | 按需, cautious | Web scraping and site-to-markdown extraction | `用 Firecrawl 抓取这个网站并整理成适合 Claude 阅读的 Markdown` | External web access; check copyright/privacy. |
| `session-report` | https://claude.com/plugins/session-report | 按需 | Session cost and token usage review | `生成这次 Claude Code 会话的 session report，分析 token 和缓存使用` | Use after work, not during coding. |

## Agent Control

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `Hookify` | https://claude.com/plugins/hookify | 常驻 after rules stabilize | Enforce project constraints and prevent unwanted behavior | `根据这些项目规则创建 Hookify 约束，防止 Claude 以后违反` | Turns CLAUDE.md rules into guardrails. |
| `Ralph Loop` | https://claude.com/plugins/ralph-loop | 按需, cautious | Iterative self-repair with clear stop criteria | `用 Ralph Loop 反复修复这个问题，直到测试通过或遇到明确阻塞` | Do not combine with high-permission plugins without strict limits. |

## Design and Frontend

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `Frontend Design` | https://claude.com/plugins/frontend-design | 按需 | UI implementation, polished frontend code | `用 Frontend Design 设计并实现这个页面，避免通用 AI 风格` | Pair with `Playwright` for visual verification. |
| `Design` | https://claude.com/plugins/design | 按需 | Design critique, UX writing, accessibility, handoff | `用 Design 审查这个界面，重点看 UX 文案、可访问性和交接问题` | Use before `Frontend Design` when standards are unclear. |
| `Playground` | https://claude.com/plugins/playground | 按需 | Interactive HTML explorers/prototypes | `做一个可交互的 HTML playground，让我能调整参数并预览结果` | Prototype only; product code still needs engineering. |

## Coding and Quality

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `TypeScript LSP` | https://claude.com/plugins/typescript-lsp | 常驻 for TS/JS | Type/reference diagnostics and refactoring | `用 TypeScript LSP 检查这次修改的类型错误和引用问题` | TS/JS only. |
| `sonarqube` | https://claude.com/plugins/sonarqube | 按需 | Enterprise quality gates, secrets, security and code quality | `用 sonarqube 检查当前改动的代码质量、安全风险和质量门禁` | Heavy; overlaps with `Semgrep` and `Aikido Security`. |
| `Code Simplifier` | https://claude.com/plugins/code-simplifier | 按需 | Simplify recently changed code after tests pass | `在不改变功能的前提下，简化最近修改过的代码` | Use after functionality stabilizes. |
| `Serena` | https://claude.com/plugins/serena | 常驻 for large codebases | Semantic navigation and refactoring | `用 Serena 分析这个函数的调用链，并给出安全的重构方案` | Overlaps with `Sourcegraph`/`Greptile`; local semantic focus. |
| `Security Guidance` | https://claude.com/plugins/security-guidance | 常驻 for code projects | Lightweight security reminders while editing | `检查这段代码是否有命令注入、XSS 或不安全模式` | Low-cost security guardrail. |
| `Semgrep` | https://claude.com/plugins/semgrep | 常驻 for security-sensitive projects | Rule-based vulnerability scanning | `用 Semgrep 扫描当前改动里的安全漏洞，并给出修复建议` | Overlaps with `Aikido Security`/`sonarqube`. |
| `Aikido Security` | https://claude.com/plugins/aikido | 按需, cautious | SAST, secrets, IaC review before release | `用 Aikido Security 扫描 SAST、密钥泄露和 IaC 风险` | Broader security platform; check authorization. |
| `Sonatype Guide` | https://claude.com/plugins/sonatype-guide | 按需 | Dependency and supply-chain review | `用 Sonatype Guide 检查这些依赖是否有漏洞，并推荐安全版本` | Does not replace source scanning. |

## Code Management

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `GitHub` | https://claude.com/plugins/github | 常驻 if GitHub is primary | Issues, PRs, repo search, GitHub API | `用 GitHub 帮我查看这个仓库的 open PR，并总结需要处理的事项` | Cautious: remote repository access. |
| `Commit Commands` | https://claude.com/plugins/commit-commands | 常驻 for frequent commits | Commit, push, PR workflow | `检查 diff 后帮我生成合适的 commit，并准备 push 和 PR` | Run after tests/reviews. |
| `Greptile` | https://claude.com/plugins/greptile | 按需 | Natural-language repo search | `用 Greptile 找出用户登录逻辑在哪里实现，以及依赖哪些模块` | Overlaps with `Sourcegraph` and `Serena`. |
| `PR Review Toolkit` | https://claude.com/plugins/pr-review-toolkit | 按需 | PR checks for tests, errors, types, quality | `用 PR Review Toolkit 审查这个 PR，重点看测试、错误处理和类型设计` | Overlaps with `Code Review`/`CodeRabbit`. |

## Debugging and Review

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `Chrome DevTools` | https://claude.com/plugins/chrome-devtools-mcp | 按需, cautious | Live browser debugging, network, console, performance | `用 Chrome DevTools 连接当前页面，检查 console、network 和性能问题` | Use for debugging; `Playwright` for repeatable tests. |
| `Code Review` | https://claude.com/plugins/code-review | 按需 | PR review with specialized agents | `用 Code Review 审查这个 PR，列出高置信度问题和修复建议` | Lighter than `CodeRabbit`. |
| `CodeRabbit` | https://claude.com/plugins/coderabbit | 按需 | Deep code review with analyzers | `用 CodeRabbit 对当前改动做深度代码审查，重点看安全和边界情况` | Do not substitute for tests. |
| `Optibot Code Review` | https://claude.com/plugins/optibot | 按需 | Local diff, branch, patch, production-risk review | `用 Optibot review my changes，重点找生产 bug、业务逻辑问题和安全漏洞` | Marketplace plugin by third party; overlaps with `CodeRabbit`. |
| `Sourcegraph` | https://claude.com/plugins/sourcegraph | 按需 | Cross-repo search, incident investigation, references | `用 Sourcegraph 跨仓库搜索这个 API 的调用方和历史修改` | Better for cross-repo than local semantic edits. |

## Business and Daily Work

| Plugin | URL | Default | Trigger | Typical prompt | Overlap notes |
| -- | -- | -- | -- | -- | -- |
| `Productivity` | https://claude.com/plugins/productivity | 常驻 for daily work assistant use | Tasks, day planning, work context memory | `帮我整理今天的任务和上下文，给出接下来最该做的三件事` | Overlaps with `Remember`; personal workflow focus. |
| `Engineering` | https://claude.com/plugins/engineering | 常驻 for engineering management | Standups, code review, architecture, incidents, docs | `用 Engineering 帮我整理这次架构决策，输出 ADR 草稿` | Overlaps with engineering-specific review plugins. |
| `Data` | https://claude.com/plugins/data | 按需, cautious | SQL, dataset exploration, visualizations | `用 Data 帮我写 SQL 分析这个指标，并生成面向业务的结论` | Sensitive data boundary required. |
| `Operations` | https://claude.com/plugins/operations | 按需 | SOP, vendor, process, compliance tracking | `用 Operations 把这个流程整理成 SOP，并标出风险和负责人` | Business-process scope only. |
| `Finance` | https://claude.com/plugins/finance | 按需, cautious | Reconciliation, statements, variance analysis | `用 Finance 分析这份报表的预算与实际差异，并解释主要原因` | Financial data requires permission boundary. |
| `Product Management` | https://claude.com/plugins/product-management | 常驻 for PM/owner roles | Specs, roadmaps, user research, stakeholder updates | `用 Product Management 把这个想法整理成 PRD 和路线图建议` | Pair with `Feature Dev` for implementation. |
| `Notion` | https://claude.com/plugins/notion | 常驻 if team docs live in Notion | Search/update pages and databases | `用 Notion 搜索相关项目文档，并更新这份需求说明` | Cautious: workspace access. |

## Default Combination Patterns

- Long-running code project: `CLAUDE.md Management` + `Hookify` + `Security Guidance` + language LSP.
- New feature: `Feature Dev` + language intelligence (`TypeScript LSP` or `Serena`) + `PR Review Toolkit`.
- Frontend page: `Frontend Design` + `Playwright` + `Chrome DevTools`.
- Pre-release: `Semgrep` + `Sonatype Guide` + `Code Review` or `Optibot Code Review`.
- Large-codebase debugging: `Serena` + `Sourcegraph` or `Greptile` + `Chrome DevTools`.
- Requirement to delivery: `Product Management` + `Feature Dev` + `GitHub` + `PR Review Toolkit`.