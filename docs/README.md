# Docs 使用说明

本目录只保存 SOP 和模板，不保存知识库正文。

## 1 文档分工

- `CLAUDE.md`：全局入口、任务路由、确认边界和执行原则。
- `docs/README.md`：本目录地图。
- `docs/Workspace.md`：workspace 文件结构说明。
- `docs/UserFocus.md`：用户近期关注摘要，供 Daily Paper Watch 等轻量任务快速读取。
- `docs/operation/`：操作流程，回答“怎么做”。
- `docs/pattern/`：页面模板，回答“写成什么样”。
- `docs/SOP-Lint-Report.md`：历史审查报告，用于追踪曾经出现过的冲突，不作为执行规范。

## 2 当前索引约定

当前 workspace 采用根目录 Dataview 索引：

- `INDEX-paper.md` -> `wiki/papers/`
- `INDEX-concept.md` -> `wiki/concepts/`
- `INDEX-entity.md` -> `wiki/entities/`
- `INDEX-gaps.md` -> `wiki/gaps/`
- `INDEX-comparisons.md` -> `wiki/comparisons/`
- `INDEX-synthesis.md` -> `wiki/synthesis/`

不要再新增 `wiki/papers/index.md`、`wiki/concepts/index.md`、`wiki/entities/index.md`、`wiki/gaps/index.md` 或 `wiki/synthesis/index.md` 作为主索引。

例外：`wiki/comparisons/index.md` 已存在，可作为 comparison 手写列表继续使用；根目录 `INDEX-comparisons.md` 可作为 Dataview 总览。

## 3 Operation 文档

- `Discover.md`：论文发现与候选筛选。
- `DailyPaperWorklist.md`：每日论文发现 worklist，用于基于 `docs/UserFocus.md` 的临时 arXiv query 检索、Hugging Face Papers 检查和 OpenReview 补充检索。
- `UserFocus.md`：用户近期关注摘要的维护规则。
- `PDFParse.md`：PDF 到 raw markdown 解析。
- `Summary.md`：单篇论文 summary 生成。
- `PaperIndex.md`：论文索引维护。
- `Concept.md`：Concept 页面维护。
- `Entity.md`：Entity 页面维护。
- `Gap.md`：Gap / hypothesis / question 讨论与写入。
- `Comparison.md`：横向比较讨论与写入。
- `Synthesis.md`：综合理解讨论与写入。
- `Batch.md`：批量论文处理顺序。

## 4 执行顺序

执行任务时先读 `CLAUDE.md`，再按任务类型读取对应 `docs/operation/*.md`，最后读取对应 `docs/pattern/*.md`。

讨论型内容写入前必须经用户确认：Concept 新增/合并/删除、Entity 新增/合并/删除、Gap、Comparison、Synthesis、`check=checked`、`status=end/stable` 等状态收口。

## 5 Pattern 文档

- `DailyPaperReport.md`：每日论文发现报告格式，用于生成飞书版本和 `wiki/daily-report/` Obsidian 版本。
- `Summary.md`：单篇论文 summary 页面模板。
- `PaperIndex.md`：论文索引字段模板。
- `Concept.md`：Concept 页面模板。
- `Entity.md`：Entity 页面模板。
- `Gap.md`：Gap 页面模板。
- `Comparison.md`：Comparison 页面模板。
- `Synthesis.md`：Synthesis 页面模板。
