# A. Index 模板  

### 字段说明
- `Entity`：引用到具体 entity 页面，必须使用 `[[entity_name]]` 格式  
- `Type`：Entity 类型  
	- `author_group`：作者组、研究团队、实验室、机构合作组  
	- `dataset`：数据集、合成数据、训练数据资源  
	- `system`：方法系统、模型系统、框架、agent、pipeline、工具链  
	- `benchmark`：评测基准、任务集合、标准评测环境  
- `Linked Papers`：引用到具体 paper summary 的反链，必须使用 `[[paper_id]]` 格式
- `Status`：Entity 当前状态  
	- `new`：经由你与用户讨论后，需要新增的 Entity 条目  
	- `stable`：已有且无需操作的条目  
	- `add`：已有 Entity 条目，仅需新增 paper 反链、别名或说明  
	- `merge`：重复或高度重合的 Entity 条目需要合并，一个合并到另一个  
	- `delete`：确认不再保留的 Entity 条目  
- `check`：人工审核，包含 `checked / uncheck`  
- `Action_Target`：当 `Status=merge/delete` 时，说明要合并到或替换成哪个 Entity  
- `Notes`：记录调整原因  
  
| Entity              | Type                                        | Linked Papers          | Status                              | Check               | Action_Target | Notes |     |
| ------------------- | ------------------------------------------- | ---------------------- | ----------------------------------- | ------------------- | ------------- | ----- | --- |
| \[\[entity_name\]\] | author_group / dataset / system / benchmark | \[\[paper_xxxxxxxx\]\] | new / stable / add / merge / delete | uncheck / checked |               |       |     |
  


# B. Entity 正文模板
---
name: entity_full_name
type: author_group / dataset / system / benchmark
status: new / stable / add / merge / delete
check: uncheck / checked
Action_Target: None / entity_name
aliases:
  - 简称1
  - 简称2
tags:
  - aaa
  - bbb
---
# entity_name

## A. Definition

[简要描述该实体]

## B. Source

> 如果该实体来自内部论文，就使用反链，如果来源于外部论文，就给出该论文的完整 DOI 链接和论文Title

- source: [[paper_id]]  / 外部 doi 和 title
- evidence: [说明该实体在论文中如何出现，例如本文方法、baseline、benchmark、训练数据等]

## C. Linked Papers

> 这部分仅涉及库内论文，如果有论文引用了该实体，反链引用即可


写一个表格
