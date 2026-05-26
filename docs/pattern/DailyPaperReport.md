# Daily Paper Report Pattern

用于每日论文发现报告。该报告有两个版本：

- Obsidian 版本：写入 `wiki/daily-report/Daily-Paper-Watch-YYYY-MM-DD.md`，必须包含 YAML frontmatter。
- 飞书版本：写入飞书云文档，正文内容必须与 Obsidian 版本保持一致；飞书版不包含 YAML frontmatter。

日报属于 discover report，不等于论文入库。候选论文不要写成不存在的内部反链。

## 1 Obsidian Version

```markdown
---
type: daily-paper-watch
date: YYYY-MM-DD
focus_source: docs/UserFocus.md
search_window: YYYY-MM-DD..YYYY-MM-DD
sources:
  - huggingface_papers
  - arxiv_query_search
  - openreview_optional
library_check:
  - wiki/papers frontmatter
status: draft
feishu_doc:
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
|  | [arXiv](https://arxiv.org/abs/xxxx.xxxxx) / [HF](https://huggingface.co/papers/xxxx.xxxxx) / [OpenReview](https://openreview.net/forum?id=...) |  | download / discuss / watch |

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
5. 需要用户判断：

### 7 Source Notes

- 
```

## 2 Frontmatter Fields

`type`

报告类型。Daily Paper Watch 固定使用 `daily-paper-watch`，方便以后用 Dataview 按类型检索。

`date`

日报日期，格式为 `YYYY-MM-DD`。通常等于任务执行日期。

`focus_source`

本次检索所依据的关注源。默认是 `docs/UserFocus.md`。

`search_window`

实际检索时间窗口。建议写成 `YYYY-MM-DD..YYYY-MM-DD`。默认覆盖最近 48-72 小时，而不是只查当天。

`sources`

本次检查过的数据源。常用值：

- `huggingface_papers`
- `arxiv_query_search`
- `semantic_scholar_optional`
- `openreview_optional`

使用 `openreview_optional` 时，必须在 `Source Notes` 中说明检查的 venue/year 或 recent window。OpenReview 只用于最近来源补充，不用于无边界历史回溯。

`library_check`

本次用于去重或已有库检查的本地来源。通常包括：

- `wiki/papers frontmatter`

不要写 `INDEX-paper.md` 作为机器检查来源，因为 `INDEX-paper.md` 是 Dataview 视图定义，不是 Claude Code 可直接读取的渲染表格。

`status`

日报自身状态。默认 `draft`。不要把它和 paper 的 `status` 混用。

`feishu_doc`

飞书文档链接或文档标识。飞书写入失败时留空，并在 `Source Notes` 说明失败原因。

## 3 Section Rules

## 1 Focus Areas Covered

记录每个 `docs/UserFocus.md` 关注 part 是否被覆盖。

- `Focus Area`：关注方向名称。
- `Search Strategy`：本次临时生成的 query 摘要，不必写完整长 query。
- `Result / Notes`：该方向今天的结论，例如 `高产`、`有少量候选`、`无直接候选`、`OpenReview 有补充`。不要输出 `Reviewed / Kept` 这类数量审计列。

## 2 Recommended Candidates

按关注方向分组列出候选。每个 focus area 使用一个 `###` 小节。

- `Title`：论文标题。
- `Source`：必须使用可点击链接，例如 `[arXiv](https://arxiv.org/abs/xxxx.xxxxx)`、`[HF](https://huggingface.co/papers/xxxx.xxxxx)`、`[OpenReview](https://openreview.net/forum?id=...)`。不要只写裸 arXiv ID，也不要伪造链接。
- `Why It Matters`：为什么和当前关注方向有关，尽量说明命中的任务、方法、benchmark、dataset、system 或 gap。
- `Suggested Action`：只能使用 `download`、`discuss`、`watch` 之一。
- OpenReview 候选如果有可核验链接或 ID，直接写入对应 focus area 的 `Recommended Candidates` 表格；不要为 OpenReview 单独开候选区。

## 3 Cross-Cutting Candidates

放同时命中多个关注方向的候选，例如同时涉及 benchmark、GUI agent 和 long-horizon evaluation 的论文。

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

记录抓取异常、重复合并、OpenReview 补充检索的 venue/year 或 recent window、Hugging Face 页面缺字段、飞书写入失败等情况。

## 4 Feishu Version

飞书版本与 Obsidian 版本使用同一份正文内容，章节、候选论文、排序、行动建议和 Source Notes 必须保持一致。

差异只允许有：

- Obsidian 版本保留 YAML frontmatter。
- 飞书版本不包含 YAML frontmatter。
- 飞书版本可使用飞书支持的样式增强展示，但不得改变正文内容。

飞书版本优先使用稳定 Markdown：标题、表格、加粗、引用块、列表和链接。不要假设 `docx_builtin_import` 能解析 Obsidian callout 或 HTML-like callout 标签。

推荐写法：

```markdown
# Daily Paper Watch - YYYY-MM-DD

> [!important] 今日最重要
> - **最建议下载 / 入库**：
> - **最值得讨论**：
> - **需要用户判断**：

## 1 Focus Areas Covered

...

## 2 Recommended Candidates

...
```

如果飞书 Markdown 不支持某些高亮语法，使用加粗、引用块或醒目的小标题替代。
