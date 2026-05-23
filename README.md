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
