# 1 目标

从 paper summary、limitations、assumptions、future work，以及用户与模型的讨论中整理研究空白、研究假设和开放问题，并写入 `wiki/gaps/`。

Gap 不在每篇论文处理时自动生成。模型可以提出候选 Gap，但写入前必须经过用户确认。

# 2 目录约定

- 总览：`INDEX-gaps.md`
- confirmed gap：`wiki/gaps/confirmed/gap_name.md`
- hypothesis：`wiki/gaps/hypotheses/gap_name.md`
- question：`wiki/gaps/questions/gap_name.md`

不要使用 `wiki/gaps/index.md` 或 `wiki/gaps/confirmed-gaps.md`。

# 3 操作步骤

## 3.1 候选讨论

1. 读取模板：`docs/pattern/Gap.md`
2. 读取总览：`INDEX-gaps.md`
3. 根据任务范围读取相关 gap 页面，不要全量扫描 `wiki/gaps/**`
4. 根据任务范围读取相关 paper summary，不要全量扫描 `wiki/papers/*.md`
5. 从以下位置提取候选内容：
   - paper summary 的 `## 6 Gap 线索`
   - `Limitations and Assumptions`
   - Evidence 中暴露出的不足
   - 多篇论文之间的矛盾或空白
   - 用户与模型讨论中形成的问题或假设
6. 合并语义重复候选项。
7. 将候选项分为 `confirmed gap / hypothesis / question`。
8. 向用户汇报候选列表，等待确认。

## 3.2 写入

1. 如果已有相似条目，优先更新原条目，不重复创建。
2. 按 Type 写入对应子目录：
   - `confirmed gap` -> `wiki/gaps/confirmed/`
   - `hypothesis` -> `wiki/gaps/hypotheses/`
   - `question` -> `wiki/gaps/questions/`
3. 更新页面 frontmatter，保证 Dataview 可被 `INDEX-gaps.md` 收集。
4. 如需改变 Type，先迁移文件到目标子目录，再更新 frontmatter。
5. 更新完成后，在 `wiki/log.md` 记录本次调整。

# 4 分类规则

- `confirmed gap`：已有较明确证据支持的研究空白，例如多篇论文反复暴露同一 limitation，或用户确认值得沉淀。
- `hypothesis`：可测试但尚未验证的研究想法，应包含前提、claim、最小验证实验和可能反例。
- `question`：还没有形成明确假设的开放问题。

# 5 状态规则

- `open`：仍在讨论或等待更多证据，默认状态
- `draft`：初步假设，尚未验证
- `testing`：正在验证
- `confirmed`：已经确认
- `rejected`：已经被证据反驳
- `closed`：问题已解决或不再维护

`Type` 表示条目性质，`Status` 表示当前生命周期。不要用 `Status=confirmed` 替代 `Type=confirmed gap`。

# 6 质量要求

- 不要把所有 paper summary 里的 Gap 线索搬入 `gaps/`。
- 每条 gap 必须关联至少一篇已存在的 paper，使用 `[[paper_id]]`。
- 如果只是模型推测，标为 `hypothesis` 或 `question`，不要标为 `confirmed gap`。
- 不要把单篇论文的普通 limitation 直接写成 `confirmed gap`。
- 不要创建不存在的 paper 反链。
- 写入前必须经过用户确认。
