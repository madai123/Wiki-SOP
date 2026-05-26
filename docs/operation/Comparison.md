# 1 目标

在用户提出比较问题时，对论文、方法、系统、benchmark、dataset 或 concept 进行横向比较，并在用户确认后写入 `wiki/comparisons/`。

Comparison 不在每篇论文处理时自动生成，只保存用户与模型讨论后确认有价值的比较结论。

# 2 输入与索引

- 模板：`docs/pattern/Comparison.md`
- 总览：`wiki/comparisons/index.md`，如需要也可由根目录 `INDEX-comparisons.md` 通过 Dataview 汇总
- 相关索引：
  - `INDEX-paper.md`
  - `INDEX-concept.md`
  - `INDEX-entity.md`
  - `INDEX-gaps.md`

# 3 操作步骤

## 3.1 讨论

1. 明确用户的比较问题。
2. 先读相关 index，定位与问题相关的 paper / concept / entity / gap。
3. 只读取与比较问题直接相关的页面。
4. 如果 index 信息不足以判断范围，先向用户确认比较对象，不要全量读取目录。
5. 生成比较草案。
6. 向用户汇报核心结论，询问是否写入。
7. 用户确认前，不写入文件。

## 3.2 写入

1. 根据比较主题创建或更新：`wiki/comparisons/comparison_name.md`
2. 如果已有相似 comparison，优先更新原页面，不重复创建。
3. 更新 `wiki/comparisons/index.md` 或确认根目录 `INDEX-comparisons.md` 可通过 frontmatter 自动汇总。
4. 如相关 paper / concept / entity / gap 页面有“相关比较”区域，可同步补充反链；没有对应区域时，不强行改模板。
5. 更新完成后，在 `wiki/log.md` 记录本次调整。

# 4 质量要求

- comparison 必须由用户问题触发，不自动创建。
- 写入前必须经过用户确认。
- 只记录讨论后值得保留的核心结论。
- 所有库内页面必须使用反链。
- 不要创建不存在的 paper / concept / entity / gap 反链。
- 如果比较涉及实验数值，必须来自已有 paper summary、原文表格或用户提供的数据。
- 写入阶段直接输出更新后的 Markdown 内容，不要用代码块包裹。
