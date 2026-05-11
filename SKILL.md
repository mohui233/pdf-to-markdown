---
name: "pdf-to-markdown"
description: "将 PDF 转为可继续编辑的 Markdown，支持简单版式直转、复杂版式脚本转换与扫描件 OCR 分流。用户需要 PDF 转 MD 时调用。"
---

# PDF 转 Markdown

用于将 PDF 转为可继续编辑的 Markdown，并按文档类型选择合适的转换路径。

## 触发方式

- **指令触发**：`/pdf-to-markdown`
- **隐式触发**：用户要求将 PDF 转成 Markdown，或要求抽取 PDF 正文并保留标题层级。

## 能力目录 (Commands)

| 指令 | 职责说明 | 对应文件 |
| :--- | :--- | :--- |
| `/pdf-to-markdown` | 执行 PDF 到 Markdown 的完整转换流程 | [commands/pdf-to-markdown.md](commands/pdf-to-markdown.md) |

## 文件结构

- `rules/route-and-env.md`：定义 PDF 分类标准、环境检查规则、依赖安装规则
- `README.md`：人工阅读说明与可复制提示词

## 全局约束

- 判定标准只从 `rules/route-and-env.md` 读取
- 执行步骤只从 `commands/pdf-to-markdown.md` 读取
- 不要在未检查环境前直接安装依赖
- 简单文本型 PDF 优先走 `markitdown`
- 复杂版式型 PDF 优先走临时 Python 脚本
- 扫描型 PDF 先提示 OCR，不要继续错误转换
- 证据不足或结果不稳时，只列出问题区域，不要强行给出完整结论
