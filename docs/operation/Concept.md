# 1 目标

维护 `wiki/concepts/` 下的 Concept 页面，并通过根目录 `INDEX-concept.md` 的 Dataview 视图形成 Concept 总览。

当前约定：不维护 `wiki/concepts/index.md`。Concept 的总览、筛选、统计和缺项检查由各 Concept 页面 frontmatter + `INDEX-concept.md` 自动生成。

# 2 操作步骤

## 2.1 讨论与确认

1. 读取模板：`docs/pattern/Concept.md`
2. 读取总览：`INDEX-concept.md`
3. 根据任务范围读取相关 Concept 页面：`wiki/concepts/concept_name.md`
4. 根据任务范围读取相关 paper summary：`wiki/papers/paper_id.md`
5. 优先匹配已有 Concept，不默认新建。
6. 将候选变化分为 `new / add / merge / delete / stable`。
7. 用户确认前，不创建、删除、合并或修改任何 Concept 页面。

## 2.2 写入

只处理用户确认后的变化。

- `new`：创建 `wiki/concepts/concept_name.md`，写入 frontmatter 和正文模板，并同步相关 paper 的 `## 8 Concept links`。
- `add`：更新已有 Concept 的 `## 2 Linked Papers` 和 frontmatter，并同步相关 paper 的 `## 8 Concept links`。
- `merge`：确认合并方向后，将 source Concept 的有效内容迁移到 target Concept，更新相关 paper 反链，再删除 source 页面。
- `delete`：删除前先移除相关 paper 中的 Concept 反链，再删除 Concept 页面。
- `stable`：无新增信息时不强制重写页面。

写入完成后，更新 `wiki/log.md`。

# 3 Frontmatter 规则

每个 Concept 页面必须维护：

```yaml
name: ""
level: L1 / L2 / L3
l1: "" / None
l2: "" / None
l3: "" / None
aliases: []
status: new / stable / add / merge / delete
Action_Target: None / xxx
created_at: YYYY-MM-DD
updated_at: YYYY-MM-DD
Notes: ""
```

字段说明：

- `level` 只允许 `L1 / L2 / L3`。
- 一个 `L3` 只能属于一个 `L2`，一个 `L2` 只能属于一个 `L1`。
- `status=merge` 时，`Action_Target` 写保留的目标 Concept；其他状态写 `None`。
- `Notes` 记录边界、合并原因或用户确认意见。

# 4 质量要求

- 每篇已完成 summary 的论文通常应至少能归入一个 `L3` Concept；无法判断时放入讨论输出的 `Unresolved Papers`。
- 不要为了填满层级而创造空泛 Concept。
- 不要把单篇论文的方法名、具体模块、dataset、benchmark、system 或 metric 默认写成 Concept。
- Concept 页面中的 paper 反链只能引用已经存在于 `wiki/papers/` 的页面。
- 新增、合并、删除 Concept 前必须经过用户确认。

# 5 用户确认前输出

输出草案，不写入文件：

1. `New Concepts`
2. `Add Papers to Existing Concepts`
3. `Merge Suggestions`
4. `Delete Suggestions`
5. `Unresolved Papers`
6. `Deferred Terms`
7. `Need User Confirmation`
