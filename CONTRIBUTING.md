# Contributing

欢迎补充和纠错。这个仓库的目标不是收集越多越好，而是让新手快速理解 Claude 官方插件怎么选、什么时候开、插件之间有什么影响。

## 可接受的贡献

1. 修正失效或错误的 Claude 官方插件链接。
2. 根据官方页面更新插件描述。
3. 补充“常驻/按需”的推荐理由。
4. 补充插件之间的覆盖、冲突、互补关系。
5. 改进新手快速选择、常见组合或术语解释。

## 事实标准

请优先引用以下来源：

- Claude 插件页：https://claude.com/plugins
- Anthropic 官方插件 manifest：https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json
- Anthropic public plugins：https://github.com/anthropics/claude-plugins-public

如果信息来自插件作者的第三方仓库，请在 PR 中说明来源。

## 写作风格

- 用中文写给新手看，避免堆术语。
- 描述要准确，不夸大插件能力。
- 推荐方式必须写成“常驻：具体场景”或“按需：具体场景”。
- 影响关系要写清楚“替代、重叠、互补、冲突、权限风险”中的哪一种。

## PR 检查清单

- [ ] 插件名称链接到正确的 Claude 官方插件页。
- [ ] 描述没有偏离官方功能。
- [ ] 推荐方式明确写出常驻或按需。
- [ ] 对相关插件的影响关系已经补充或更新。
- [ ] 没有把第三方插件误写成 Anthropic 自研插件。