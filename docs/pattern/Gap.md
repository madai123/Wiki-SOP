# A. Index 格式

根目录 `[当前工作目录 / INDEX-gaps.md]` 使用 Dataview 或总表维护所有 `confirmed gap / hypothesis / question`

## 字段说明

- `Gap_name`：引用到具体 gap 详情页的反链，必须使用 `[[gap_name]]` 格式
- `Name`：gap / hypothesis / question 的名称
- `Type`：条目类型，包含 `confirmed gap / hypothesis / question`
- `Status`：生命周期状态，不替代 `Type`
	  - `open`：仍在讨论或等待更多证据，默认状态
	  - `draft`：初步假设，尚未验证
	  - `testing`：正在验证
	  - `confirmed`：已经确认
	  - `rejected`：已经被证据反驳
	  - `closed`：问题已解决或不再维护
- `Related Papers`：相关库内论文，必须使用 `[[paper_id]]` 格式
- `check`：人工审核状态，包含 `checked / uncheck`
- `Notes`：一句话说明原因或当前判断

| Gap_name     | Type                                  | Status                                                 | Related Papers     | check             | Notes |
| ------------ | ------------------------------------- | ------------------------------------------------------ | ------------------ | ----------------- | ----- |
| [[gap_name]] | confirmed gap / hypothesis / question | open / draft / testing / confirmed / rejected / closed | [[paper_xxxxxxxx]] | checked / uncheck |       |


# B. Gaps 正文模板

文件路径按 `Type` 决定：

- `confirmed gap`：`wiki/gaps/confirmed/gap_name.md`
- `hypothesis`：`wiki/gaps/hypotheses/gap_name.md`
- `question`：`wiki/gaps/questions/gap_name.md`
---  
name: gap_name  
type: confirmed gap / hypothesis / question  
status: open / draft / testing / confirmed / rejected / closed  
check: uncheck / checked
related_papers:  
 - paper_id  
tags:  
 - tag1  
 - tag2  
---

# gap_name  
  
## A. 简介  
  
[用 1-3 句话说明这个 gap / hypothesis / question 是什么。]  
  
## B. 证据来源  
  
> 只引用库内已有 paper，使用 `[[paper_id]]` 反链
  
- [[paper_id]]：[简要说明这篇论文如何支持或引出该 gap]  
  
## C. 为什么重要  
  
[说明这个问题为什么值得保留，可能影响什么任务、方法或研究方向。]  
  
## D. 当前判断  
  
[说明当前状态为什么是 open / draft / testing / confirmed / rejected / closed。]  
  
## E. 下一步  
  
[可以继续读什么、验证什么、比较什么，或者下一轮要和用户讨论什么。]
