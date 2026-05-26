# 1 目标

维护根目录 `INDEX-paper.md`，用于通过 Dataview 展示 `wiki/papers/` 下论文页面的基本信息和处理状态。

Paper Index 不承担详细 summary 功能；详细内容只写在 `wiki/papers/paper_id.md`。

# 2 操作步骤

## 2.1 读取与检查

1. 读取格式参考：`docs/pattern/PaperIndex.md`
2. 读取当前索引：`INDEX-paper.md`
3. 读取目标论文页面：`wiki/papers/paper_id.md`
4. 如论文页面尚未生成，读取 metadata：`downloads/paper_id.json`
5. 确认 `paper_id` 是否已经有对应页面或索引记录，避免重复创建

## 2.2 新增或更新

1. 如果使用 Dataview 索引，优先通过维护 paper 页面的 frontmatter 来更新索引展示。
2. 如果 `INDEX-paper.md` 中包含手写表格，只更新当前论文对应行，不重写无关条目。
3. 如果 summary frontmatter 与 metadata 冲突，优先使用 summary frontmatter，并在 `Notes` 或日志中记录冲突。
4. 更新完成后，在 `wiki/log.md` 记录本次调整。

# 3 字段规则

- `Paper_id`：使用 `[[paper_id]]`
- `Title`：来自 metadata 或论文正文
- `Year`：来自 metadata 或论文正文
- `Source ID`：来自 arXiv / DOI / OpenReview / Semantic Scholar / 用户明确提供的信息
- `status`：`metadata finished / summary finished / have discussed`
- `check`：`uncheck / checked`，默认 `uncheck`
- `Notes`：简要记录缺失、冲突或人工判断

# 4 质量要求

- 不要重复创建同一个 `paper_id`。
- 不要凭空补全 metadata。
- 不要伪造 DOI、arXiv ID、OpenReview ID 或 Semantic Scholar ID。
- 只有用户明确确认后，才允许将 `check` 改为 `checked`。
- 如果用户只是下载或导入论文但未生成 summary，应标为 `metadata finished`。
- 不要用代码块包裹最终写入内容，除非用户明确要求。
