# Academic Writing Skill for Claude Code

A comprehensive skill for writing scientific manuscripts with journal-specific formatting, citation management, and format conversion.

## What This Skill Does

✅ **Journal-Specific Formatting** - Writes sections according to journal requirements  
✅ **Citation Management** - Tracks and formats references automatically  
✅ **Reference Database** - Maintains bibliography with multiple citation styles  
✅ **Format Conversion** - Reformats papers between different journal styles  
✅ **Methods Section Generation** - Creates standardized methods sections for bioinformatics papers  

## Quick Start

### 1. Clone the Repository

**macOS:**
```bash
# Clone to Claude plugins directory
cd ~/.claude/plugins/repos/
git clone https://github.com/mihinduk/academic-writing-skill.git
```

**Linux:**
```bash
# Clone to Claude plugins directory
cd ~/.claude/plugins/repos/
git clone https://github.com/mihinduk/academic-writing-skill.git
```

**Alternative location (if you prefer a different Claude skills directory):**
```bash
# Clone to a temporary location first
git clone https://github.com/mihinduk/academic-writing-skill.git

# Then copy to your Claude skills directory
# macOS:
cp -r academic-writing-skill ~/Library/Application\ Support/Claude/skills/user/

# Linux:
cp -r academic-writing-skill ~/.config/Claude/skills/user/
```

### 2. Verify Installation

Start Claude Code:
```bash
claude
```

Ask:
```
Do you have the academic-writing skill? List its capabilities.
```

### 3. Use It!

```
Using the academic-writing skill, create a methods section for my 
VICAST pipeline following BMC Bioinformatics requirements.
```

## What's Included

```
academic-writing-skill/
├── SKILL.md                              # Main skill documentation
├── SETUP_INSTRUCTIONS.md                  # Detailed setup guide
├── journal_specs/
│   └── bmc_bioinformatics.json           # BMC Bioinformatics requirements
└── templates/
    └── methods_bioinformatics.md         # Methods section template & examples
```

## Key Features

### 1. Journal-Specific Requirements
- Word limits
- Section structure
- Citation styles
- Formatting requirements
- Software citation rules

### 2. Citation Management
- Use `[REF:key]` markers in text
- Automatic numbering
- Multiple citation styles
- Formatted reference lists

### 3. Software Citation Helper
- Templates for common tools
- Version number tracking
- Parameter documentation

### 4. Format Conversion
- Convert between journal formats
- Update citation styles
- Adjust section organization
- Check word limits

## Example Usage

### For Your VICAST Paper

```bash
# Navigate to paper directory
cd "/Users/handley_lab/Handley Lab Dropbox/virome/Diamond_lab_isolate_seq/2025_07_03_Diamond_NovaSeq_N1027/paper/"

# Start Claude Code
claude
```

Then ask Claude:
```
Using the academic-writing skill:

1. Read the BMC Bioinformatics journal requirements
2. Review the methods template for bioinformatics papers
3. Clone and review https://github.com/mihinduk/VICAST
4. Create a methods section in sections/methods.md with proper citations
5. Create references.bib with all cited software
6. Use the docx skill to compile a formatted Word document

Follow BMC Bioinformatics requirements for software citations and 
parameter reporting.
```

## Adding More Journals

Copy `journal_specs/bmc_bioinformatics.json` and modify for other journals:

```bash
cd academic-writing-skill/journal_specs/
cp bmc_bioinformatics.json bioinformatics.json
# Edit bioinformatics.json with that journal's requirements
```

## Integration with docx Skill

This skill works seamlessly with Claude's built-in docx skill:
- Academic-writing skill: Handles content and citations
- docx skill: Creates formatted Word documents

## Future Extensions

You can extend this skill with Python scripts for:
- `init_paper.py` - Initialize paper directory structure
- `compile_manuscript.py` - Generate final formatted documents
- `reformat.py` - Convert between journal formats
- `citation_manager.py` - Manage bibliography

See SKILL.md for full script specifications.

## Files Description

- **SKILL.md**: Complete skill documentation with all features and usage examples
- **SETUP_INSTRUCTIONS.md**: Step-by-step installation and usage guide
- **journal_specs/bmc_bioinformatics.json**: Complete BMC Bioinformatics requirements
- **templates/methods_bioinformatics.md**: Template and examples for methods sections

## Support

For issues or questions:
1. Check SETUP_INSTRUCTIONS.md for troubleshooting
2. Review examples in templates/methods_bioinformatics.md
3. Ask Claude Code to "explain the academic-writing skill"

## Version

1.0 - Initial release with BMC Bioinformatics support

---

**Ready to write better papers faster!** 🚀
