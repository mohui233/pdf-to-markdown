# PDF 转 Markdown Skill

## 使用说明

本技能用于将 PDF 转为可继续编辑的 Markdown。

执行时按文档类型自动分流：

- 简单文本型 PDF：优先用 `markitdown`
- 复杂版式型 PDF：优先用临时 Python 脚本
- 扫描型 PDF：先 OCR

## 目录结构

- `SKILL.md`：技能入口、触发方式、全局约束
- `rules/route-and-env.md`：分类标准、环境检查、依赖安装规则
- `commands/pdf-to-markdown.md`：完整执行流程与输入输出约定

## 使用顺序

1. 先读取 `SKILL.md`，确认触发方式与全局约束。
2. 再读取 `rules/route-and-env.md`，判断 PDF 类型并检查环境。
3. 最后执行 `commands/pdf-to-markdown.md` 中的步骤完成转换。

## 维护约定

- 入口信息只写在 `SKILL.md`
- 执行步骤只写在 `commands/`
- 判定标准与环境规则只写在 `rules/`
- 不在多个文件重复维护同一条规则
