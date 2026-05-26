# 1 目标

规范一批论文的批量处理顺序，避免在 summary、索引、Concept、Entity 和讨论型页面之间交叉写入造成混乱。

# 2 推荐顺序

1. 为每篇论文完成 PDFParse，得到 `raw/paper_id/paper_id.md`。
2. 为每篇论文生成 `wiki/papers/paper_id.md` summary。
3. 更新或确认 `INDEX-paper.md`。
4. 基于本 batch 讨论 Concept 候选。
5. 用户确认后，更新 `wiki/concepts/` 和相关 paper 的 `## 8 Concept links`。
6. 基于本 batch 讨论 Entity 候选。
7. 用户确认后，更新 `wiki/entities/` 和相关 paper 的 `## 9 Entity links`。
8. 只有用户明确需要时，再讨论 Gap / Comparison / Synthesis。
9. 所有写入完成后，更新 `wiki/log.md`。

# 3 确认边界

可以按流程直接写入：

- paper summary
- paper frontmatter
- Dataview index 所需的基础字段
- log

必须用户确认后写入：

- Concept 新增、合并、删除
- Entity 新增、合并、删除
- Gap 写入
- Comparison 写入
- Synthesis 写入
- 将 `check` 改为 `checked`
- 将未确认状态改为 `stable / end`，或将人工审核字段 `check` 改为 `checked`

# 4 读取范围

- 优先读取根目录 `INDEX-*.md` 和相关页面 frontmatter。
- 只打开与当前 batch 或当前问题直接相关的页面。
- 不默认全量读取 `wiki/papers/*.md`、`wiki/concepts/*.md` 或 `wiki/entities/*.md`。
- 如果 index 信息不足，先向用户确认范围。
