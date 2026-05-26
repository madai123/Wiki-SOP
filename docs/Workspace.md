# Workspace 文件结构说明

本 workspace 用于管理论文下载、原文解析、论文总结、概念索引、实体索引、研究空白、方法对比和领域综合理解。

# 1 总体结构

```text
claude_workspace/
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
    ├── README.md
    ├── Workspace.md
    ├── SOP-Lint-Report.md
    ├── operation/
    └── pattern/
```

# 2 根目录

## `CLAUDE.md`

全局执行规范。模型执行任务前应优先读取，用于确认任务入口、读取范围、写入确认规则和日志规则。

## `INDEX-*.md`

根目录索引文件，主要通过 Dataview 汇总 `wiki/` 下页面 frontmatter。

- `INDEX-paper.md`：论文总览
- `INDEX-concept.md`：Concept 总览
- `INDEX-entity.md`：Entity 总览
- `INDEX-gaps.md`：Gap / hypothesis / question 总览
- `INDEX-comparisons.md`：Comparison 总览
- `INDEX-synthesis.md`：Synthesis 总览

除非用户明确要求迁移结构，不要再新增 `wiki/*/index.md` 作为主索引。

# 3 输入材料

## `downloads/`

保存原始 PDF 和 metadata：

- `paper_id.pdf`
- `paper_id.json`

## `raw/`

保存 OCR / parser 输出：

- `raw/paper_id/paper_id.md`
- `raw/paper_id/paper_id.json`
- `raw/paper_id/imgs/`

# 4 Wiki 知识库

## `wiki/log.md`

操作日志。每次写入、删除、合并、索引更新或结构调整后追加记录。

## `wiki/daily-report/`

保存 Daily Paper Watch 生成的 Obsidian 版本日报。

日报是 discover report，不等于论文入库。默认文件名：

- `Daily-Paper-Watch-YYYY-MM-DD.md`

该目录下页面可以包含 YAML frontmatter，用于后续按日期、来源、候选数量和状态检索。

## `wiki/papers/`

保存单篇论文 summary，文件名使用 `paper_id.md`。

页面通常包括 metadata、一句话贡献、问题设定、方法核心、Evidence、Limitations and Assumptions、Gap 线索、Figures and Tables、Concept links、Entity links、与已有工作的关系。

## `wiki/concepts/`

保存跨论文复用的方法、机制、理论、训练目标、表示方式或研究路线。

Concept 总览来自各页面 frontmatter 和 `INDEX-concept.md`，不维护 `wiki/concepts/index.md`。

## `wiki/entities/`

保存具体对象，仅维护四类：

- `author_group`
- `dataset`
- `system`
- `benchmark`

Entity 总览来自各页面 frontmatter 和 `INDEX-entity.md`。

## `wiki/gaps/`

保存研究空白、假设和开放问题。

- `wiki/gaps/confirmed/`：confirmed gap
- `wiki/gaps/hypotheses/`：hypothesis
- `wiki/gaps/questions/`：question

Gap 总览来自各页面 frontmatter 和 `INDEX-gaps.md`。

## `wiki/comparisons/`

保存用户确认后的横向比较页面。

`wiki/comparisons/index.md` 可作为手写列表保留；`INDEX-comparisons.md` 可作为 Dataview 总览。

## `wiki/synthesis/`

保存用户确认后的综合理解页面，例如领域地图、方法谱系、共享假设和趋势判断。

Synthesis 总览来自各页面 frontmatter 和 `INDEX-synthesis.md`。

# 5 Docs 文档

## `docs/operation/`

保存流程文档，说明每类任务应该怎么做。

## `docs/pattern/`

保存页面模板，说明最终页面应该长什么样。

## `docs/SOP-Lint-Report.md`

历史 lint 报告，用来追踪曾经的混乱点，不作为当前执行规范。
