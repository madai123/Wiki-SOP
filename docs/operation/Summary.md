# 1 目标

规范单篇论文 summary 生成流程，确保输出内容忠于原文，并写入 `wiki/papers/paper_id.md`。

# 2 输入与读取

1. 读取模板：`docs/pattern/Summary.md`
2. 读取 metadata：`downloads/paper_id.json`
3. 读取 raw markdown：`raw/paper_id/paper_id.md`
4. 如需核对图表，读取 `raw/paper_id/imgs/` 中对应图片

# 3 操作步骤

1. 确认 `paper_id`、metadata 和 raw markdown 均存在。
2. 按 `docs/pattern/Summary.md` 创建或更新 `wiki/papers/paper_id.md`。
3. 根据论文正文完成 `## 1` 到 `## 7`。
4. 默认保留 `## 8 Concept links`、`## 9 Entity links`、`## 10 与已有工作的关系` 为空；这些部分只在用户主动触发并确认后写入。
5. 更新根目录 `INDEX-paper.md` 对应信息，或确认 Dataview 可从 frontmatter 自动展示。
6. 在 `wiki/log.md` 追加本次 summary 操作记录。

# 4 质量要求

## 4.1 Frontmatter

- `source_id`、`title`、`authors`、`year` 必须来自 metadata 或论文正文，不要补造。
- `status` 初次 summary 完成后写 `summary finished`。
- `manual_review_needed` 可用于标记需要人工复查的论文。
- `tags` 命名不要包含空格，优先复用已有标签。

## 4.2 深度总结

- 除短引文外，正文必须经过理解后重构，不要照抄摘要或大段原文。
- 引文必须来自论文原文，不得修改或杜撰。
- 关键公式保留为标准 LaTeX，并解释公式中关键项的作用。
- Figure/Table 只收录对理解方法、实验或结论有帮助的内容。
- 图片引用复用 raw markdown 中已验证存在的相对路径，例如 `![](raw/xxx/imgs/figure_1.png)`；如果图片已复制到目标页面同目录，才只写文件名。不要杜撰不存在的地址。

## 4.3 关联讨论

`## 10 与已有工作的关系` 只在用户主动要求时处理。

可用来源：

- 当前 workspace 内已有 paper summary
- arXiv / OpenReview / Semantic Scholar 返回的外部论文信息
- 用户明确提供的论文、链接或讨论结论

写入前必须得到用户确认。库内论文使用 `[[paper_id]]`，库外论文使用标题加 DOI/arXiv/OpenReview 等真实来源编号，不创建伪反链。

# 5 输出要求

- 写入文件时直接写 Markdown 正文，不要包裹三反引号。
- 不要伪造 DOI、arXiv ID、OpenReview ID 或 Semantic Scholar ID。
- 如果 raw markdown 信息不足，应标注“需要复查”，不要强行补全。
