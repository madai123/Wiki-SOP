# Daily Paper Report Pattern

用于每日论文发现报告。公开版模板只规定内容结构，不绑定具体个人关注方向、私有账号或外部文档平台。

- 本地版本：写入 `wiki/daily-report/Daily-Paper-Watch-YYYY-MM-DD.md`，必须包含 YAML frontmatter。
- 可选外部发布版本：正文内容必须与本地版本保持一致；外部版本不包含 YAML frontmatter。

日报属于 discover report，不等于论文入库。候选论文不要写成不存在的内部反链。

## 1 Local Markdown Version

```markdown
---
type: daily-paper-watch
date: YYYY-MM-DD
focus_source: docs/UserFocus.md
search_window: YYYY-MM-DD..YYYY-MM-DD
sources:
  - arxiv_query_search
  - optional_public_source
library_check:
  - wiki/papers frontmatter
status: draft
external_doc:
---

# Daily Paper Watch - YYYY-MM-DD

### 1 Focus Areas Covered

| Focus Area | Search Strategy | Result / Notes |
| --- | --- | --- |
|  |  |  |

### 2 Recommended Candidates

### 2.1 Focus Area Name

| Title | Source | Why It Matters | Suggested Action |
| --- | --- | --- | --- |
|  | [Source](https://example.com/paper) |  | download / discuss / watch |

### 3 Cross-Cutting Candidates

| Title | Source | Why It Matters | Suggested Action |
| --- | --- | --- | --- |
|  |  |  |  |

### 4 Existing Library Matches

| Candidate | Matched Existing Item | Match Type | Decision |
| --- | --- | --- | --- |
|  |  | source_id / title / alias | skipped |

### 5 Watch Signals

| Signal | Evidence | Suggested Follow-up |
| --- | --- | --- |
|  |  |  |

### 6 Recommended Next Actions

1. 建议下载 / 入库：
2. 建议先讨论：
3. 建议继续观察：
4. 建议更新 `docs/UserFocus.md`：
5. 需要人工判断：

### 7 Source Notes

- 
```

## 2 Frontmatter Fields

`type`

报告类型。Daily Paper Watch 固定使用 `daily-paper-watch`，方便以后按类型检索。

`date`

日报日期，格式为 `YYYY-MM-DD`。通常等于任务执行日期。

`focus_source`

本次检索所依据的关注源。默认是 `docs/UserFocus.md`。

`search_window`

实际检索时间窗口。建议写成 `YYYY-MM-DD..YYYY-MM-DD`。默认覆盖最近 48-72 小时，而不是只查当天。

`sources`

本次检查过的数据源。常用值：

- `arxiv_query_search`
- `huggingface_papers_optional`
- `openreview_optional`
- `semantic_scholar_optional`
- `publisher_page_optional`

使用可选来源时，必须在 `Source Notes` 中说明检查的范围或时间窗口。不要做无边界历史回溯。

`library_check`

本次用于去重或已有库检查的本地来源。通常包括：

- `wiki/papers frontmatter`

不要写 `INDEX-paper.md` 作为机器检查来源，因为 `INDEX-paper.md` 是 Dataview 视图定义，不是可直接读取的渲染表格。

`status`

日报自身状态。默认 `draft`。不要把它和 paper 的 `status` 混用。

`external_doc`

可选外部发布链接或标识。外部发布失败时留空，并在 `Source Notes` 说明失败原因。

## 3 Section Rules

## 1 Focus Areas Covered

记录每个 `docs/UserFocus.md` 关注 part 是否被覆盖。

- `Focus Area`：关注方向名称。
- `Search Strategy`：本次临时生成的 query 摘要，不必写完整长 query。
- `Result / Notes`：该方向今天的结论，例如 `有高相关候选`、`有少量候选`、`无直接候选`、`可选来源有补充`。不要输出 `Reviewed / Kept` 这类数量审计列。

## 2 Recommended Candidates

按关注方向分组列出候选。每个 focus area 使用一个 `###` 小节。

- `Title`：论文标题。
- `Source`：必须使用可点击链接，例如 `[arXiv](https://arxiv.org/abs/xxxx.xxxxx)`、`[OpenReview](https://openreview.net/forum?id=...)`、`[DOI](https://doi.org/...)`。不要只写裸 source id，也不要伪造链接。
- `Why It Matters`：为什么和当前关注方向有关，尽量说明命中的任务、方法、benchmark、dataset、system 或 gap。
- `Suggested Action`：只能使用 `download`、`discuss`、`watch` 之一。

## 3 Cross-Cutting Candidates

放同时命中多个关注方向的候选。

如果没有 cross-cutting candidate，写 `None`。

## 4 Existing Library Matches

记录已有库命中。默认只记录摘要或少量代表项，避免日报太长。不要为了数量审计展开完整清单。

匹配类型：

- `source_id`
- `title`
- `alias`
- `similar_title`

如果重复项很多，可以只写：

```text
duplicates skipped: N
details omitted
```

## 5 Watch Signals

记录趋势苗头，不等于推荐入库。

适合写：

- 某个 benchmark / dataset / system 名称反复出现。
- 某个 focus area 当天出现多个相关候选。
- 某个方向值得更新到 `docs/UserFocus.md`。

## 6 Recommended Next Actions

最多 5 条。只给行动建议，不直接执行下载、解析、summary 或入库。

## 7 Source Notes

记录抓取异常、重复合并、可选来源补充检索范围、页面缺字段、外部发布失败等情况。

## 4 Optional External Version

外部发布版本与本地版本使用同一份正文内容，章节、候选论文、排序、行动建议和 Source Notes 必须保持一致。

差异只允许有：

- 本地版本保留 YAML frontmatter。
- 外部版本不包含 YAML frontmatter。
- 外部版本可使用目标平台支持的样式增强展示，但不得改变正文内容。

外部版本优先使用稳定 Markdown：标题、表格、加粗、引用块、列表和链接。不要假设任何特定平台能解析 Obsidian callout 或 HTML-like callout 标签。
