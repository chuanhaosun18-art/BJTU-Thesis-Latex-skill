# Master Thesis Studio (BJTU)

Claude Code Skill for writing Beijing Jiaotong University (BJTU) master's thesis.

## Overview

This skill provides an end-to-end thesis writing workflow for BJTU-style master's theses:

- **Reverse parse** an existing `.docx` draft into structured Markdown
- **Outline planning** and chapter drafting with academic conventions
- **Formula rendering** via LaTeX-to-OMML conversion (80+ symbols, `\mathcal`, `\mathbb`, `\frac`, sub/superscripts)
- **Figure/table/equation numbering** with BJTU format (`图X-Y`, `表X-Y`, `(X-Y)`)
- **Reference management** following GB/T 7714
- **Safe DOCX generation** through Flat OPC XML pipeline preserving all template styles

## BJTU Format Specifics

| Item | Format |
|------|--------|
| Chapter title | `1 绪论` (Arabic numeral, no "第X章") |
| Figure caption | `图X-Y` (compact, hyphen separator) |
| Table caption | `表X-Y` |
| Equation number | `(X-Y)` |
| Heading styles | `aff1` / `afff` / `aff9` / `affb` |
| Body style | `aff3` |
| Even page header | 北京交通大学硕士学位论文 |
| References | GB/T 7714 |

## Installation

Copy this directory to your Claude Code skills folder:

```bash
cp -r master-thesis-studio-bjtu ~/.claude/skills/master-thesis-studio
```

Or clone and symlink:

```bash
git clone <repo-url> ~/master-thesis-studio-bjtu
ln -s ~/master-thesis-studio-bjtu ~/.claude/skills/master-thesis-studio
```

## Usage

1. Place your BJTU Word template (or an existing thesis draft) as `01_template/original_template.docx` in your project directory.
2. In Claude Code, the skill activates automatically for thesis-related tasks.
3. Use natural language to:
   - Parse an existing `.docx` into Markdown chapters
   - Draft or revise chapters
   - Generate a formatted `.docx` output

## Directory Structure

```
master-thesis-studio/
├── SKILL.md                  # Skill definition and instructions
├── assets/
│   └── project_state.schema.json
├── examples/
│   └── Template.docx         # BJTU thesis template
├── references/
│   ├── placeholders.md       # Placeholder syntax reference
│   ├── reference_rules.md    # GB/T 7714 citation rules
│   ├── writing_workflow.md   # Writing workflow guide
│   └── xml_mapping_spec.md   # Word XML mapping spec
├── scripts/
│   ├── word_xml_core.py      # Core Word XML engine
│   ├── flat_opc_converter.py # Flat OPC ↔ DOCX converter
│   ├── reverse_parse_docx.py # DOCX → Markdown parser
│   ├── reference_tools.py    # Reference formatting
│   └── ...                   # Other utilities
└── templates/
    ├── project_manifest.md
    ├── thesis_master_index.md
    └── ...
```

## Requirements

- Python 3.12+
- `lxml` (XML processing)
- Claude Code CLI

## Credits

Adapted from [master-thesis-studio](https://github.com) for Beijing Jiaotong University format.

---

## 中文说明

### 简介

本项目是一个 [Claude Code](https://claude.ai/claude-code) Skill，用于辅助撰写**北京交通大学硕士学位论文**。它提供了从大纲规划、章节撰写到生成符合学校格式要求的 Word 文档的完整工作流。

### 核心功能

- **反向解析**：将已有的 `.docx` 论文草稿解析为结构化 Markdown，方便后续编辑
- **大纲规划与章节撰写**：支持用自然语言指挥 Claude 起草、修改论文各章节
- **公式渲染**：LaTeX 公式自动转换为 Word 原生 OMML 格式，支持 80+ 数学符号、`\mathcal`、`\mathbb`、`\frac`、上下标等
- **图表公式自动编号**：符合北交大格式（`图X-Y`、`表X-Y`、`(X-Y)`）
- **参考文献管理**：遵循 GB/T 7714 国标格式
- **安全生成 DOCX**：通过 Flat OPC XML 管线生成 Word 文档，完整保留模板样式

### 北交大格式规范

| 项目 | 格式 |
|------|------|
| 章标题 | `1 绪论`（阿拉伯数字，无"第X章"） |
| 图题 | `图X-Y`（紧凑格式，短横线分隔） |
| 表题 | `表X-Y` |
| 公式编号 | `(X-Y)` |
| 章标题样式 | `aff1`（论文章节标题） |
| 一级节标题 | `afff`（论文一级节标题） |
| 二级节标题 | `aff9`（论文二级节标题） |
| 正文样式 | `aff3` |
| 偶数页页眉 | 北京交通大学硕士学位论文 |
| 参考文献 | GB/T 7714 |

### 安装方法

将本仓库克隆到 Claude Code 的 skills 目录：

```bash
git clone https://github.com/chuanhaosun18-art/master-thesis-studio-bjtu.git
cp -r master-thesis-studio-bjtu ~/.claude/skills/master-thesis-studio
```

或使用符号链接：

```bash
git clone https://github.com/chuanhaosun18-art/master-thesis-studio-bjtu.git ~/master-thesis-studio-bjtu
ln -s ~/master-thesis-studio-bjtu ~/.claude/skills/master-thesis-studio
```

### 使用方法

1. 将北交大 Word 论文模板放置到项目目录的 `01_template/original_template.docx`
2. 在 Claude Code 中，该 Skill 会自动识别论文相关任务并激活
3. 用自然语言与 Claude 交互即可：
   - "帮我解析这个 Word 论文草稿"
   - "写一下第二章的理论基础"
   - "生成 Word 文档"

### 环境要求

- Python 3.12+
- `lxml`（XML 处理库）
- Claude Code CLI
