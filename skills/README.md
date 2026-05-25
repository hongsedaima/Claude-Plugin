# Skills

This repository currently provides one reusable Skill.

## `project-plugin-management`

Initialize project-level Claude plugin management rules.

Use it when starting, onboarding, or reorganizing a project so the agent can:

- inspect project context;
- ask for missing key information;
- recommend necessary Claude marketplace plugins;
- separate always-on, on-demand, not-needed, and cautious-authorization plugins;
- write plugin enable/disable rules into `CLAUDE.md`, `AGENTS.md`, or project memory after confirmation.

Skill path:

```text
skills/project-plugin-management
```

Suggested invocation:

```text
Use $project-plugin-management to initialize plugin management rules for this project.
```