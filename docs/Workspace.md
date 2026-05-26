# Docs 使用说明与 Workspace 结构

本目录保存 SOP 和模板，不保存知识库正文。面向公开仓库时，`docs/` 可以作为可复用方法论发布；具体论文、阅读日志、个人偏好和原始材料应按需脱敏。

## 1 文档分工

- `CLAUDE.md`：全局入口、任务路由、确认边界和执行原则。
- `docs/Workspace.md`：本目录地图和 workspace 结构说明。
- `docs/UserFocus.md`：近期关注摘要模板，供 Daily Paper Watch 等轻量任务快速读取；公开前应替换为示例内容。
- `docs/operation/`：操作流程，回答“怎么做”。
- `docs/pattern/`：页面模板，回答“写成什么样”。
- `docs/SOP-Lint-Report.md`：历史审查报告，用于追踪曾经出现过的冲突，不作为执行规范。

## 2 总体结构

```text
claude_workspace/
├── README.md
├── CLAUDE.md
├── INDEX-paper.md
├── INDEX-concept.md
├── INDEX-entity.md
├── INDEX-gaps.md
├── INDEX-comparisons.md
├── INDEX-synthesis.md
├── downloads/
├── raw/
├── wiki/
│   ├── log.md
│   ├── daily-report/
│   ├── papers/
│   ├── concepts/
│   ├── entities/
│   ├── gaps/
│   │   ├── confirmed/
│   │   ├── hypotheses/
│   │   └── questions/
│   ├── comparisons/
│   │   └── index.md
│   └── synthesis/
└── docs/
    ├── Workspace.md
    ├── UserFocus.md
    ├── SOP-Lint-Report.md
    ├── operation/
    └── pattern/
```

## 3 当前索引约定

当前 workspace 采用根目录 Dataview 索引：

- `INDEX-paper.md` -> `wiki/papers/`
- `INDEX-concept.md` -> `wiki/concepts/`
- `INDEX-entity.md` -> `wiki/entities/`
- `INDEX-gaps.md` -> `wiki/gaps/`
- `INDEX-comparisons.md` -> `wiki/comparisons/`
- `INDEX-synthesis.md` -> `wiki/synthesis/`

不要再新增 `wiki/papers/index.md`、`wiki/concepts/index.md`、`wiki/entities/index.md`、`wiki/gaps/index.md` 或 `wiki/synthesis/index.md` 作为主索引。

例外：`wiki/comparisons/index.md` 已存在，可作为 comparison 手写列表继续使用；根目录 `INDEX-comparisons.md` 可作为 Dataview 总览。

## 4 根目录与输入材料

### `CLAUDE.md`

全局执行规范。模型执行任务前应优先读取，用于确认任务入口、读取范围、写入确认规则和日志规则。

### `INDEX-*.md`

根目录索引文件，主要通过 Dataview 汇总 `wiki/` 下页面 frontmatter。

### `downloads/`

保存原始 PDF 和 metadata：

- `paper_id.pdf`
- `paper_id.json`

### `raw/`

保存 OCR / parser 输出：

- `raw/paper_id/paper_id.md`
- `raw/paper_id/paper_id.json`
- `raw/paper_id/imgs/`

公开仓库通常不建议包含完整 `downloads/` 和 `raw/` 内容。

## 5 Wiki 知识库

### `wiki/log.md`

操作日志。每次写入、删除、合并、索引更新或结构调整后追加记录。公开前建议检查是否包含私有路径、个人判断或未发布工作。

### `wiki/daily-report/`

保存 Daily Paper Watch 生成的本地日报。日报是 discover report，不等于论文入库。默认文件名：

- `Daily-Paper-Watch-YYYY-MM-DD.md`

### `wiki/papers/`

保存单篇论文 summary，文件名使用 `paper_id.md`。

### `wiki/concepts/`

保存跨论文复用的方法、机制、理论、训练目标、表示方式或研究路线。Concept 总览来自各页面 frontmatter 和 `INDEX-concept.md`。

### `wiki/entities/`

保存具体对象，仅维护四类：

- `author_group`
- `dataset`
- `system`
- `benchmark`

Entity 总览来自各页面 frontmatter 和 `INDEX-entity.md`。

### `wiki/gaps/`

保存研究空白、假设和开放问题。

- `wiki/gaps/confirmed/`：confirmed gap
- `wiki/gaps/hypotheses/`：hypothesis
- `wiki/gaps/questions/`：question

### `wiki/comparisons/`

保存确认后的横向比较页面。`wiki/comparisons/index.md` 可作为手写列表保留；`INDEX-comparisons.md` 可作为 Dataview 总览。

### `wiki/synthesis/`

保存确认后的综合理解页面，例如领域地图、方法谱系、共享假设和趋势判断。

## 6 Operation 文档

- `Discover.md`：论文发现与候选筛选。
- `DailyPaperWorklist.md`：每日论文发现 worklist，用于基于 `docs/UserFocus.md` 的临时检索、来源检查和候选报告。
- `UserFocus.md`：近期关注摘要的维护规则。
- `PDFParse.md`：PDF 到 raw markdown 解析。
- `Summary.md`：单篇论文 summary 生成。
- `PaperIndex.md`：论文索引维护。
- `Concept.md`：Concept 页面维护。
- `Entity.md`：Entity 页面维护。
- `Gap.md`：Gap / hypothesis / question 讨论与写入。
- `Comparison.md`：横向比较讨论与写入。
- `Synthesis.md`：综合理解讨论与写入。
- `Batch.md`：批量论文处理顺序。

## 7 Pattern 文档

- `DailyPaperReport.md`：每日论文发现报告格式，用于生成本地日报和可选外部发布版本。
- `Summary.md`：单篇论文 summary 页面模板。
- `PaperIndex.md`：论文索引字段模板。
- `Concept.md`：Concept 页面模板。
- `Entity.md`：Entity 页面模板。
- `Gap.md`：Gap 页面模板。
- `Comparison.md`：Comparison 页面模板。
- `Synthesis.md`：Synthesis 页面模板。

## 8 执行顺序

执行任务时先读 `CLAUDE.md`，再按任务类型读取对应 `docs/operation/*.md`，最后读取对应 `docs/pattern/*.md`。

讨论型内容写入前必须经用户确认：Concept 新增/合并/删除、Entity 新增/合并/删除、Gap、Comparison、Synthesis、`check=checked`、`status=end/stable` 等状态收口。
