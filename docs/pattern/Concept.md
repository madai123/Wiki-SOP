# 1. 字段说明

- `L1`：
	- community / research ecosystem  
	- examples: research ecosystem A, interaction paradigm B, evaluation community C
- `L2`：
	- research problem / task family  
	- examples: task family A, model family B, representation learning C
- `L3`：
	- research trajectory / dominant route  
	- should be able to absorb at least 3–5 future papers  
	- avoid paper-specific methods or implementation details
- `Status`：Concept  当前状态
	  - `new`：经由你与用户讨论后，需要新增的 Concept  条目
	  - `stable`：已有且无需操作的条目
	  - `add`：已有 Concept 条目，仅需新增 paper 反链
	  - `merge`：已有 Concept  条目进行合并，一个合并到另一个
	  - `delete`：确认不再保留的 Concept 条目
- `Action_Target`：当 `Status=merge/delete` 时，说明要合并到或替换成哪个 Concept
- `Notes`：记录调整原因

# 2. Concept 正文模板
---
name: ""
level: L3/L2/L1
l1: "" / None
l2: "" / None
l3: "" / None
aliases: []
status: new / stable / add / merge / delete
Action_Target: None / xxx
Notes: ""
---

## 1 Definition

[这个 L3 Concept  在当前研究库里的定义。]


## 2 Linked Papers

- \[\[paper_xxxxxxxx\]\]
	- Evidence：[为什么这篇论文属于这个 Concept ]

## 3 Core Patterns

- 默认留空，用户讨论触发

这个 Concept 下论文反复出现的共同模式：

- [总结出的共同模式]
	- Evidence 1：[论文原文]
	- Evidence 2：[论文原文]
	- Evidence 3：[论文原文]
...

## 4 Key Differences Inside This Concept 

- 默认留空，用户讨论触发

这个 Concept  内部有哪些分支或差异：

- [内部差异]
	- Evidence 1：[论文原文]
	- Evidence 2：[论文原文]
	- Evidence 3：[论文原文]
...

## 5 Related Concept 

### \[\[another-Concept \]\]

- reason：为什么认为这两个 Concept 相关
...

## 6 Open Questions
