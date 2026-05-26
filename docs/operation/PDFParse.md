# 1 目标

将已下载的论文 PDF 解析为可供 summary 使用的 raw markdown。

PDFParse 阶段只生成 `raw/` 材料，不生成 paper summary，不更新 Concept / Entity / Gap / Comparison / Synthesis。

# 2 输入与输出

输入：

- `downloads/paper_id.pdf`

输出：

- `raw/paper_id/paper_id.md`
- `raw/paper_id/paper_id.json`
- `raw/paper_id/imgs/`

# 3 操作步骤

1. 确认 `downloads/paper_id.pdf` 存在。
2. 确认 `raw/paper_id/` 是否已存在；如果存在且用户没有明确要求重跑，先询问是否覆盖。
3. 确认解析方式：
   - MaaS：需要 `ZHIPU_API_KEY`
   - selfhosted：需要本地 vLLM/SGLang 服务可用
4. 执行解析，例如：
   - `glmocr parse downloads/paper_id.pdf --output raw/paper_id --api-key $ZHIPU_API_KEY`
5. 确认输出文件存在。
6. 在 `wiki/log.md` 记录本次解析操作。

# 4 质量要求

- 如果 `ZHIPU_API_KEY` 未设置且未指定 selfhosted 模式，应报告错误，不继续解析。
- 不要启动或关闭无关服务。
- 不要在解析阶段改写 summary 或 wiki 知识页面。
- 如果解析结果缺页、缺图或 OCR 明显错误，应标记需要复查。
