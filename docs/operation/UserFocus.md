# User Focus Maintenance

用于维护 `docs/UserFocus.md`，让自动任务快速了解用户近期关注点。

> [!note] 目标
> `docs/UserFocus.md` 是轻量上下文，不是正式知识库页面。
>
> 它服务于 Daily Paper Watch、Discover 等自动任务，帮助模型判断什么论文更值得推荐。

## 1 什么时候更新

在以下情况可以更新：

- 用户明确说“最近关注 / 最近重点 / 后续多看 / 先关注”某个方向。
- Daily Paper Watch 多次围绕同一主题运行。
- 用户确认某些方向值得持续 watch。
- 用户明确说某类论文不再重要或降低优先级。

## 2 更新规则

> [!warning] 保持短
> 只写近期偏好和筛选口径，不写长篇分析。
>
> 如果内容需要展开成完整论述，应写入 `wiki/synthesis/`，而不是扩展 `docs/UserFocus.md`。

建议结构：

- `当前关注`
- `优先推荐`
- `降低优先级`
- `Recent Threads`
- `Update Notes`

## 3 写入原则

- 可以根据用户明确表达直接更新。
- 不要根据模型单方面猜测大幅改写。
- 不要删除已有关注点，除非用户明确表示不再关注。
- 每次更新后记录 `wiki/log.md`。

## 4 Daily Paper Watch 使用方式

Daily Paper Watch 应优先读取：

1. `docs/UserFocus.md`
2. `docs/operation/DailyPaperWorklist.md`
3. `docs/pattern/DailyPaperReport.md`
4. 必要时再读取 `INDEX-*.md`

如果 `docs/UserFocus.md` 已足够判断相关性，不要读取完整 wiki 页面。
