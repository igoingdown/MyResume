# 项目重构与优化计划 (Refactor Plan)

通过对当前项目的结构、代码和文档进行分析，我识别出了一些潜在的问题，并制定了以下的重构与优化计划。本计划旨在提升项目的可维护性、自动化程度以及使用体验。

## 1. 现状分析

当前项目主要包含：
- **核心内容**：基于 LaTeX (`moderncv`) 的中英文简历及模板。
- **辅助文档**：`interview_doc` 目录下的面试准备资料。
- **构建方式**：依赖用户本地安装 LaTeX 环境，通过手动执行 `xelatex` 命令编译。

### 存在的问题
1.  **缺乏自动化构建工具**：用户需要手动 cd 到各个目录并输入繁琐的编译命令。没有一键编译所有简历的机制。
2.  **构建环境不统一**：依赖用户本地环境 (MacTeX/TeX Live)，可能因版本或缺失字体/包导致编译失败。
3.  **代码复用率低**：多个 `main.tex` 文件可能存在重复的导言区（Preamble）配置（如包引用、颜色定义、页面设置），维护成本高。
4.  **临时文件污染**：编译过程中产生的 `.aux`, `.log`, `.out` 等文件未被自动清理，且缺乏 `.gitignore` 规范，导致仓库可能变得杂乱。
5.  **缺乏 CI/CD**：每次修改后需要手动编译并确认 PDF 效果，没有自动化的构建和产物归档流程。

---

## 2. 优化方案

### 阶段一：基础规范与清理 (Foundation)

- **添加 `.gitignore`**
  - 在根目录添加 `.gitignore` 文件，忽略编译产生的中间文件（`*.aux`, `*.log`, `*.out`, `*.toc`, `*.synctex.gz`, `*.fls`, `*.fdb_latexmk` 等）。
  - 确保 PDF 产物（如果有必要保留在仓库中）不被忽略，或者选择忽略 PDF 并依赖 Release 发布。

- **目录结构微调** (可选)
  - 建议将简历源文件归档到 `src/` 或更清晰的分类中，例如：
    ```text
    .
    ├── resumes/
    │   ├── zh/ (对应 zhaomingxing_resume_for_job_zh)
    │   └── en/ (对应 zhaomingxing_resume_for_job_en)
    ├── templates/ (对应 resume_template)
    ├── docs/
    │   ├── interview/ (对应 interview_doc)
    │   └── images/
    ```

### 阶段二：自动化构建 (Automation)

- **引入 `Makefile`**
  - 在根目录创建 `Makefile`，封装常用的构建命令。
  - 示例目标：
    - `make zh`: 编译中文简历。
    - `make en`: 编译英文简历.
    - `make template`: 编译模板.
    - `make all`: 编译所有.
    - `make clean`: 清理所有中间文件.
  - 建议使用 `latexmk` 替代直接调用 `xelatex`，因为 `latexmk` 能自动处理依赖和多次编译问题。

### 阶段三：代码重构 (Refactoring)

- **提取公共配置**
  - 创建 `common/preamble.sty` 或 `common/config.tex`。
  - 将 `zhaomingxing_resume_for_job_zh/main.tex` 和 `resume_template/main.tex` 中通用的 `\usepackage`, 颜色定义, 页面边距设置提取出来。
  - 在各个 `main.tex` 中通过 `\input{../common/config}` 引入，保持源文件简洁。

### 阶段四：容器化与持续集成 (DevOps)

- **Docker 化**
  - 创建 `Dockerfile`，基于轻量级 TeX 镜像（如 `texlive/texlive`），预装项目所需的 `ctex`, `moderncv` 等依赖。
  - 允许用户通过 `docker run --rm -v $(pwd):/work myresume make all` 进行编译，无需本地安装庞大的 TeX 发行版。

- **GitHub Actions**
  - 配置 `.github/workflows/build.yml`。
  - 在 push 代码时自动触发构建。
  - 自动将生成的 PDF 上传为 Artifacts，或在打 Tag 时自动发布 Release。

## 3. 执行建议

建议按阶段顺序执行。目前优先推荐实施 **阶段一** 和 **阶段二**，能立即提升日常维护效率。
