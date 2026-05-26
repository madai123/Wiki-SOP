# 1 目标

维护 `wiki/entities/` 下的 Entity 页面，并通过根目录 `INDEX-entity.md` 的 Dataview 视图形成总览。

Entity 只维护四类：`author_group / dataset / system / benchmark`。

# 2 操作步骤

## 2.1 讨论与确认

1. 读取模板：`docs/pattern/Entity.md`
2. 读取总览：`INDEX-entity.md`
3. 根据任务范围读取相关 Entity 页面：`wiki/entities/entity_name.md`
4. 根据任务范围读取相关 paper summary：`wiki/papers/paper_id.md`
5. 从论文中提取候选 Entity，并判断类型。
6. 将候选变化分为 `new / add / merge / delete / stable`。
7. 向用户汇报需要确认的变化。
8. 用户确认前，不创建、删除、合并或修改任何 Entity 页面。

## 2.2 写入

只处理用户确认后的变化。

- `new`：创建 `wiki/entities/entity_name.md`，写入 frontmatter 和正文模板，并同步相关 paper 的 `## 9 Entity links`。
- `add`：更新已有 Entity 的 `## C. Linked Papers`、别名或说明，并同步相关 paper 的 `## 9 Entity links`。
- `merge`：确认合并方向后，将 source Entity 的有效内容迁移到 target Entity，更新相关 paper 反链，再删除 source 页面。
- `delete`：删除前先移除相关 paper 中的 Entity 反链，再删除 Entity 页面。
- `stable`：无新增信息时不强制重写页面。

写入完成后，更新 `wiki/log.md`。

# 3 类型定义

## 3.1 author_group

作者组、稳定研究团队、实验室或机构合作组。

不提取单个作者、一次性署名或没有明确研究身份的普通机构名。

## 3.2 dataset

训练、验证或评测中使用的数据集或数据资源。

不提取单个 split、统计数字、普通数据增强方法。

## 3.3 system

具体命名的方法、模型、框架、agent、pipeline 或工具链。

不提取普通 module、loss function、没有明确名称的小组件或一次性实验实现细节。

## 3.4 benchmark

用于标准化评测的任务、环境、数据集变体或 benchmark suite。

不提取单个指标、单个实验配置、单个模型结果或普通训练数据。

# 4 状态与审核

- `status`：维护动作状态，使用 `new / stable / add / merge / delete`
- `check`：人工审核状态，使用 `uncheck / checked`
- `check` 默认 `uncheck`，只有用户明确确认后才改为 `checked`

# 5 质量要求

- 不要把普通术语、指标、公式变量提取为 Entity。
- 不要创建不存在的 paper 反链。
- 新增、合并、删除 Entity 前必须经过用户确认。
- Entity 页面和相关 paper 页面的反链必须同步。
