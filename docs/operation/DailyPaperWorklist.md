# Daily Paper Worklist

用于每日论文发现任务。该文档只描述公开版 worklist，不绑定具体个人关注方向、私有账号、外部文档平台或自动化实现。

> [!note] 任务目标
> 每日根据 `docs/UserFocus.md` 中的关注摘要，临时生成检索策略，检查公开论文来源中与当前研究方向相关的新论文，形成候选列表。
>
> 本任务只做 Discover，不下载、不解析、不生成 summary、不写入 `wiki/papers/` 等知识正文页面。
>
> 默认产物：
>
> - 本地 Markdown 日报：`wiki/daily-report/Daily-Paper-Watch-YYYY-MM-DD.md`。
> - 可选外部发布版本：由使用者自行接入文档平台或消息系统，正文内容应与本地版本一致。

> [!tip] 每日输入
> - 当前日期：`YYYY-MM-DD`
> - 关注摘要：`docs/UserFocus.md`
> - 公开论文来源：
>   - arXiv query search
>   - Hugging Face Papers 日期页，可选
>   - OpenReview 或会议站点检索，可选
>   - Semantic Scholar / Crossref / publisher page，可选

> [!note] 检索策略
> 不维护固定关键词订阅表。执行时先读取 `docs/UserFocus.md`，再根据当前关注点临时生成 query。
>
> 生成 query 时应覆盖每个当前关注 part，并允许同义词扩展。每个 part 默认生成 1-3 个 query；每个 query 必须包含至少一个具体技术词、任务词或实体词，避免只使用过宽词。

> [!warning] 明确不做
> - 不要自动下载论文。
> - 不要自动调用 PDFParse。
> - 不要自动生成 `wiki/papers/paper_id.md`。
> - 不要自动写入 Concept / Entity / Gap / Comparison / Synthesis。
> - 不要为未入库论文创建 `[[paper_id]]` 内部反链。
> - 不要伪造 DOI、arXiv ID、OpenReview ID、Semantic Scholar ID、publisher URL 或其他 source id。
> - 不要把当日临时 query 写回 workspace，除非用户明确要求固化。

## 1 执行步骤

> [!note] Step 1 - 读取已有上下文
> 先读取：
>
> - `CLAUDE.md`
> - `docs/UserFocus.md`
> - `docs/operation/Discover.md`
> - `docs/pattern/DailyPaperReport.md`
>
> 目标是先用 `docs/UserFocus.md` 快速理解当前关注点，再决定当日检索策略。
>
> 只有需要去重或定位已有主题时，再读取可机器解析的 Markdown frontmatter：
>
> - 列出 `wiki/papers/*.md`，只抽取 frontmatter 中的 `title`、`source_id`、`aliases`、`status`。
> - 如需定位已有主题，再列出 `wiki/concepts/*.md`、`wiki/entities/*.md`、`wiki/gaps/**/*.md`、`wiki/synthesis/*.md`，只抽取 frontmatter 中的 `name`、`title`、`aliases`、`status`。
> - `INDEX-*.md` 是 Obsidian / Dataview 的人类视图，不要假设模型能读取 Dataview 渲染后的表格。
>
> 如果 `docs/UserFocus.md` 已足够判断相关性，不要读取完整 wiki 页面。

> [!note] Step 2 - 生成当日检索策略
> 将 `docs/UserFocus.md` 中的每个关注 part 转换为临时检索 query。
>
> 要求：
>
> - 每个关注 part 默认生成 1-3 个 query。
> - 每个 query 应包含 category、任务词、技术词或实体词。
> - 默认使用最近 48-72 小时窗口，避免更新时间、时区和索引延迟造成遗漏。
> - 每个关注 part 默认最多保留 3-5 篇候选。
> - 当某个 part 当天无候选时，在报告中记录为 no candidates，不要强行扩宽到大类检索。
> - 不要输出 `Reviewed / Kept` 等数量审计列；日报重点是“有什么值得看”和“为什么值得看”。

> [!note] Step 3 - 检索公开来源
> 根据 Step 2 生成的 query 检索公开论文来源。
>
> 对每条候选提取：
>
> - title
> - source link
> - source id，如 arXiv ID / DOI / OpenReview ID / Semantic Scholar ID
> - authors
> - abstract 或 summary
> - published / updated date
> - matched focus area
>
> 默认不按过宽大类 RSS 全量拉取，也不要把 RSS 作为 fallback。需要补充来源时，优先使用有明确时间窗口和可核验链接的来源。

> [!tip] Step 4 - 去重与已有库检查
> 同一论文可能同时出现在多个来源。
>
> 候选之间的去重优先级：
>
> 1. source id 完全相同。
> 2. title 规范化后相同。
> 3. title 高度相似且作者重叠。
>
> 已有库检查：
>
> - 允许通过文件列表读取 `wiki/papers/*.md` 的 frontmatter，用于检查 `title`、`source_id`、`aliases`、`status`。
> - 不要依赖 `INDEX-paper.md` 的 Dataview 渲染结果；如果需要等价数据，直接从 paper 页面 frontmatter 抽取。
> - 命中已有 `source_id` / `title` / `aliases` 的候选，默认不进入推荐列表。
> - 已有库命中只记录 skipped count；除非用户要求细节，否则不要在日报中展开全部重复项。
> - 不修改任何已有 wiki 文件，不改变 paper status。

> [!note] Step 5 - 相关性判断
> 对每篇候选给出 `suggested_action`，而不是维护长期优先级状态：
>
> - `download`：直接相关，建议考虑下载或入库。
> - `discuss`：方向相关，但需要判断是否值得跟进。
> - `watch`：边缘相关或趋势信号，暂不建议入库。
> - `skip`：重复、弱相关或缺少可核验来源。
>
> 判断依据：
>
> - 是否命中 `docs/UserFocus.md` 当前关注 part。
> - 是否涉及当前库中的 Concept / Entity / Gap / Synthesis。
> - 是否提供新 benchmark / dataset / system / evaluation dimension。
> - 是否可能补充已有 synthesis 或 gap。
> - 是否只是通用背景论文，且与当前库关系较弱。
>
> 输出候选表时不要包含 `Category` 列。`Source` 必须写成可点击链接，不要只写裸 source id。

> [!note] Step 6 - 生成本地日报
> 按 `docs/pattern/DailyPaperReport.md` 生成 Markdown。
>
> 文件路径：
>
> - `wiki/daily-report/Daily-Paper-Watch-YYYY-MM-DD.md`
>
> 本地日报必须包含 YAML frontmatter。候选论文不要写成不存在的内部反链。

> [!tip] Step 7 - 可选外部发布
> 如需同步到外部文档、消息、邮件或 dashboard，使用同一份正文内容。
>
> 外部发布版本要求：
>
> - 标题建议：`Daily Paper Watch - YYYY-MM-DD`
> - 不包含 YAML frontmatter
> - 章节、候选论文、排序、行动建议和 Source Notes 不得与本地版本分叉
> - 可以使用目标平台支持的样式增强展示，但不得改变正文事实内容
>
> 如果外部发布失败，不要删除本地日报；在最终回复或日志中说明失败原因，并给出本地报告路径。

## 2 写入规则

> [!warning] 默认只写 Daily Report，不写知识正文
> Daily Paper Worklist 默认只写：
>
> - `wiki/daily-report/Daily-Paper-Watch-YYYY-MM-DD.md`
> - 可选外部发布版本
>
> 这两个产物是 discover report，不等于论文入库。
>
> 只有用户明确说“写入 / 记录 / 保存 / 入库 / 下载 / 解析 / 生成 summary”某篇论文时，才进入对应 SOP。

写入本地日报后，需要更新 `wiki/log.md`。
