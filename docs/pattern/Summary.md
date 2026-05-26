---
source_id: paper doi / arxiv id
title: paper_title
authors:
  - aaa
  - bbb
  - ...
year: 2026 / ...
status: metadata finished / summary finished / have discussed
manual_review_needed: true/false
tags:
  - aaa
  - bbb
---

## 1 一句话贡献
[ 1-2 句话说清这篇论文。 ]


## 2 问题设定

请写 2-3 段：  
  
1. 第一段：说明任务背景和该论文关注的**具体问题**
2. 第二段：说明现有方法为什么失败，必须**具体**指出 failure mode
3. 第三段：说明本文的切入点和问题重定义


## 3 方法核心  

请按机制展开，不少于 3 个小节
  
每个小节必须包含：  
  - 这个机制输入是什么  
  - 输出是什么  
  - 解决哪个 failure mode  
  - 和其他机制如何衔接  
  
如果有关键公式，必须保留并解释公式中每一项的作用


## 4 Evidence

说明论文如何证明自己的 claim，要求：

1. 使用了哪些 benchmark / datasets  
2. 和哪些 baseline 比较  
3. 主要指标是什么  
4. 关键结果是什么
5. 哪个消融证明了哪个组件有用
6. 如果论文有图表，说明图表如何支持 claim
  
禁止只写“达到 SOTA”


## 5 Limitations and Assumptions

**本节分两层写**：论文作者明确承认的限制，以及从论文设计中推断出的隐含假设

要求：  
- 不要只列关键词，每一点都要解释“为什么这是限制/假设”
- 每条都必须包含“发现 + 支撑引文 + 解释”
- 引文必须来自论文原文，尽量准确到句，不要整段复制
- 如果论文没有明确写 limitation，也要根据方法、实验设置和依赖条件进行合理分析
- 不要编造论文没有支持的结论；不确定时标注“不确定”或“需要复查”

### 5.1 Explicit Limitations

#### 输出模板

```
- **限制1**：xxx
> 支撑引文： 论文原文
> 解释：为什么这构成限制，会影响什么

- **限制2**：xxx
> 支撑引文： 论文原文
> 解释：为什么这构成限制，会影响什么

...
```

### 5.2 Implicit Assumptions

#### 输出模板
```
- **限制1**：xxx
> 支撑引文： 论文原文
> 解释：为什么这能推出该假设；如果假设不成立，方法可能在哪里失效

- **限制2**：xxx
> 支撑引文： 论文原文
> 解释：为什么这能推出该假设；如果假设不成立，方法可能在哪里失效

...

```

## 6 Gap 线索

> 关注点：具体的、可探索的科研空白

#### 输出模板

```
**Gap**：具体研究空白  
> **支撑引文**：论文原句  
> - **为什么值得做**：这个空白可能带来什么研究价值
```


## 7 Figures and Tables

记录对理解论文有帮助的图表

#### 输出模板

```
### Figure X: <name>  
![](path)  
- caption: 几句话描述关键点
- what_it_shows:  
- why_it_matters:  
- linked_section: 
```

## 8 Concept links

**要求：**
 - 默认留空， 用户主动触发

#### 输出模板

```
[[Concept_A]]
[[Concept_B]]
[[Concept_C]]
```

## 9 Entity links

**要求：**
 - 默认留空， 用户主动触发

#### 输出模板

```
[[Entity_A]]
[[Entity_B]]
[[Entity_C]]
```


## 10 与已有工作的关系

**要求：**
 - 默认留空， 用户主动触发
 - 本节只记录用户确认后的高价值关系，不记录完整 references / citations
 - 内部论文使用 `[[paper_id]]` 反链；外部论文使用标题 + DOI/arXiv 链接，不创建伪反链

**关系类型说明：**
- `type: refer`  
    表示**本文引用了对方**。通常来自本文 references、related work、method 或 experiment baseline。
- `type: cite`  
    表示**对方引用了本文**。通常来自 Semantic Scholar 的 cited-by / citationContext。

**relationship 枚举：**
- `builds_on`：本文继承了该工作的思想、任务设定、表示方式或方法框架。
- `improves`：本文改进了该工作的某个问题或缺陷。
- `contrasts_with`：本文与该工作形成路线、设定或方法对比。
- `contradicts`：本文与该工作在结论、假设或实验结果上存在冲突。
- `method_neighbor`：方法相近，属于相邻路线，但没有明确继承或改进关系

#### 输出模板

```
### work [idx]
- link: [[paper_xxxxxxxx]] 或 External: Paper Title 和 完整 DOI/arXiv: ...  
  
- type: cite / refer
- relationship: builds_on / improves / contrasts_with / contradicts / method_neighbor  
> 支撑引文: "论文原文或 S2 citationContext 中的短句"  
> - 说明: 解释这条关系为什么成立
```
