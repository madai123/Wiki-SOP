# 1 目标

发现与用户需求相关的论文候选，并在用户确认后再进入下载、解析或入库流程。

Discover 阶段只负责发现和筛选，不生成 summary，不写入 wiki 页面。

# 2 可用来源

- arXiv MCP：检索 arXiv 论文。
- OpenReview MCP：检索会议论文；下载时保留 OpenReview ID。
- Semantic Scholar：用于引用关系、相关论文和 metadata 辅助核验。
- 用户提供的论文标题、链接、DOI、arXiv ID 或 OpenReview ID。

# 3 操作步骤

1. 明确用户的研究问题、时间范围、 venue 或关键词。
2. 检索候选论文。
3. 去重并核对来源编号。
4. 根据用户目标筛选候选。
5. 向用户汇报候选列表和推荐理由。
6. 等待用户确认是否下载、解析或入库。

# 4 输出格式

| # | paper title | year / venue | source id | 简要理由 |
| --- | --- | --- | --- | --- |
| 1 |  |  | arXiv / DOI / OpenReview / Semantic Scholar |  |

同时说明是否建议加入当前 workspace。

# 5 质量要求

- 不要把外部论文直接写成内部反链。
- 只有论文入库并生成对应 `wiki/papers/paper_id.md` 后，才允许使用 `[[paper_id]]`。
- 不要伪造 DOI、arXiv ID、OpenReview ID 或 Semantic Scholar ID。
- 是否下载、解析或入库必须由用户确认。
