# 1 目标

在用户提出综合分析需求时，对一个研究方向、问题、方法谱系或一组论文形成综合理解，并在用户确认后写入 `wiki/synthesis/`。

Synthesis 不在每篇论文处理时自动生成，只保存用户与模型讨论后确认有价值的综合判断。

# 2 输入与索引

- 模板：`docs/pattern/Synthesis.md`
- 总览：`INDEX-synthesis.md`
- 相关索引：
  - `INDEX-paper.md`
  - `INDEX-concept.md`
  - `INDEX-entity.md`
  - `INDEX-gaps.md`
  - `INDEX-comparisons.md`

# 3 操作步骤

## 3.1 讨论

1. 明确用户提出的综合分析问题。
2. 先读相关 index，定位与问题相关的 paper / concept / entity / gap / comparison。
3. 只读取与综合问题直接相关的页面。
4. 如果 index 信息不足以判断范围，先向用户确认综合范围，不要全量读取目录。
5. 生成综合草案。
6. 向用户汇报核心结论、不确定点和建议写入方式。
7. 用户确认前，不写入文件。

## 3.2 写入

1. 根据综合主题创建或更新：`wiki/synthesis/synthesis_name.md`
2. 如果已有相似 synthesis 页面，优先更新原页面，不重复创建。
3. 页面应保留：
   - frontmatter 属性
   - 相关页面反链
   - 简短综合结论
4. 通过页面 frontmatter 支持 `INDEX-synthesis.md` 的 Dataview 汇总。
5. 如相关 paper / concept / entity / gap / comparison 页面有“相关综合”区域，可同步补充反链；没有对应区域时，不强行改模板。
6. 更新完成后，在 `wiki/log.md` 记录本次调整。

# 4 质量要求

- synthesis 必须由用户问题或明确讨论需求触发，不自动创建。
- 写入前必须经过用户确认。
- synthesis 应体现跨论文、跨概念、跨实体、跨 gap 或跨 comparison 的综合理解。
- 不要把单篇论文 summary 改写成 synthesis。
- 所有库内页面必须使用反链。
- 不要创建不存在的 paper / concept / entity / gap / comparison 反链。
- 不要默认读取 `wiki/papers/*.md`、`wiki/concepts/*.md`、`wiki/entities/*.md` 等全量目录。
- 如果综合结论需要展开成长篇分析，应拆成多个 synthesis 页面。

# 5 输出要求

讨论阶段输出：

1. 综合问题
2. 相关页面
3. 核心综合结论
4. 不确定点
5. 是否建议写入 wiki

写入阶段直接输出更新后的 Markdown 内容，不要用代码块包裹。
