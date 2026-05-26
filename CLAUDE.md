# 1 目标

统一说明本知识库各类任务的执行入口、读取范围、写入确认规则和日志规则。

具体操作流程看 `docs/operation/`，具体页面格式看 `docs/pattern/`，workspace 结构看 `docs/Workspace.md`。

# 2 通用执行原则

1. 执行任何任务前，先确认当前工作目录和任务类型。
2. 根据任务类型读取对应的 `docs/operation/*.md`。
3. 需要写页面时，再读取对应的 `docs/pattern/*.md`。
4. 写入前确认目标文件路径。
5. 涉及讨论型内容时，先和用户确认，再写入。
6. 每次写入、删除、merge、index 更新后，都要更新 `wiki/log.md`。
7. 不要默认全量读取目录。优先读取根目录 `INDEX-*.md`，再定位相关页面。
8. 不要创建不存在的内部反链。
9. 不要伪造 DOI、arXiv ID、OpenReview ID、Semantic Scholar ID 或其他 source id。

# 3 当前索引约定

当前 workspace 使用根目录 Dataview 索引：

- `INDEX-paper.md` -> `wiki/papers/`
- `INDEX-concept.md` -> `wiki/concepts/`
- `INDEX-entity.md` -> `wiki/entities/`
- `INDEX-gaps.md` -> `wiki/gaps/`
- `INDEX-comparisons.md` -> `wiki/comparisons/`
- `INDEX-synthesis.md` -> `wiki/synthesis/`

不要再新增 `wiki/papers/index.md`、`wiki/concepts/index.md`、`wiki/entities/index.md`、`wiki/gaps/index.md` 或 `wiki/synthesis/index.md` 作为主索引。

例外：`wiki/comparisons/index.md` 已存在，可作为 comparison 手写列表继续维护；根目录 `INDEX-comparisons.md` 可作为 Dataview 总览。

# 4 准备工作

执行新任务时确认：

```text
当前工作目录：[绝对路径]

已确认目录：
- downloads/
- raw/
- wiki/
- docs/

已确认索引：
- INDEX-paper.md
- INDEX-concept.md
- INDEX-entity.md
- INDEX-gaps.md
- INDEX-comparisons.md
- INDEX-synthesis.md

缺失项：
- [如果没有缺失，写：无]
```

# 5 任务入口

## 5.1 论文 Discover

读取：`docs/operation/Discover.md`

只负责发现候选论文，不直接生成 summary，不写入 wiki。是否下载、解析或入库，需要用户确认。

## 5.2 Daily Paper Watch

读取：

- `docs/UserFocus.md`
- `docs/operation/DailyPaperWorklist.md`
- `docs/pattern/DailyPaperReport.md`

每日根据 `docs/UserFocus.md` 的近期关注点临时生成 query，并检查公开论文来源。

可选来源包括 arXiv query search、Hugging Face Papers 日期页、OpenReview、Semantic Scholar、publisher page 等。不要使用过宽 RSS 作为 fallback。

默认只做论文发现和候选报告，不下载、不解析、不生成 summary、不写入 `wiki/papers/` 等知识正文页面。

执行时先用 `docs/UserFocus.md` 判断用户近期关注点；只有需要去重或定位时再读取根目录 `INDEX-*.md`，不要默认读取完整 wiki 页面。

最终报告默认生成本地版本，并可选生成外部发布版本：

- 本地版本：写入 `wiki/daily-report/Daily-Paper-Watch-YYYY-MM-DD.md`。
- 外部版本：如需发布到外部文档或消息系统，正文必须与本地版本保持一致。

## 5.3 PDF 到 Markdown 解析

读取：`docs/operation/PDFParse.md`

只负责从 `downloads/paper_id.pdf` 生成 `raw/paper_id/paper_id.md`、`raw/paper_id/paper_id.json` 和 `raw/paper_id/imgs/`。

## 5.4 论文 Summary 生成

读取：

- `docs/operation/Summary.md`
- `docs/pattern/Summary.md`

主要写入：

- `wiki/papers/paper_id.md`

## 5.5 Paper Index 更新

读取：

- `docs/operation/PaperIndex.md`
- `docs/pattern/PaperIndex.md`

主要维护：

- `INDEX-paper.md`
- `wiki/papers/paper_id.md` frontmatter

## 5.6 Concept 维护

读取：

- `docs/operation/Concept.md`
- `docs/pattern/Concept.md`

主要写入：

- `wiki/concepts/concept_name.md`
- 相关 paper 页面中的 `## 8 Concept links`

新增、合并、删除 Concept 前必须经过用户确认。

## 5.7 Entity 维护

读取：

- `docs/operation/Entity.md`
- `docs/pattern/Entity.md`

主要写入：

- `wiki/entities/entity_name.md`
- 相关 paper 页面中的 `## 9 Entity links`

Entity 只维护四类：`author_group / dataset / system / benchmark`。新增、合并、删除 Entity 前必须经过用户确认。

## 5.8 Gap 讨论与写入

读取：

- `docs/operation/Gap.md`
- `docs/pattern/Gap.md`

主要写入：

- `wiki/gaps/confirmed/gap_name.md`
- `wiki/gaps/hypotheses/gap_name.md`
- `wiki/gaps/questions/gap_name.md`

Gap 不自动生成。写入前必须经过用户确认。

## 5.9 Comparison 讨论与写入

读取：

- `docs/operation/Comparison.md`
- `docs/pattern/Comparison.md`

主要写入：

- `wiki/comparisons/comparison_name.md`
- `wiki/comparisons/index.md` 或页面 frontmatter

Comparison 只由用户问题触发，不自动生成。写入前必须经过用户确认。

## 5.10 Synthesis 讨论与写入

读取：

- `docs/operation/Synthesis.md`
- `docs/pattern/Synthesis.md`

主要写入：

- `wiki/synthesis/synthesis_name.md`

Synthesis 只由用户问题或明确讨论需求触发，不自动生成。写入前必须经过用户确认。

## 5.11 Batch 论文处理

读取：`docs/operation/Batch.md`

按 `PDFParse -> Summary -> PaperIndex -> Concept 讨论与确认 -> Entity 讨论与确认 -> Gap/Comparison/Synthesis 按需讨论` 的顺序执行。

# 6 写入确认规则

## 6.1 可以按流程直接写入

- paper summary
- paper frontmatter
- Dataview index 所需的基础字段
- log

## 6.2 必须用户确认后写入

- Concept 新增、合并、删除
- Entity 新增、合并、删除
- Gap 写入
- Comparison 写入
- Synthesis 写入
- 将 `check` 改为 `checked`
- 将未确认状态改为 `stable / end`，或将人工审核字段 `check` 改为 `checked`

# 7 读取范围规则

为避免上下文过大：

1. 优先读取根目录 `INDEX-*.md`。
2. 根据 index 定位相关页面。
3. 只读取与当前任务直接相关的页面。
4. 不默认读取全量目录。
5. 如果 index 信息不足，先向用户确认范围。

不要默认通篇扫描：

- `wiki/papers/*.md`
- `wiki/concepts/*.md`
- `wiki/entities/*.md`
- `wiki/gaps/**/*.md`
- `wiki/comparisons/*.md`
- `wiki/synthesis/*.md`

# 8 输出规则

- 按对应 pattern 输出。
- 不要把最终结果包裹在代码块中，除非用户明确要求。
- 不要输出多余解释。
- 不要创建不存在的内部反链。
- 不要伪造 DOI、arXiv、OpenReview 或 source id。
- 图片引用复用 raw markdown 中已验证存在的相对路径；如果图片已复制到目标页面同目录，才只写文件名。不要杜撰不存在的地址。

# 9 日志规则

每次完成写入、删除、merge 或 index 更新后，追加更新 `wiki/log.md`。

推荐格式：

```text
## YYYY-MM-DD Operation

- type: summary / paper-index / concept / entity / gap / comparison / synthesis / pdf-parse / discover
- affected files:
  - [file path]
- related papers:
  - [[paper_id]]
- changes:
  - [简要说明本次变化]
- notes:
  - [补充说明]
```
