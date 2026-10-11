# 中国研究生网络安全创新大赛作品报告模板

## 文件结构

- `main.tex`：文档类、全局格式和文件装配。
- `frontmatter/`：封面、填写说明和目录。
- `chapters/`：摘要及五章正文，每章一个文件。
- `backmatter/references.tex`：参考文献。

正文文件不能单独编译；请始终以 `main.tex` 为主文件。

正文采用标准的 `\chapter{}`、`\section{}` 和 `\subsection{}` 命令，
不需要调用额外的章节命令。

## 中文宏包

模板使用 `ctexart`。若出现 `ctexart.cls not found`，说明当前 TeX 环境缺少 CTeX 中文宏集。

原生 TeX Live 可安装：

```bash
tlmgr install ctex
```

Ubuntu 26.04 的发行版 TeX Live 可安装：

```bash
sudo apt update
sudo apt install texlive-xetex texlive-lang-chinese
```

## 编译

XeLaTeX 的输出目录参数是 `-output-directory`，不是 `-outdir`：

```bash
mkdir -p build
/usr/bin/xelatex -interaction=nonstopmode -file-line-error -output-directory=build main.tex
/usr/bin/xelatex -interaction=nonstopmode -file-line-error -output-directory=build main.tex
```

第二次编译用于更新目录和总页数。若编辑器自动加入了 `-outdir=...`，请在其 LaTeX 构建配置中改为 `-output-directory=...`。

若机器上同时安装了用户版和系统版 TeX Live，可先检查实际调用路径：

```bash
type -a xelatex
```

本机通过 `apt` 安装的完整版本位于 `/usr/bin/xelatex`。如果 `xelatex` 优先指向 `~/texlive/2026/bin/x86_64-linux/xelatex`，可暂时显式使用系统版本：

```bash
/usr/bin/xelatex -interaction=nonstopmode -file-line-error -output-directory=build main.tex
```

永久修复时，请从 `~/.bashrc` 的 `PATH` 中移除或后置不完整的 `~/texlive/2026/bin/x86_64-linux`，然后重新打开终端，或执行 `hash -r` 清除 Bash 的命令路径缓存。
