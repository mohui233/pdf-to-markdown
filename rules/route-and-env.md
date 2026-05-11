# 路由与环境规则

主流程以 `SKILL.md` 为准，本文件只保留分类判断、环境检查和安装命令。

## 分类判断

### 简单文本型 PDF

满足多数条件时归入此类：

- 单栏排版
- 正文连续
- 表格很少
- 图文混排较少
- 标题结构简单

### 复杂版式型 PDF

满足多数条件时归入此类：

- 双栏或弱双栏
- 表格较多
- 参数清单较多
- 图文混排明显
- 标题编号复杂

### 扫描型 PDF

满足任一条件时归入此类：

- 无文字层
- 文本抽取结果为空或极差
- 页面主要是图片扫描

## 环境检查硬规则

- 不要在未检查环境前直接安装依赖。
- 简单文本型 PDF 优先检查 `markitdown`，不要默认走 Python 脚本。
- 复杂版式型 PDF 优先检查 `PyMuPDF`，不要默认先装一堆无关包。
- 所有安装动作都应先说明原因，再执行。
- `PyMuPDF` 优先安装到当前目录下的 `.\_pydeps`，避免污染全局环境。

## 检查与安装命令

检查 `markitdown`：

```powershell
markitdown --version
```

安装 `markitdown`：

```powershell
python -m pip install --user markitdown
```

检查 `PyMuPDF`：

```powershell
python -c "import sys; sys.path.insert(0, r'.\_pydeps'); import fitz; print('ok')"
```

安装 `PyMuPDF`：

```powershell
python -m pip install --target ".\_pydeps" PyMuPDF
```
